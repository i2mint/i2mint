
# package files

The following graph shows what modules can import others. 
These arrows are strict and show **the only** import relationships there can be.
(Only the order need to be remembered, since one module can be dependent of all the above, 
but no arrow go upward.)
More details below.

```
     ┌───────────────┐
  ┌─ │   __init__    │ ─┐
  │  └───────────────┘  │
  │    │                │
  │    │                │
  │    ▼                │
  │  ┌───────────────┐  │
  │  │     util      │ ─┼────┐
  │  └───────────────┘  │    │
  │    │                │    │
  │    │                │    │
  │    ▼                │    │
  │  ┌───────────────┐  │    │
  │  │     base      │ ◀┘    │
  │  └───────────────┘       │
  │    │                     │
  │    │                     │
  │    ▼                     │
  │  ┌───────────────┐       │
  └▶ │ other_modules │ ◀─────┘
     └───────────────┘
```

### `{pkg_name}/{pkg_name}/__init__.py`

Where we import any "interface" objects, i.e. objects we want the user to have access to directly by doing a `from pkg_name import ...`. 
To avoid circular imports, no modules of the package should access inner-package resources through this "root". 

Note: When packages are small, it's possible that `__init__.py` is the only module, in which case all other modules described below are 
unnecessary. It might be a better idea to start with expansion in mind though, to avoid refactoring and import back-compatibility issues later.

### `{pkg_name}/{pkg_name}/util.py`

Where utility objects go. Stuff that the package needs (or might need) in more than one module. 
`util.py` should only have external imports: The package depends on `util.py`, never visa versa. 

Note the singular. It's `util.py` not `utils.py`. 
This is to leave the option to create a `utils` package folder if we need to separate utilities in several modules. 

Note: There could be an argument to transition from a module to a package by replacing `util.py` by with `util/__init__.py`. 
In that case, `utils.py` could make sense.


### `{pkg_name}/{pkg_name}/base.py`

Where base functionality for the package should be put. 
`util.py` is the only inner-package module that `base.py` can depend on.


### `{pkg_name}/{pkg_name}/tests/`

Where tests go.
Folder has a `__init__.py` to make it import-accessible.



## Optionally...

### `{pkg_name}/{pkg_name}/data/`

For data that the package might require (if it requires it) -- not for test data though, 
test data should be in `{pkg_name}/{pkg_name}/tests/data`
Folder does not have an `__init__.py`
Data access objects are to be placed in `{pkg_name}/{pkg_name}/util.py`. 
These data access objects use `importlib_resources.files` (or `importlib.resources.files` for 3.9+) to reference the folder's files
(not `__name__` or other such fragile hacks):
`{pkg_name}/{pkg_name}/data`


### `{pkg_name}/{pkg_name}/tools`

`tools.py` or `tools/__init__.py`. 
For objects that are made from package objects, for various purposes. 
For example, in a package providing data-object-layering functionality (like `dol`), a `tools` module would contain 
functions to print data source (whether folder or database) statistics or visualize data structures using the package's 
functionality to access the data. 

Another related name, for more marginal applications, is `examples`.


### `{pkg_name}/{pkg_name}/examples/`

For examples of how the package can be used (need to make sure we ignore the folder, or specific modules, in CI, if these examples require dependencies we don't actually need in the package)
Folder has a `__init__.py` to make it import-accessible
No package code should import stuff from here.


### `{pkg_name}/{pkg_name}/scrap`

For work in progress or relevant code we may or may not want to integrate
Folder has a `__init__.py` to make it import-accessible
No package code should import stuff from here.

### `{pkg_name}/misc`

For miscellaneous package files, such as extra md documents, notebooks, images, etc.,  
