For next i2mint synch meeting:

* [ ] docker-compose problem of [kafkaposted CI](https://github.com/i2mint/kafkaposted/actions/runs/11794840638/job/32853290265#step:7:2046)
* [ ] [s3dol](https://github.com/i2mint/s3dol/actions/runs/11797788730/job/32862527293#step:7:1630) not publishing because of validation. Seems like tests depended on something that is not there anymore. See with VF what used to be the deps. 
* [ ] [making CI fail when there's an error](https://github.com/i2mint/i2mint/discussions/13#discussioncomment-10529978)
* [ ] Look into, the signature-comparison framework (see https://github.com/i2mint/i2/discussions/63 and https://github.com/i2mint/i2/discussions/76). Concrete goal: Refactor `is_call_compatible` to the framework.


## 2024-11-12

* In `epythet.published_docs`, some git tools: [check_token_scopes, ensure_branch, repo_data, commit_data, default_branch_and_commit_sha](https://github.com/i2mint/epythet/blob/cc32ebe872d0742aaf151bf8978dd5594f3ef30e/epythet/tools/published_docs.py#L245). Should really be moved to hubcap, but put as todo only.
* [s3dol](https://github.com/i2mint/s3dol/actions/runs/11797788730/job/32862527293#step:7:1630) not publishing because of validation. Seems like tests depended on something that is not there anymore. 
* Automatically created branch for all i2mint repos that are missing docs. But my [epythet.tools.published_docs:configure_github_pages](https://github.com/i2mint/epythet/blob/cc32ebe872d0742aaf151bf8978dd5594f3ef30e/epythet/tools/published_docs.py#L168) is not working. So I manually edited the pages settings to set the gh-pages as the source branch, and edited the readme to trigger CI and doc gen. The only ones left (besides `s3dol` which has CI problem) are those that don't really need docs, so I didn't process: `content, dol_cookbook, examples, i2i_scrap, py2misc, spearhead_sump`.
  * See Documentation pages section of [projects_inspection_and_ci notebook](https://github.com/i2mint/i2mint/blob/main/misc/notebooks/projects_inspection_and_ci.ipynb) for github tools for this

## 2024-11-06

* Trying to fix CI doc gen and publishing. Doing what is specified in [epythet docs](https://github.com/i2mint/epythet?tab=readme-ov-file#publishing-to-github-page-with-github-actions). Did [this](https://github.com/i2mint/isee/blob/2ff23745587fdeb694d39f0bd20e1c11f76acec1/actions/generate-documentation/action.yml), but that didn't work. Got [this CI error](https://github.com/thorwhalen/hubcap/actions/runs/11700605176/job/32584955742), so reverting to [what it was](https://github.com/i2mint/isee/blob/c76c94f4320e3e9adf59a98e8ba637370c3c3165/actions/generate-documentation/action.yml).

 
## 2024-11-05

* `dol.KeyTemplate` applications:
  * [parse_github_url](https://github.com/thorwhalen/hubcap/blob/a1d4e1be3ee9dffd09a70b6ddb47a0736c1eedc9/hubcap/util.py#L791): parse a GitHub URL and returns a dict of its components
  * [generate_github_url](https://github.com/thorwhalen/hubcap/blob/a1d4e1be3ee9dffd09a70b6ddb47a0736c1eedc9/hubcap/util.py#L836): generate a GitHub URL from the provided components dict.
  * [transform_github_url](https://github.com/thorwhalen/hubcap/blob/a1d4e1be3ee9dffd09a70b6ddb47a0736c1eedc9/hubcap/util.py#L955): transform a GitHub URL to another type, updating components as needed
* [A Pipe and operations exercise](https://github.com/i2mint/dol/discussions/44#discussioncomment-11153514)
* [partial(partial,partial): Discussion comment](https://github.com/i2mint/dol/discussions/44#discussioncomment-11153693)
* [partial(partial,partial): Medium article](https://medium.com/@thorwhalen1/partial-partial-partial-f90396901362)


## 2024-11-04

* [oplot.density_distribution](https://github.com/i2mint/oplot/blob/677868cc8bbd9cd7c01c99949f1fcc4a8b6c0980/oplot/plot_data_set.py#L53): Plots the density distribution of different data sets (arrays).
* [lkj.enable_sourcing_from_file](https://github.com/i2mint/lkj/blob/984944889e5d99f0186dda0a3e04cb95bd949e19/lkj/filesys.py#L10): Decorator for functions enables the decorated function to source from a file.
* [hubcap.replace_relative_urls](https://github.com/thorwhalen/hubcap/blob/24039e46c298b6ccf4952f083946ae6135acb734/hubcap/util.py#L91):     Replace relative URLs in a markdown string with absolute URLs based on the root_url.


## 2024-10-28

* [from.replace_image_links](https://github.com/thorwhalen/hubcap/blob/964ee189c5d5c7acaac4ea86adf9a85d81c21650/hubcap/util.py#L78): Replace relative image paths in a markdown string with absolute URLs for PyPI. --> **NOTE: Replaced by [hubcap.replace_relative_urls](https://github.com/thorwhalen/hubcap/blob/24039e46c298b6ccf4952f083946ae6135acb734/hubcap/util.py#L91)**
* [lkj recipe: Get a list of unique relative file paths](https://github.com/i2mint/lkj/discussions/2#discussioncomment-11075347)

## 2024-10-27

* [oa.prompt_json_function](https://github.com/thorwhalen/oa/blob/a9724f401eae71fc6aab7fb87cc0b64b2713804c/oa/tools.py#L444) more robust, easier to use and control.
* [sung](https://github.com/thorwhalen/sung): A start of a spotify dol
* In section "Parsing out information" of [oa - Various use cases.ipynb](https://github.com/thorwhalen/oa/blob/a76a180e6e70652cd5b52d4cda6b65fdb27b714c/misc/oa%20-%20Various%20use%20cases.ipynb), an example of how to make a parser (data extractor) with `oa.prompt_json_function`.
* [In dol, patch fix](https://github.com/i2mint/dol/blob/57b5d14ce32a7650d30cc437faedbfc6b513a326/dol/base.py#L259) when @cache_keys (possibly other store wrappers too) are applied to classes with classmethod.

## 2024-10-09

* [dol_cookbook.pipes.get_rows_iterator](https://github.com/i2mint/dol_cookbook/blob/abfa877c764dfa4664a7b2f2f81b902cbd5a2c9a/dol_cookbook/pipes.py#L13): Get an iterator over the rows of a DataFrame
* New package. `ug`, to accumulate google API tools. Namely, we have:
   * [search_maps](https://github.com/thorwhalen/ug/blob/ed433199b97339d8f1f53641ec9355814a7a138e/ug/maps.py#L93): Tool to get map search results
   * [acquire_maps_search_results_from_different_locations](https://github.com/thorwhalen/ug/blob/ed433199b97339d8f1f53641ec9355814a7a138e/ug/maps.py#L34) (to get and store multiple map search results)
* [subfolder_stores](https://github.com/i2mint/dol/blob/4b82d365f0f6b82d161178d26c651531d08c0030/dol/filesys.py#L696): Create a store of subfolders of a given folder, where the keys are the subfolder paths
  * In the process of testing `subfolder_stores`, wrote [populate_folder](https://github.com/i2mint/dol/blob/4b82d365f0f6b82d161178d26c651531d08c0030/dol/tests/test_filesys.py#L69), but should be generalized.
  
## 2024-10-08

* Extended urls that can be downloaded by [graze.util.google_drive_download_url](https://github.com/thorwhalen/graze/blob/4316e2525de3555b41d7a86a907e4123eb32ee69/graze/util.py#L317) and made ensurance of folders in paths more robust (but locally -- there is a todo to centralize, using the general [url_to_file_download](https://github.com/thorwhalen/graze/blob/4316e2525de3555b41d7a86a907e4123eb32ee69/graze/base.py#L267) function.
* Changed [isee.actions.format-source-code](https://github.com/i2mint/isee/blob/master/actions/format-source-code/action.yml) to use black instead of `axblack`. This was long due, and motivated by this error (solved the error):
  * [x] [Understanding this coe formatting CI error](https://github.com/i2mint/ju/actions/runs/11181072235/job/31084209395#step:5:93). Is it axblack, or black? See previous errors, where I couldn't install `datamodel_code_generator` just for testing. I commented out code formatting for now (todo: fix).

## 2024-09-21
* [tabled.auto_decode_bytes](https://github.com/i2mint/tabled/blob/34307900606f6cbf8aab34e93c126d084b9993c8/tabled/util.py#L192): Decode a byte sequence into a string, trying charset_normalizer gueses if fails.

## 2024-09-20

* [CascadedStores](https://github.com/i2mint/dol/blob/359cf56804e90f50297f6af7be7a463860bd7252/dol/sources.py#L445):  A MutableMapping interface to a collection of stores that will write a value in all the stores it contains, read it from the first store it finds that has it, and write it back to all the stores up to the store where it found it.

## 2024-09-19

* [lru_cache_method](https://github.com/i2mint/dol/blob/6365940b2bf28ce49b84f99b78915e2a5a2c2fae/dol/tools.py#L390): A decorator to cache the result of a method, ignoring the first argument
* [dol.cache_this(..., pre_cache)](https://github.com/i2mint/dol/blob/6ee10e80cf3672bc429eac8cc4fc76b8b7c02404/dol/tools.py#L182): pre_cache argument in cache_this

## 2024-09-18

* [aix.chat_funcs](https://github.com/thorwhalen/aix/blob/b8b58e8ddcda541d0ca493549bd0c539b2d49425/aix/gen_ai/__init__.py#L3). Facades for AI chat with various providers (handles openAI and google now). See [pypi readme](https://pypi.org/project/aix/)

## 2024-09-16

* [unique_affixes](https://github.com/i2mint/lkj/blob/892d320e21497159c7842906e064ed523506b291/lkj/strings.py#L110): Returns a list of unique prefixes (or suffixes) for the given iterable of sequences.

## 2024-09-13

* [Discussion: Renaming files to a normalized form](https://github.com/i2mint/dol/discussions/44#discussioncomment-10637725) -- using `oa` and `dol`.

## 2024-09-12

* [match_aliases](https://github.com/thorwhalen/imbed/blob/e2d0d3318fcd3f5ee19f3257f990a7450e794d16/imbed/util.py#L467): Matches the keys of aliases to the given fields, using the values of aliases as the matching logic (could be a list of possible fields, a regular expression, or a custom matching function.).

## 2024-09-10

* [ju.pydantic_util.ModelExtractor](https://github.com/i2mint/ju/blob/d7c54f9522a9a3a5f02636606e311c8b7be1fc93/ju/pydantic_util.py#L577): Extracts key paths and corresponding values from data based on matching Pydantic models.
* Uses new [dol.explicit.KeysReader](https://github.com/i2mint/dol/blob/240a6636630dc61cc18e752f8cdfdb07f1c99fb7/dol/explicit.py#L22): Mapping defined by keys with a getter function that gets values from keys.

## 2024-09-05

* [i2.itypes.ObjectClassifier](https://github.com/i2mint/i2//blob/38ccdf043d1a1aa5091a321144100aa579aa0fa1/i2/itypes.py#L314): A general-purpose classifier for objects based on a set of verifying functions.
* [oplot.heatmap_sns](https://github.com/i2mint/oplot/blob/79dcf8317420ede96b09968a8b5f197c7d2958e0/oplot/matrix.py#L275)

## 2024-09-03

* [ju.model_digraph](https://github.com/i2mint/ju/blob/8aefa5e1efd1959cd9f4a262f2f42187bc22ce3b/ju/viz.py#L9). See [Visualizing your models as a graph](https://github.com/i2mint/ju/discussions/4#discussioncomment-10530803)
* [AI Q&A: Markdown hyperlinked TOC don't work on pypi](https://github.com/thorwhalen/umpyre/discussions/61#discussioncomment-10529712)
* [field_paths_and_annotations](https://github.com/i2mint/ju/blob/1d789125b848e85f7ee959fc4746b108b93fd91e/ju/util.py#L437)
* [dol.paths.PathMappedData](https://github.com/i2mint/dol/blob/0b41260fa07bcb154217d45678ae0cfccba6c7fb/dol/paths.py#L376)

## 2024-08-29

* [json to pydantic tools](https://github.com/i2mint/ju/discussions/1#discussioncomment-10484400)
* [lkj.truncate_dict_values](https://github.com/i2mint/lkj/blob/c542856c5baa7082d354606456a9d3fb4386fc26/lkj/dicts.py#L6)
* [ju.pydantic_util.py](https://github.com/i2mint/ju/blob/62016b8394c60918d69de11620df51e5bd1b4201/ju/pydantic_util.py#L1), with functions: `is_valid_wrt_model`, `valid_models`, and `data_to_pydantic_model`, and `pydantic_model_to_code`

## 2024-08-28

* [oa Discussion: More types and models](https://github.com/thorwhalen/oa/discussions/8#discussioncomment-10476879) for openai
* [titbit.md_toc_string](https://github.com/i2mint/titbit/blob/3b00dca9b6d0d4864b17a5ff5f436ee721bc466c/titbit/strings.py#L23)

## 2024-08-27

* [See failed CI](https://github.com/thorwhalen/oa/actions/runs/10579336623/job/29311525240#step:8:219): `i2` is not installed (leading to import error), though it is (and has always been) in the `setup.cfg`.
* [i2.replace_kwargs_using](https://github.com/i2mint/i2//blob/f4e554d4f8c975ff027d986261a0e3daf8c94bac/i2/signatures.py#L4171): Decorator that replaces the variadic keyword argument of the target function using the `sig`, the signature of a source function. 

## 2024-08-23

* [Discussion: Parameter.empty behavior in function definitions
](https://github.com/i2mint/i2/discussions/77#discussioncomment-10428992)
  * Wrote a [Stackoverflow: How can I get the _true_ signature of a Python function?](https://stackoverflow.com/questions/78905311/how-can-i-get-the-true-signature-of-a-python-function).
* [Discussion: Default Source Object](https://github.com/i2mint/i2/discussions/77#discussioncomment-10429063)

## 2024-08-22

* Made [scraped](https://pypi.org/project/scraped) into a command tool and added more docs
* [Responded to a reddit post](https://www.reddit.com/r/OpenAI/comments/1cencjx/comment/ljcq38u/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button) about getting a pdf of openai API documentation: 
* [dol.store_aggregate](https://github.com/i2mint/dol/blob/3272737bfa49095e92c2e074ce8404c57279dde2/dol/tools.py#L499): Create an aggregate object of a store's content.

## 2024-08-21

* Commit: [add exception handling to dol.Pipe](https://github.com/i2mint/dol/blob/0d917936110c79806183b2246b32e0d34c8c6cd6/dol/util.py#L545)
* Commit: [add exception handling to i2.Pipe](https://github.com/i2mint/i2//blob/8c084844b44b33d26956b05c26959504b4188efa/i2/multi_object.py#L503)
* Recipe: [A path getter with Pipe](https://github.com/i2mint/dol/discussions/44#discussioncomment-10406153)

## 2024-08-20

* Repaired the tests of `is_call_compatible`. See the "Use of postprocess" section of [Notes on Aug 2024 work on signatures](https://github.com/i2mint/i2/discussions/63#discussioncomment-10394910) for a design comment. 
* Discussion comment: [Forwarding methods to extend mappings?](https://github.com/i2mint/dol/discussions/46#discussioncomment-10397874)

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

