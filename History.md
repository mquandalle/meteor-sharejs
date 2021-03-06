## vNEXT

* Bump ShareJS version to 0.6.3.
* Adjust Ace config callback to run after the editor has been connected.
* Created a helper function to create a document on the server, and added a couple of tests (implicitly testing the rest of the stack.)
* Set the default value of `opsCollectionPerDoc` to `false` for the ShareJS Mongo driver. This reduces the amount of collection namespace pollution. **However, you will need to migrate your data from the previous per-document collections if you didn't use this option in an earlier version of this package.** Otherwise, your previous documents will be empty when your app loads. You can also override this behavior and use your previous schema by including the following in `Meteor.settings`:

    ```json
    {
        "sharejs": {
            "options": {
                "db": {
                    "type": "mongo",
                    "opsCollectionPerDoc": true
                }
            }
        }
    }
    ```
* Store the Meteor `userId` in the ShareJS ops collection through some egregious monkey-patching. Hopefully the modularity of ShareJS 0.7 will make this easier; to make sure this happens, you should pitch in at https://github.com/share/ShareJS/issues/286.

## v0.5.2

* Added built-in support for loading Ace editor extensions and themes.

## v0.5.1

* Fixed an issue with the Ace submodule repository path.

## v0.5.0

* Hacked up support for Meteor 0.8.0 (Blaze). Expect changes as Meteor's UI API improves.

## v0.4.0

* Preliminary support for user-accounts integration. #6
* More robust connection on both http and https services.
* Removed any references to Redis. It's much better to use Mongo with Meteor!
* Fixed a bug that prevented editing with IE.
* Moved Ace into a submodule instead of using build-fetcher - this allows themes to be more easily supported in the future.

## v0.3.2

* Download CDN files (ace) on the server, and serve as a Meteor file. #2, #3.
