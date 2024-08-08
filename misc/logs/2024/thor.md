## 2024-08-08

* [lkj.log_calls](https://github.com/i2mint/lkj/blob/8eb21a04f23b3a1a79f178ddc7c4abcfc3655397/lkj/loggers.py#L123): Decorator that adds logging before and after the function's call.

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


