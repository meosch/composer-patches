# Why did we fork this repo?
The owner of the already forked repository stated that if you used it in production to fork it and use your fork.

NOTE: The syntax for this fork is different. See [this pull request](https://github.com/cweagans/composer-patches/pull/118).
Also note that the `patches-ignore` section does not work in a seperate patch file, it must be in the main composer.json.

## Instructions
Instructions on how to use the `` branch are found [here](https://github.com/acquia/blt/issues/1379#issuecomment-295868485).

> dmsmidt commented on Apr 20, 2017
> @aangelinsf, I've done what you wish to accomplish with the OpenSocial distribution.

> 1. Use the patched composer-patches version you mentioned instead of the default.
Add the following to your root composer.json's repositories section:
`{ "type" : "vcs", "url" : "https://github.com/triquanta/composer-patches" },`
Then require the patched version like this:
`"cweagans/composer-patches": "dev-fix-ignore-dependency-patches as 1.6.1",`
> 2. Ignore the patch defined in the distro in the root composer.json (note ignore setup is slightly different in the new version)
> 3. Add a different patch in the root composer.json.
It would be great if you could test cweagans/composer-patches#118.
If you want to use it in production, I would advice to get the patched version from a repo you own.

## composer.json
To the main `composer.json` I added the following to the `repositories` section:
```json
        "composer-patches-fix": {
            "type" : "vcs",
            "url" : "https://github.com/meosch/composer-patches"
        }
```
and this to the `require` section:
```json
        "cweagans/composer-patches": "dev-fix-ignore-dependency-patches as 1.6.4"
```
and this to the `extra` section:
```json
        "patches-ignore": {
            "drupal/crop": {
                "Make Crop API compatible with core Media": "https://www.drupal.org/files/issues/2918441-beta1-packaged-info-file.patch"
        }
```
