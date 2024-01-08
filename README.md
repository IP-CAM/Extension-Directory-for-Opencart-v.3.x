# Extension Directory for Opencart 3
A small extension to help organize modules, themes, plugins, OCMODs of any kind separately without altering core Opencart file & folder structure, enabling a clean and modular workspace for efficient development. Works with `cp -ans`.

Explanation of used `cp` options:

`-a` or `--archive` preserves attributes, links and copies directories recursively (it's in fact alias of `-dR` `--preserve=all`)

`-n` or `--no-clobber` prevents overwriting existing files

`-s` or `--symbolic-link` makes symbolic links instead of literal copying

______________

Install either via `/system/` folder or by renaming it to install.xml, zipping to `opencart3-extension-directory.ocmod.zip` and uploading it.

Sample directory structure:

```
├── admin
├── catalog
├── extension
│   ├── extension_1.ocmod
│   │   ├── upload
│   │   └── install.xml
│   └── extension_2.ocmod
│   │   ├── upload
│   │   └── install.xml
├── image
└── system
```
### Requirements:
* Unix-like server (any variant).
* Opencart 3.x

### Usage notes:
* `extension/` directory will automatically be created on the first run if it does not exist.
* Symlinks are **regenerated** when `marketplace/modification/refresh` is called (when modifications are refreshed).
* Symlinks are **cleared** when `marketplace/modification/clear` is called (when modifications are cleared).
* When creating/deleting new `.php` files in your extension, make sure you rebuild the symlinks by refreshing modifications.
* When editing `install.xml` in your extension, make sure you refresh modifications.
* Only extension folders with names ending in `.ocmod` will be accounted for. If you want to "disable" an extension, just add an underscore or something at the end of the folder name: `.ocmod_` and refresh modifications.

### Caveats
* Due to the `-n` option (see above), it will not work if your extension attempts to override a "native" file via the `upload/*` folder (This is also default OpenCart OCMOD behaviour)
* In-production use not recommended.
