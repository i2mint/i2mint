## 2024-08-21

* Commit: [add exception handling to dol.Pipe](https://github.com/i2mint/dol/blob/8cb22419cee948e72d8549b9fb211687af88f0be/dol/util.py#L545)

## 2024-08-20

* Repaired the tests of `is_call_compatible`. See the "Use of postprocess" section of [Notes on Aug 2024 work on signatures](https://github.com/i2mint/i2/discussions/63#discussioncomment-10394910) for a design comment. 
* Discussion comment: [Forwarding methods to extend mappings?](https://github.com/i2mint/dol/discussions/46#discussioncomment-10397874)
  
For next i2mint synch meeting:
* [ ] Look into why the `configure_github_pages` doesn't work on some repos (two reasons: missing branch (might be that the CI is still the old one) and 10 of them (`kafkaposted`, `redisposted`, etc.) for some other reason. See "set github settings for pages" section of my "Scrap 2024" notebook for code.
* [ ] Look into, the signature-comparison framework (see https://github.com/i2mint/i2/discussions/63 and https://github.com/i2mint/i2/discussions/76). Concrete goal: Refactor `is_call_compatible` to the framework.

## 2024-08-15

* [Sig.pair_with](https://github.com/i2mint/i2//blob/70b29fe7b8aea49726a4a4e66d3ae4413e4adead/i2/signatures.py#L1421), and changed `SigComparison` name to `SigPair` to open for other uses (like merge, etc.)
* Looked into `is_call_compatible_with` `param_comparator` default. Was None, and changed to `dflt1_is_empty_or_dflt2_is_not` if `None` in code. But I like setting the default in def directly, but when I do, some tests failed because call compatibility was also used in Sig method and `SigComparison`, with `None` default. [See commit](https://github.com/i2mint/i2//blob/22056169ad704308f189e48416e44db6a0ecc7e1/i2/signatures.py#L4983)
  * Reflection: Here's another example of a wish for signature (in this case default) injection tools. We have 3 functions, f, g, and h, where g and h use f, but in order to allow the interface of g and h to have full control over the parametrization of `f` (here, the `param_comparator` argument), the needed parameters need to be in g and h too, along with default, annotation, docs... Not only a lot of visual noise and repetition, but also violates the one source of truth (if we change the default of `param_comparator`, we need to change it in two other places. This is where the `None` trick is useful. It allows us to have one place (the body of `f`, the single source of truth) where the default is actually set. The undesirable effect there though, is that we then don't have a signature that is as informative as it could be (need to look into the code to see what the default actually is). Further, it doesn't solve the one-source-of-truth problem with annotations and docs.
  * Posted a stackoverflow to try to gather opinions: [How can I avoid interface repetition in Python function signatures and docstrings?](https://stackoverflow.com/questions/78874506/how-can-i-avoid-interface-repetition-in-python-function-signatures-and-docstring)

For new i2mint synch meeting:
* [x] Look into [this test input](https://github.com/i2mint/i2//blob/6b2cd0fc82936dc29d1653959959cde1ca1fce00/i2/tests/signatures_test.py#L708) to see if the `test_call_compatibility('(a=0, /, b=0, *, c=0)', '(a, b, c)')` should actually fail or pass. It used to pass. After a few changes in `i2.signatures` it fails. Not sure why. **Note that this problem happened before the `dflt1_is_empty_or_dflt2_is_not` change mentioned above, but after some light refactoring. 

## 2024-08-14

* [GPT for i2.signatures](https://chatgpt.com/g/g-C93Mr7Bsm-python-signatures)
* [i2.signatures.SigComparison](https://github.com/i2mint/i2//blob/e550e753d2d65c769494d61c10033b6145be631b/i2/signatures.py#L4939)

## 2024-08-13

* We discovered that the docs weren't working anymore because since Oct 2023, the docs moved to the `gh-pages` branch, and folder='/' (root) of repos,
and we hadn't updated tings he pages settings of the repos
(as, to be fair, was mentioned at the end of the new README of [epythet](https://github.com/i2mint/epythet).
Doing so manually repaired the problem.
* So now, I want to write code to change the pages settings automatically.
I added a [configure_github_pages](https://github.com/i2mint/epythet/blob/5bfecc4def08f8bb7ab4739b0619a708648d28b3/epythet/tools/published_docs.py#L125) in `epythet` to do so.
* See [chatGPT chat](https://chatgpt.com/share/b1eba162-f513-4f64-81f1-c90e72efe553) I had while developing.
  * Namely, it didn't work `i2mint/lkj`, so I tried for `thorwhalen/graze` and it worked.
  * It also works for `i2mint/posted`
    * Before that I was thinking (but it's probably **wrong**) it's an authorization error (though it doesn't say so, like it does sometimes).
    * My token seems valid (according to [token_user_info](https://github.com/i2mint/epythet/blob/5bfecc4def08f8bb7ab4739b0619a708648d28b3/epythet/tools/published_docs.py#L85)) though, and even has the required `admin:repo_hook` perm (see [tokens settings](https://github.com/settings/tokens))
     * ... Also, because the `configure_github_pages` function works for `thorwhalen/graze` and `i2mint/posted`
  * Could help: [github pages API docs](https://docs.github.com/en/rest/pages/pages?apiVersion=2022-11-28#update-information-about-a-apiname-pages-site)
* Further Questions:
  * Why do we get "This job was skipped" for Publish GitHub Pages in [oa](https://github.com/thorwhalen/oa): See [action run](https://github.com/thorwhalen/oa/actions/runs/10367803495).
  * Where's the part of CI that should populate gh-pages?
    * I ask because epythet's docs were absent, because [gh-pages was empty](https://github.com/i2mint/epythet/tree/6461d8d2ced02f3d276fe016cb524c25d4ffb889). It resolved itself automatically when I pushed to [epythet](https://github.com/i2mint/epythet/tree/gh-pages)


* [configure_github_pages_for_repo_stubs](https://github.com/i2mint/epythet/blob/ac56909a1ffe78fa7041ce01381f0cfdfcffb432/epythet/tools/published_docs.py#L176): Configure Pages for an iterable of repo stubs, or all repos in an organization.

Ran `configure_github_pages_for_repo_stubs` for all of i2mint. 
The info for the 91 unsuccessful ones was pickled and saved [here](/Users/thorwhalen/Dropbox/tmp/i2mint_docs_status.pkl). 

```
16 out of 107 repos have been successfully configured for github pages
['i2mint/audiostream2py',
 'i2mint/azuredol',
 'i2mint/config2py',
 'i2mint/dol',
 'i2mint/epythet',
 'i2mint/i2',
 'i2mint/isee',
 'i2mint/meshed',
 'i2mint/mongodol',
 'i2mint/pdfdol',
 'i2mint/posted',
 'i2mint/py2http',
 'i2mint/py2json',
 'i2mint/s3dol',
 'i2mint/tabled',
 'i2mint/wads']
```



## 2024-08-08

* [lkj.log_calls](https://github.com/i2mint/lkj/blob/60f1c4b69b2be83996b2e8758cb557c5107051e1/lkj/loggers.py#L128): Decorator that adds logging before and after the function's call.

## 2024-08-07

* [AI-enabled documentation generation ](https://github.com/i2mint/spearhead_sump/discussions/3) discussion (for Spearhead Sump project).
  * [DocStringGPT](https://chatgpt.com/g/g-pWto6xvCb-docstringgpt): Custom GPT I made to try out some AI-enabled documentation generation things. See [more info](https://github.com/i2mint/spearhead_sump/discussions/3#discussioncomment-10265194)

## 2024-07-30

* [Data acquisition stores](https://github.com/thorwhalen/graze/discussions/5#discussioncomment-10189819)
* [Clean up explicit tools](https://github.com/i2mint/dol/discussions/46#discussioncomment-10189828)
* Repaired some very annoying [config2py.config_getter](https://github.com/i2mint/config2py/issues/10#issuecomment-2258592376) issue.

## 2024-07-27

* [add typing to dol.cache_this](https://github.com/i2mint/dol/blob/b6b2b3d0c7f3a23051356d4d5bbe75790820d295/dol/tools.py#L21)
* [graze.url_to_file_download](https://github.com/thorwhalen/graze/blob/cc645112381a6932e6194170ccc32bfa2e130e26/graze/base.py#L245-L246)

## 2024-07-22

* [cache=False option in cache_this](https://github.com/i2mint/dol/blob/022d8a483c86cc0e2fb667351ad6551db9e9b56d/dol/tools.py#L286-L287)

## 2024-06-28

* Closed [More robust version handling: Take 2: Taking max version as "latest"](https://github.com/i2mint/isee/issues/29) issue.

## 2024-06-27

* Made [Make it possible to use return values in CI](https://github.com/i2mint/isee/issues/28) issue.

## 2024-06-24

* [Discussion on different implementation choices](https://github.com/i2mint/tabled/discussions/7#discussioncomment-9859012) of a `DataframeKvReader`.

## 2024-06-21

* A tool to make a text aggregate of a github repo (files, wiki, and discussions):
[repo_text_aggregate](https://github.com/thorwhalen/hubcap/blob/f78d41beb21983670d6601c8cd561f2a756772b7/hubcap/repo_slurp.py#L433) and related.
* [lkj.wrapped_print](https://github.com/i2mint/lkj/blob/f36a940ef859fbee89fd823d7f8c5997398d4b44/lkj/loggers.py#L3): Prints a list of items ensuring the total line width does not exceed `max_width`.
## 2024-06-20

The need for this popped up again: 
[Enable layered architectures to provide useful context-dependent error information](https://github.com/i2mint/i2/issues/45)

## 2024-06-19

* [github_repo_text_aggregate](https://github.com/thorwhalen/hubcap/blob/e00e56f709ee9d8a17d3fd4d4db4fc02943cddcf/hubcap/repo_slurp.py#L142)
  * uses [markdown_from_mapping](https://github.com/thorwhalen/hubcap/blob/e00e56f709ee9d8a17d3fd4d4db4fc02943cddcf/hubcap/repo_slurp.py#L91)

## 2024-06-13

* With `isee`, working on the [More robust version handling](https://github.com/i2mint/isee/issues/11) issue, which obliges us to perform [this annoying hack](https://github.com/i2mint/isee?tab=readme-ov-file#vesion-tag-misalignment).
   * doc: add module docs and commented `gen_sem`
   * refactor: separate `get_version` from gen_semver to be able to test it better:
  [see this commit](https://github.com/i2mint/isee/blob/485104d638a68029493cf1619cc1f085e37c0f43/isee/generation_utils.py#L21)

## 2024-06-06

* [cache_this](https://github.com/i2mint/dol/blob/9de66532acee982aac73181b1f1206bc3b83550b/dol/tools.py#L133): Transforms a method into a cached property with control over cache object and key.


