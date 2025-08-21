For next i2mint synch meeting:

* [ ] [S3ClientDol.__setitem__](https://github.com/i2mint/s3dol/blob/6effff79155a0d13af3aac1c751653454ea2e0cd/s3dol/base.py#L255-L256) takes Mapping values? But why? And how is it actually tested with binary [here](https://github.com/i2mint/s3dol/blob/6effff79155a0d13af3aac1c751653454ea2e0cd/s3dol/tests/test_store.py#L36)?
* [ ] s3dol tests pass on CI, but not locally: E.g.: `FAILED s3dol/tests/test_base.py::test_s3_dol_crud[localstack-localstack-http://localhost:4566] - s3dol.utility.S3DolException: Error checking bucket existence: Could not connect to the endpoint URL: "http://localhost:4566/test-bucket"`
* [ ] See [Comment on "More robust version handling: Keep versions aligned." issue](https://github.com/i2mint/isee/issues/30#issuecomment-2589617985)
* [ ] See the local (i2mint/qo) solution of some CI syntax problem [in this log entry](https://github.com/i2mint/i2mint/blob/main/misc/logs/2024/thor.md#2024-12-10). Need to find where to change this in `isee` templates.
* [ ] **master/main CI branch problem**. Have a look at how to (1) specify CI-triggering branch as a variable, (2) specify several, and (3) default to default branch. --> Check out [this solution to get default branch in CI](https://github.com/marketplace/actions/get-the-default-branch). I repaired it and did a [pull request](https://github.com/scottmmjackson/get-the-default-branch-action/pull/2). I also tested it [in isee]().
* [ ] docker-compose problem of [kafkaposted CI](https://github.com/i2mint/kafkaposted/actions/runs/11794840638/job/32853290265#step:7:2046)
* [ ] Look into, the signature-comparison framework (see https://github.com/i2mint/i2/discussions/63 and https://github.com/i2mint/i2/discussions/76). Concrete goal: Refactor `is_call_compatible` to the framework.

TODOs:
* Update all i2mint projects to include `ignore: "tests/,scrap/"` in publish block. Think of other things to update.

## 2025-08-21

* Published Podcast: [Private AI: The Future of Encrypted Machine Learning](https://open.spotify.com/episode/3Y8BpFHl9AmRnRaJrOQNAL?si=9H_P-2CxTu-TG60IhOruxA)
  * [Interactive dashboard](https://thorwhalen.com/y/2025/private_ai.html)
  * [Report](https://drive.google.com/file/d/1sipwp73O2_xXgr5juUNoYAeSdEAP-3Zb/view)

## 2025-08-20

* [sshdol tool](https://github.com/i2mint/sshdol?tab=readme-ov-file#fast-sync-to-local-folder) for **fast** local sync (copying missing files from remote to local). 
* VF pointed out ACT, a tool for local github actions. Gathered some [ACT installation info and scripts]([ACT](https://github.com/i2mint/isee/issues/15#issuecomment-3205177201)) under the (old) issue for this isee enhancement.

## 2025-08-13

### fix: `wads` gh-pages ci template

Reason was that was checking for `master` branch to do its job. Changed condition to be "if on default branch". 

That is, replaced

```
    if: "!contains(github.event.head_commit.message, '[skip ci]') && github.ref == 'refs/heads/master'"
```

with

```
    if: "!contains(github.event.head_commit.message, '[skip ci]') && github.ref == format('refs/heads/{0}', github.event.repository.default_branch)"
```

Replaced all current CIs wti this new one, and updated wads template.


## 2025-05-22

* [cw](https://github.com/i2mint/cw/): Tools for python to CLI
* [dn](https://github.com/thorwhalen/dn): Tools for parsing and generating markdown.

## 2025-05-20

* [s3dol.store:SupabaseS3BucketDol etc](https://github.com/i2mint/s3dol/blob/c7b8afe70f5432620c6eacba0ef0598d70ec1aa4/s3dol/store.py#L150). Supabase has a different API than standard AWS, so needed some adaptation.

  
## 2025-05-17

* [vd: Value Dispatch: Wire Python functions to stores for seamless input/output handling.](https://pypi.org/project/vd/)
  
## 2025-05-13

* [dol: ReprMixin](https://github.com/i2mint/dol/blob/fe070639101178de3a9a6c368c6ec8f94d452a48/dol/filesys.py#L639): To use to force a nicer repr (because trans wrappers make it hard to recover the name of the original class)
* [xdol: resolve_values_to_bytes](https://github.com/i2mint/xdol/blob/98370a76d01c5996b985abb7076409890a491e2a/xdol/x_codecs.py#L10): Value-encoding wrapper to encode to bytes.
* [dol: Use the standard lib codecs module?](https://github.com/i2mint/dol/discussions/46#discussioncomment-13131581)
* [dol: Standard lib support for postget and preset](https://github.com/i2mint/dol/discussions/46#discussioncomment-13131631)
  
## 2025-05-07

* Changed isee actions code for pytest ignore (wasn't ignoring scrap and examples in pytest, resulting in import errors (dependencies not there))
* Made [taped ci](https://github.com/i2mint/taped/blob/master/.github/workflows/ci.yml) work --> needed to add system dependencies
  
## 2025-03-18

* [tabled.duplicate_groups](https://github.com/i2mint/tabled/blob/fd5286c19756249fefdc8d41b730e13a50312ae6/tabled/util.py#L14): get the groups of duplicates in a dataframe
* [lkj.compare_field_values](https://github.com/i2mint/lkj/blob/9795e74eeb9fd44453504c5503763269fa6e8669/lkj/dicts.py#L231): Compare two dictionaries' values field by field (with functional parameters)
* [oa._resources](https://github.com/thorwhalen/oa/blob/d09fb369b581846ee72db3016e3d9fb2f5f9ddc4/oa/_resources.py): Tools for SSOT for oa, etc.
   * [oa._resources.compare_pricing_info_to_model_info](https://github.com/thorwhalen/oa/blob/d09fb369b581846ee72db3016e3d9fb2f5f9ddc4/oa/_resources.py#L49) to compare code hard coded information and documentation parsed one


## 2025-03-13

* Closed `xdol` [Issue: Flexible Mapping Update with Customizable Key Policies](https://github.com/i2mint/xdol/issues/2) with [update_with_policy](https://github.com/i2mint/xdol/blob/c0a5e8b4444e8d6b93371da0cc412b68b5b05774/xdol/updating.py#L310)
* [Discussion comment: Already existing (sorta) finer types
](https://github.com/i2mint/i2/discussions/77#discussioncomment-12485697). Finer types than the collections.abc ones

## 2025-03-11

* [Mutable Mapping Interface for Filesystems and Blob Storage - Data Type Flexibility](https://github.com/i2mint/dol/discussions/53#discussioncomment-12460364)
* Started (and later closed) work on [Design Proposal: Recursive Functionality for SshFilesReader/SshFiles](https://github.com/i2mint/sshdol/issues/1)

## 2025-03-04

* [get_markdown comment](https://github.com/thorwhalen/aix/discussions/3#discussioncomment-12387852)
  * implemented this as [aix.bytes_to_markdown](https://github.com/thorwhalen/aix/blob/f2604e0a33405cf53f944bbd9932b6684927b92d/aix/contexts.py#L245): Convert bytes of a given format to markdown text
  * implemented [aix.bytes_store_to_markdown_store](https://github.com/thorwhalen/aix/blob/f2604e0a33405cf53f944bbd9932b6684927b92d/aix/contexts.py#L327) that uses `convert_to_markdown` to convert a whole store (e.g. files of a folder) to a store with markdown versions (this store could also be a dict, which we can convert to a single aggregate file using `aix.aggregate_store`).
  * Example in [this notebook](https://github.com/thorwhalen/aix/blob/2564726676e65a316732948e145f00219aa34305/misc/aix_contexts_wip.ipynb#L1)

## 2025-02-28

* [pdfdol.get_pdf](https://github.com/i2mint/pdfdol/blob/358a575149fe9bb252b142f803a6734d373a20de/pdfdol/tools.py#L93): Convert the given source to a PDF (bytes) and process it using the specified egress.
* [Testing different AI's ability to produce SVG](https://github.com/thorwhalen/aix/discussions/7#discussioncomment-12350529)

## 2025-02-27

* [lkj.CallOnError](https://github.com/i2mint/lkj/blob/e6884485198596be33a9b2f1397d2a6a9d8ca4b6/lkj/loggers.py#L422): An extension of the suppress context manager that enables the user to issue a warning message when an import error occurs.


## 2025-02-25

* `estate`'s [remove_decorator_code and separate_decorator_code](https://github.com/thorwhalen/astate/blob/7d1670d60d4431c2d04874eb6cf68e10a8ad6ae3/extract.py#L8)
* `meshed` [expand and collapse_function_calls](https://github.com/i2mint/meshed/blob/4b7d0452768f2c79ffce013fe2dbfbee6653e58d/meshed/scrap/collapse_and_expand.py#L96): Collapse or expand function calls in a source code string.
   * See [this demo comment](https://github.com/i2mint/meshed/discussions/54#discussioncomment-12312801)


## 2025-02-24

* Overhaul of [dropboxdol](https://pypi.org/project/dropboxdol/)
  
## 2025-02-08

* [FindReplaceTool](https://github.com/i2mint/lkj/blob/c6fbe0c78871040b87ece2cbf821870d4ab18880/lkj/strings.py#L421): A general-purpose find-and-replace tool.
* Solved the `set -e` problem using `FindReplaceTool`. [See how here](https://github.com/i2mint/lkj/discussions/4#discussioncomment-12104547)
  
## 2025-02-03

* [Enhancement Comment: a KeyCodecs.mapped_keys and postelizing invertible_maps
](https://github.com/i2mint/dol/discussions/46#discussioncomment-12040329)
* Lot's more work on [msword](https://github.com/thorwhalen/msword) (dol for msword files); wrappers, readme, tests.

## 2025-01-29

* [aix.contexts.PackageCodeContexts](https://github.com/thorwhalen/aix/blob/cee22c3f8489839a8943c8dd535b6515cee1263f/aix/contexts.py#L487): Manages aggregation and saves of the code of local packages

## 2025-01-28

Discussion with VF about i2i approach. Gathered some references about what we talked about, listed below. 
See [notes on this here](https://github.com/i2mint/i2mint/discussions/13#discussioncomment-11983426).

## 2025-01-14

* [Comment on "More robust version handling: Keep versions aligned." issue](https://github.com/i2mint/isee/issues/30#issuecomment-2589617985)

## 2025-01-08

* [x] CI publishing is red, but still publishes. [Example here](https://github.com/cosmograph-org/py_cosmograph/actions/runs/12470074713/job/34804523681#step:7:207)
    * Problem was newlines in password. Added [troubleshooting mention in isee](https://github.com/i2mint/isee/blob/master/README.md#common-non-fatal-error-during-publishing).
