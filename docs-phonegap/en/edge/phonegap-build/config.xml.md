# Configure Your App

  Apps built using Adobe® PhoneGap™ Build can be set up either through our web interface, or by using a `config.xml`. The `config.xml` file, as specified in the [W3C widget specification](http://www.w3.org/TR/widgets/), allows developers to easily specify metadata about their applications. You can see a sample `config.xml` with our [PhoneGap Start](https://github.com/phonegap/phonegap-start/blob/master/www/config.xml) application.

  One thing to note: please ensure that your `config.xml` file is at the top level of your application (the same level as your `index.html` file). Otherwise it will not be loaded correctly.

  We're continually adding features to cour `config.xml` support, to give PhoneGap Build developers more power to customize their apps. If there are any specific features you'd like to see support for, [please let us know](http://getsatisfaction.com/nitobi/products/nitobi_phonegap_build).

## Essential Properties

* `<widget>`: The widget element must be the root of your XML document - it lets us know that you are following the W3C specification. When using PhoneGap Build, ensure you have the following attributes set on your widget element:
  * `id`: the unique identifier for your application. To support all supported platforms, this *must* be reverse-domain name style (e.g. `com.yourcompany.yourapp`)
  * `version`: for best results, use a major/minor/patch style version, with three numbers, such as `0.0.1`
  * `versionCode`: (optional) when building for Android, you can set the versionCode by specifying it in your *config.xml*. For more information on Android's versionCode attribute, see [the Android documentation](http://developer.android.com/guide/publishing/versioning.html). 

* `<name>`: The name of the application.

* `<description>`: A description for your application. 

#### Notes:
  
  BlackBerry only supports latin characters in the `<name>` attribute.

  BlackBerry should keep the `<description>` element at a reasonable length

#### Usage:
    
    <?xml version="1.0" encoding="UTF-8" ?>
        <widget xmlns = "http://www.w3.org/ns/widgets"
            xmlns:gap = "http://phonegap.com/ns/1.0"
            id        = "com.phonegap.example"
            versionCode="10" 
            version   = "1.0.0">
        
        <!-- versionCode is optional and Android only -->

        <name>PhoneGap Example</name>

        <description>
            An example for phonegap build docs. 
        </description>

        <author href="https://build.phonegap.com" email="support@phonegap.com">
            Hardeep Shoker 
        </author>

    </widget>

<a name="platform"></a>
## Platform Build Selection

By default PhoneGap Build builds your application for every platform. If you only want to build for certain platforms you can specify these platforms with the `gap:platform` tag.  

* `<gap:platform />`:You can have zero or more of these elements present in your `config.xml`. If you specify none, all platforms will be built.

  * `name`: platform to build - one of `android, ios, winphone, blackberry, webos, symbian`

#### Usage:
    
    <gap:platform name="ios" />
    <gap:platform name="android" />
    <gap:platform name="webos" />
    <gap:platform name="symbian" />
    <gap:platform name="blackberry" />
    <gap:platform name="winphone" />

<a name="preferences"></a>
## Preferences

See the Configuration Reference section in the main PhoneGap docs for all of the preferences supported by PhoneGap (and PhoneGap Build). In addition to these, the following is a list of custom preferences supported by PhoneGap Build.

You can have zero or more `<preference>` elements in your `config.xml`. If you specify none, default properties maybe applied. Supported attributes are name` (required) and `value` (required).

The 

### Multi-Platform

<table class="table table-bordered">

  <tr>
    <td><code>phonegap-version</code></td>
    <td>  
      Currently supported versions are <b>2.5.0</b>, <b>2.7.0</b>, <b>2.9.0</b>,
      and <b>3.0.0</b> (default) -- all versions prior to 2.5.0 have been
      deprecated. If you don't specify a version in your config, it will be set
      to the current default version. Your app will not build if you specify
      an unsupported version number.
      <br/><br/>
      Example: 
      <br/>
      <code>
          &lt;preference name="phonegap-version" value="3.0.0" /&gt;
      </code>
    </td>
  </tr>

  <tr>
    <td><code>orientation</code></td>
    <td>
      Device orientation; possible values are <code>default, landscape, or
      portrait</code>. Please note that <code>default</code> means <b>both</b>
      landscape and portrait are enabled. If you want to use each platform's
      default settings (usually portrait only), remove this tag from your
      config.xml file.
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="orienation" value="landscape" /&gt;</code>
  </tr>

  <tr>
    <td><code>fullscreen</code></td>
    <td>
      Makes your app full screen, with values <code>true or false</code>. This
      hides the status bar at the top, and is false by default.
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="fullscreen" value="true" /&gt;</code>
  </tr>

</table>

### iOS Only

<table class="table table-bordered">

  <tr>
    <td><code>target-device</code><br/>(ios only)</td>
    <td>
      For targeting a specific device; possible values are <code>handset,
      tablet, or universal</code>. Note that this currently only applies to iOS
      builds; by default all builds are universal.
      <br/><br/>
      Example:
      <br/>
      <code>
          &lt;preference name="target-device" value="universal" /&gt;
      </code>
    </td>
  </tr>

  <tr>
    <td><code>prerendered-icon</code><br/>(ios only)</td>
    <td>
      This will cause iOS to not apply its gloss to the app's icon on the user's
      home screen; possible values are <code>true or false</code>, default is
      false.
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="prerendered-icon" value="true" /&gt;</code>
    </td>
  </tr>

  <tr>
    <td valign=top style="white-space:nowrap"><code>ios-statusbarstyle</code><br/>(ios only)</td>
    <td>
      Set the iOS status bar style with values <code>default, black-opaque or
      black-translucent</code>. The default is a grey status bar, black-opaque
      will appear black. Although `black-translucent` is supported, the PhoneGap
      webview does not extend beneath the status bar, so it will appear identical
      to black-opaque once your app is running.
      <br/><br/>
      Example:
      <br/>
      <code>
        &lt;preference name="ios-statusbarstyle" value="black-opaque" /&gt;
      </code>
    </td>
  </tr>

  <tr>
    <td><code>detect-data-types</code><br/>(ios only)</td>
    <td>
      Controls whether certain data types (such as phone numbers and dates) are
      automatically turned into links by the system. Defaults to "true" (as does
      the system web view). In preference to this, try using meta-tags:
      <meta name="format-detection" content="telephone=no">
      <meta name="format-detection" content="email=no">
      And use detect-data-types if meta tags don't work for you.
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="detect-data-types" value="true" /&gt;</code>
     </td>
  </tr>

  <tr>
    <td><code>exit-on-suspend</code><br/>(ios only)</td>
    <td>
      If set to true, app will terminate when suspended, for example when home
      button is pressed; default is <b>false</b>.
      <br/><br/>Example:
      <br/><code>&lt;preference name="exit-on-suspend" value="true" /&gt;</code>
    </td>
  </tr>

</table>

### Android Only

<table class="table table-bordered">

  <tr>
    <td><code>android-minSdkVersion</code><br/>(android only)</td>
    <td>
       Minimum Android SDK version. Corresponds to the `usesSdk` attributes in
       the `AndroidManifest.xml` file - more details are in
       [the Android documentation](http://developer.android.com/guide/topics/manifest/uses-sdk-element.html). Defaults to 7 (Android 2.1).
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="android-minSdkVersion" value="10" /&gt;</code>
    </td>
  </tr>

  <tr>
    <td><code>android-maxSdkVersion</code><br/>(android only)</td>
    <td>
       Maximum Android SDK version. Corresponds to the `usesSdk` attributes
       in the `AndroidManifest.xml` file - more details are in
       [the Android documentation](http://developer.android.com/guide/topics/manifest/uses-sdk-element.html). Unset by default.
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="android-maxSdkVersion" value="15" /&gt;</code>
    </td>
  </tr>

  <tr>
    <td><code>android-targetSdkVersion</code><br/>(android only)</td>
    <td>
      Corresponds to the `usesSdk` attributes in the `AndroidManifest.xml`
      file -- an integer designating the API Level that the application
      targets. If not set, the default value equals that given to
      minSdkVersion. More details are in
      [the Android documentation](http://developer.android.com/guide/topics/manifest/uses-sdk-element.html#target). Unset by default.
      <br/><br/>
      Example:
      <br/>
      <code>
        &lt;preference name="android-targetSdkVersion" value="12" /&gt;
      </code>
    </td>
  </tr>

  <tr>
    <td><code>android-installLocation</code><br/>(android only)</td>
    <td>
      Where an app can be installed - defaults to <code>internalOnly</code>
      (as the Android SDK). <code>auto</code> or <code>preferExternal</code>
      allow the app to be installed on an SD card - this can lead to unexpected
      behavior. More details available in
      [the Android documentation](http://developer.android.com/guide/appendix/install-location.html).
      <br/><br/>
      Example:
      <br/>
      <code>
        &lt;preference name="android-installLocation" value="auto" /&gt;
      </code>
    </td>
  </tr>

  <tr>
    <td><code>android-windowSoftInputMode</code><br/>(android only)</td>
    <td>
      How the main window of the activity interacts with the window containing
      the on-screen soft keyboard. More details, and possible values, available
      in [the Android documentation](http://developer.android.com/guide/topics/manifest/activity-element.html#wsoft).
      <br/><br/>
      Example:
      <br/>
      <code>
        &lt;preference name="android-windowSoftInputMode" value="stateVisible|adjustResize" /&gt;
      </code>
    </td>
  </tr>

  <tr>
    <td><code>splash-screen-duration</code><br/>(android only)</td>
    <td>
      Duration that the splash screen remains visible; defaults to 5000 (ms). For auto-hide behaviour call navigator.splashscreen.hide() in the deviceready callback.
      <br/><br/>
      Example:
      <br/>
      <code>
        &lt;preference name="splash-screen-duration" value="10000"/&gt;
      </code>
    </td>
  </tr>

</table>

### Blackberry Only

<table class="table table-bordered">
  <tr>
    <td><code>disable-cursor</code><br/>(blackberry only)</td>
    <td>
      Prevents a mouse-icon/cursor from being displayed on the app - desugars to
      <code>&lt;rim:navigation /&gt;</code>. See
      <a href="https://bdsc.webapps.blackberry.com/html5/documentation/ww_developing/rim_navigation_element_1582456_11.html">the BlackBerry documentation</a> for
      more details. Defaults to false.
      <br/><br/>
      Example:
      <br/>
      <code>&lt;preference name="disable-cursor" value="true" /&gt;</code>
    </td>
  </tr>
</table>

<a name="icons"></a>
## Icons

* `<icon>`: You can have zero or more of these elements present in your `config.xml`. If you do not specify a icon then the PhoneGap logo will be used as your application's icon. 
  * `src`: (required) specifies the location of the image file, relative to your `www` directory
  * `width`: (optional) but recommended to include, width in pixels
  * `height`: (optional) but recommended to include, height in pixels

### Usage and Additional Information:

Unless otherwise specified in a config.xml, each platform will try to use the
default `icon.png` during compilation. To define platform specific icons please
use the guide provided below.

Icon files should be the file formats specified in the examples below, other file
types are not guaranteed to work across platforms.

### Default

  The default icon must be named `icon.png` and must reside in the root of your application folder.

    <icon src="icon.png" />

### iOS

  We support classic, retina, iPad displays (and retina iPad displays in PhoneGap 2.5.0+). The following will define icons
for each specific screen type.

    <icon src="icons/ios/icon.png" gap:platform="ios" width="57" height="57" />
    <icon src="icons/ios/icon-72.png" gap:platform="ios" width="72" height="72" />
    <icon src="icons/ios/icon_at_2x.png" gap:platform="ios" width="114" height="114" />

	<!-- retina iPad support: PhoneGap 2.5.0+ only -->
	<icon src="icons/ios/icon-72_at_2x.png" gap:platform="ios" width="144" height="144" />

### Android

  We support ldpi, mdpi, hdpi, and xhdpi displays; the following will define icons for
 each specific screen type.

    <icon src="icons/android/ldpi.png" gap:platform="android" gap:density="ldpi" />
    <icon src="icons/android/mdpi.png" gap:platform="android" gap:density="mdpi" />
    <icon src="icons/android/hdpi.png" gap:platform="android" gap:density="hdpi" />
    <icon src="icons/android/xhdpi.png" gap:platform="android" gap:density="xhdpi" />

### BlackBerry

  BlackBerry icons __must be smaller__ then 16kb. BlackBerry also defines an
optional hover state; this state allows for a separate icon to be displayed
when a user uses the trackpad to roll over your icon image. By default the
non-hover icon will be used as the hover state.

    <icon src="icons/bb/icon.png" gap:platform="blackberry" />
    <icon src="icons/bb/icon_hover.png" gap:platform="blackberry" gap:state="hover"/>

### Windows Phone

  We support two icons for Windows Phone, a regular icon and a tile image.

    <icon src="icons/winphone/icon.png" gap:platform="winphone" />
    <icon src="icons/winphone/tileicon.png" gap:platform="winphone" gap:role="background" />

### WebOS 

  WebOs supports a default icon and a mini icon which can be used for notifications.

    <icon src="icons/webos/icon.png" gap:platform="webos" />
    <icon src="icons/webos/miniicon.png" gap:platform="webos" gap:role="mini" />

<a name="splashes"></a>
## Splash Screens

You can have zero or more of these elements present in your
`config.xml`. This element can have `src`, `gap:platform`, `width` and `height` attributes,
just like the `<icon>` element above. Like icon files, your splash screens
should be saved as `png` files.

	<gap:splash src="splash/ios/Default-568h@2x~iphone.png" gap:platform="ios" width="320" height="480" />


### Usage and Additional Information:

Unless otherwise specified in a config.xml, each platform will try to use the
default `splash.png` during compilation. To define platform specific splash
screens please use the guide provided below.

Splash files should be the file formats specified in the examples below. Any
other file type is not guaranteed to work across platforms.

### Warning:
If you do not supply the `gap:platform` attribute, the referenced image will be copied to ALL platforms, increasing the size of their application packages.


### Default

  The default splash must be named `splash.png` and must reside in the root of your application folder.

    <gap:splash src="splash.png" />

### iOS

  We support classic, retina, iPhone 5 and iPad displays; the following will
define splash screens for each of those. Standard iPads have two different splash
screens, portrait, landscape. Retina iPads have two additional splash screens, retina 
portrait and retina landscape (PhoneGap 2.5.0+ only).

    <gap:splash src="splash/ios/Default.png" gap:platform="ios" width="320" height="480" />
    <gap:splash src="splash/ios/Default_at_2x.png" gap:platform="ios" width="640" height="960" />
    <gap:splash src="splash/ios/Default_iphone5.png" gap:platform="ios" width="640" height="1136" />
    <gap:splash src="splash/ios/Default-Landscape.png" gap:platform="ios" width="1024" height="748" />
    <gap:splash src="splash/ios/Default-Portrait.png" gap:platform="ios" width="768" height="1004" />

	<!-- retina iPad support: PhoneGap 2.5.0+ only -->
    <gap:splash src="splash/ios/Default-Landscape_at_2x.png" gap:platform="ios" width="2048" height="1496" />
    <gap:splash src="splash/ios/Default-Portrait_at_2x.png" gap:platform="ios" width="1536" height="2008" />

### Android

  We support ldpi, mdpi, hdpi and xhdpi displays; the following will define splash
screens for each specific screen type.

    <gap:splash src="splash/android/ldpi.png" gap:platform="android" gap:density="ldpi" />
    <gap:splash src="splash/android/mdpi.png" gap:platform="android" gap:density="mdpi" />
    <gap:splash src="splash/android/hdpi.png" gap:platform="android" gap:density="hdpi" />
    <gap:splash src="splash/android/xhdpi.png" gap:platform="android" gap:density="xhdpi" />

### BlackBerry 

  BlackBerry supports a single splash image and can be defined as below.

    <gap:splash src="splash/bb/splash.png" gap:platform="blackberry" />

### Windows Phone

  Windows Phone supports a single splash image and can be defined as below.
Unlike the other supported platforms, Windows Phone splash screen should be in
`jpg` format

    <gap:splash src="splash/winphone/splash.jpg" gap:platform="winphone" />

<a name="url_schemes"></a>
## Custom URL Schemes

  iOS Only. Allows registration of [custom URL schemes](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/AdvancedAppTricks/AdvancedAppTricks.html#//apple_ref/doc/uid/TP40007072-CH7-SW50).

    <gap:url-scheme name="com.acme.myscheme" role="None">
      <scheme>pgbr</scheme>
      <scheme>pgbw</scheme>
    </gap:url-scheme>

* multiple `gap:url-scheme` elements can be present.
* `name`, optional, defaults to the application bundle id. This has to be unique. If a duplicate is found the build will fail.
* `role` must be `Editor`, `Viewer`, `Shell` or `None`, optional, defaults to `None`.
* at least one `scheme` must be present.

<a name="features"></a>
## Features 

* `<feature>`: the feature element can be used to specify which features your application is using. If you specify features of the PhoneGap API, those will be expanded to the appropriate permissions for you application. 

<a name="debug"></a>
### Custom Debug Server

The `debug-server` feature allows you to use a custom Weinre instance for your
application. By default PhoneGap Build uses `http://debug.build.phonegap.com`
however this can be changed by adding the following to your `config.xml`.

    <feature name="debug-server" required="true">
       <param name="domain" value="http://debug.custom.com"/>
       <param name="key" value="some_unique_key"/>
    </feature>

Don't forget to change the domain and key to the appropriate values.
      
### API Features

Currently supported through this interface are the following feature names:

  * `http://api.phonegap.com/1.0/battery`
    * maps to `android:BROADCAST_STICKY` permission

  * `http://api.phonegap.com/1.0/camera`
    * maps to `android:CAMERA`, `winphone:ID_CAP_ISV_CAMERA`, and `winphone:ID_HW_FRONTCAMERA` permissions

  * `http://api.phonegap.com/1.0/contacts`
    * maps to `android:READ_CONTACTS`, `android:WRITE_CONTACTS`, `android:GET_ACCOUNTS`,
      and `winphone:ID_CAP_CONTACTS` permissions

  * `http://api.phonegap.com/1.0/file`
    * maps to `WRITE_EXTERNAL_STORAGE` permission

  * `http://api.phonegap.com/1.0/geolocation`
    * maps to `android:ACCESS_COARSE_LOCATION`, `android:ACCESS_FINE_LOCATION`, 
      `android:ACCESS_LOCATION_EXTRA_COMMANDS`, and `winphone:ID_CAP_LOCATION` permissions

  * `http://api.phonegap.com/1.0/media`
    * maps to `android:RECORD_AUDIO`, `android:RECORD_VIDEO`, `android:MODIFY_AUDIO_SETTINGS`,
      and `winphone:ID_CAP_MICROPHONE` permissions

  * `http://api.phonegap.com/1.0/network`
    * maps to `android:ACCESS_NETWORK_STATE`, and `winphone:ID_CAP_NETWORKING` permissions

  * `http://api.phonegap.com/1.0/notification`
    * maps to `VIBRATE` permission

  * `http://api.phonegap.com/1.0/device`
    * maps to `winphone:ID_CAP_IDENTITY_DEVICE` permission

### Usage

    <!-- If you do not want any permissions to be added to your app, add the
        following tag to your config.xml; you will still have the INTERNET
        permission on your app, which PhoneGap requires. -->
    <preference name="permissions" value="none"/>

    <!-- to enable individual permissions use the following examples -->
    <feature name="http://api.phonegap.com/1.0/battery"/>
    <feature name="http://api.phonegap.com/1.0/camera"/>
    <feature name="http://api.phonegap.com/1.0/contacts"/>
    <feature name="http://api.phonegap.com/1.0/file"/>
    <feature name="http://api.phonegap.com/1.0/geolocation"/>
    <feature name="http://api.phonegap.com/1.0/media"/>
    <feature name="http://api.phonegap.com/1.0/network"/>
    <feature name="http://api.phonegap.com/1.0/notification"/>

<a name="plugins"></a>
## Plugins

* `<gap:plugin>`: specifies a PhoneGap plugin for PhoneGap Build to include in
your generated apps.

At present, to include a plugin, you will to ensure:

* the plugin is supported by PhoneGap Build; and
* any JavaScript script tags are present in your `index.html` file.

More details, including a list of available plugins, are in our [plugins
documentation](/docs/plugins).

<a name="access"></a>
## Access Element

* `<access>`: the access element provides your app with access to resources on other domains - in particular, it allows your app to load pages from external domains that can take over your entire webview.

A blank access tag - `<access />` - denies access to any external resources. A wildcard - `<access origin="*" />` - allows access to any external resource. Otherwise, you can specify allowed domains individually:

    <access origin="https://build.phonegap.com" />

You can also allow subdomains, using the `subdomains` attribute:

    <access origin="http://phonegap.com" subdomains="true" />

The behaviour of the access element is heavily dependent on the platform you're deploying to - we have a [blog post](/blog/access-tags) with more information. It is also likely to vary between different releases of PhoneGap - we'll work to maintain sane defaults and configurability for PhoneGap Build users.
