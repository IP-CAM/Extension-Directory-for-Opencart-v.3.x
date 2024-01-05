# Extension Directory for Opencart 3
A small extension to help organize extensions separately without altering core Opencart file & folder structure, enabling a clean and modular workspace for efficient development. Works by creating the least amount possible of symbolic links between the two directories.

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
Notes:
* `extension` directory will automatically be created on the first run if it does not exist.
* Symlinks are regenerated when `marketplace/modification/refresh` is called (when modifications are refreshed).
* Only extension folders with names ending in `.ocmod` will be accounted for. If you want to "disable" and extension, just add an underscore or something at the end of the folder name: `.ocmod_` and refresh modifications.
* Not guaranteed to work for all plugins.
* In-production use not recommended.
