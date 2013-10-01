# Using Plugins

Adobe® PhoneGap™ Build supports a whitelisted selection of PhoneGap Plugins, to extend the native functionality exposed by the PhoneGap native-app container.

The list of all supported plugins is located [here](https://build.phonegap.com/plugins).

Plugins need to implemented differently for each platform, and may not be supported across all PhoneGap platforms. If you're deploying across multiple platforms, be sure that the experience degrades gracefully for users who do not have the plugin available.

If you would like to contribute a plugin to PhoneGap Build, please see [the
relevant documentation](contributing-plugins).

## Including a plugin in your project

There are two steps to including a plugin in your project: referencing the JavaScript code for the plugin, and importing the native code.

<a name="javascripts"></a>
### Referencing the JavaScript code

As with `phonegap.js`, the JavaScript code for a plugin is inserted into your project by PhoneGap Build at build time. Plugins will usually depend on PhoneGap being loaded already, so insert a script tag after the `phonegap.js` tag, like so:

    <script src="phonegap.js"></script>
    <script src="barcodescanner.js"></script>

**Do not** include the plugin javascript files or other plugin files in your app. These will be injected by PhoneGap Build, and including them may cause problems.

### Importing the native code

To import the native code into your PhoneGap Build project, you will need to
add the correct `<gap:plugin>` tag to your config.xml file. Here
is the tag for an Example plugin:

    <gap:plugin name="com.phonegap.plugins.example" />

Plugins should be referenced by the plugin ID which is normally in a reverse domain format.

You can specify an optional version of a plugin to run with the `version` attribute.  If no version is
specified then the latest available version of the plugin is used.

    <gap:plugin name="com.phonegap.plugins.example" version="2.2.1" />

The plugin version can also specify a minimum or maximum required version.

    <gap:plugin name="com.phonegap.plugins.example" version=">=2.2.1" />
    <gap:plugin name="com.phonegap.plugins.example" version="<=2.2.1" />
    <gap:plugin name="com.phonegap.plugins.example" version=">2.2.1" />
    <gap:plugin name="com.phonegap.plugins.example" version="<2.2.1" />

You can also use the tilde (~) operator to specify _fuzzy_ versions - this will
ensure that you have the latest version of a plugin with the same major version.
For example, you could replace the tag above with:

    <gap:plugin name="com.phonegap.plugins.example" version="~2" />

which would load the latest 2.x version, but not anything with a different
major/initial version number. This version tag:

    <gap:plugin name="com.phonegap.plugins.example" version="~2.2" />

would load the latest 2.x version so long as x is greater or equal to 2. This
version tag:

    <gap:plugin name="com.phonegap.plugins.example" version="~2.2.3" />

would load the latest 2.2.x version so long as x is greater or equal to 3.

Plugins may require configuration information to be present; this can be done
with adding `<param>` children to the `<gap:plugin>` tag:

    <gap:plugin name="com.phonegap.plugins.example">
        <param name="APIKey" value="12345678" />
        <param name="APISecret" value="12345678" />
    </gap:plugin>

Read the documentation of the plugin to check whether parameters are necessary.
