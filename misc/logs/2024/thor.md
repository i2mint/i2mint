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


