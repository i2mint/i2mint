
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
