# App Center `fastlane` plugin

[![fastlane Plugin Badge](https://rawcdn.githack.com/fastlane/fastlane/master/fastlane/assets/plugin-badge.svg)](https://rubygems.org/gems/fastlane-plugin-appcenter)
[![Gem Version](https://badge.fury.io/rb/fastlane-plugin-appcenter.svg)](https://badge.fury.io/rb/fastlane-plugin-appcenter)
[![Build Status](https://travis-ci.org/microsoft/fastlane-plugin-appcenter.svg?branch=master)](https://travis-ci.org/microsoft/fastlane-plugin-appcenter)

## Getting Started

This project is a [_fastlane_](https://github.com/fastlane/fastlane) plugin. To get started with `fastlane-plugin-appcenter`, add it to your project by running:

```bash
fastlane add_plugin appcenter
```

## About App Center
With [App Center](https://appcenter.ms) you can continuously build, test, release, and monitor your apps. This plugin provides an `appcenter_upload` action which allows you to upload and [release distribute](https://docs.microsoft.com/en-us/appcenter/distribution/uploading) apps to your testers on App Center as well as to upload .dSYM files to [collect detailed crash reports](https://docs.microsoft.com/en-us/appcenter/crashes/ios) in App Center.

## Usage

To get started, first, [obtain an API token](https://appcenter.ms/settings/apitokens) in App Center. The API Token is used to authenticate with the App Center API in each call.

```ruby
appcenter_upload(
  api_token: "<appcenter token>",
  owner_name: "<appcenter account name of the owner of the app (username or organization URL name)>",
  app_name: "<appcenter app name>",
  apk: "<path to android build binary>",
  notify_testers: true # Set to false if you don't want to notify testers of your new release (default: `false`)
)
```

The action parameters `api_token` and `owner_name` can also be omitted when their values are [set as environment variables](https://docs.fastlane.tools/advanced/#environment-variables). Below a list of all available environment variables:

- `APPCENTER_API_TOKEN` - API Token for App Center
- `APPCENTER_OWNER_TYPE` - Owner type - `user` or `organization` (default value is `user`)
- `APPCENTER_OWNER_NAME` - Owner name
- `APPCENTER_APP_NAME` - App name. If there is no app with such name, you will be prompted to create one
- `APPCENTER_DISTRIBUTE_APK` - Build release path for android build
- `APPCENTER_DISTRIBUTE_AAB` - Build release path for android app bundle build
- `APPCENTER_DISTRIBUTE_IPA` - Build release path for ios build
- `APPCENTER_DISTRIBUTE_DSYM` - Path to your symbols (app.dSYM.zip) file
- `APPCENTER_DISTRIBUTE_UPLOAD_DSYM_ONLY` - Flag to upload only the dSYM file to App Center
- `APPCENTER_DISTRIBUTE_ANDROID_MAPPING` - Path to your Android mapping.txt file
- `APPCENTER_DISTRIBUTE_UPLOAD_ANDROID_MAPPING_ONLY` - Flag to upload only the mapping file to App Center
- `APPCENTER_DISTRIBUTE_DESTINATIONS` - Comma separated list of destination names. Both distribution groups and stores are supported. All names are required to be of the same destination type. Default is `Collaborators`.
- `APPCENTER_DISTRIBUTE_DESTINATION_TYPE` - Destination type of distribution destination. `group` and `store` are supported. Default is `group`
- `APPCENTER_DISTRIBUTE_MANDATORY_UPDATE` - Require users to update to this release
- `APPCENTER_DISTRIBUTE_NOTIFY_TESTERS` - Send email notification about release (default: `false`)
- `APPCENTER_DISTRIBUTE_RELEASE_NOTES` - Release notes
- `APPCENTER_DISTRIBUTE_RELEASE_NOTES_CLIPPING` - Clip release notes if its length is more then 5000, `true` by default
- `APPCENTER_DISTRIBUTE_RELEASE_NOTES_LINK` - Additional release notes link
- `APPCENTER_DISTRIBUTE_TIMEOUT` - Sets the request timeout in seconds. Used when uploading builds to App Center.

## Example

Check out the [example `Fastfile`](fastlane/Fastfile) to see how to use this plugin. Try it by cloning the repo, running `fastlane install_plugins` and `bundle exec fastlane test`.

Sample uses `.env` for setting private variables like API token, owner name, .etc. You need to replace it in `Fastfile` by your own values.

There are three examples in `test` lane:
- upload release for android with minimum required parameters
- upload release for ios with all set parameters
- upload only dSYM file for ios

## Run tests for this plugin

To run both the tests, and code style validation, run

```
rake
```

To automatically fix many of the styling issues, use
```
rubocop -a
```

## Issues and Feedback

For any other issues and feedback about this plugin, please open a [GitHub issue](https://github.com/microsoft/fastlane-plugin-appcenter/issues).

## Troubleshooting

If you have trouble using plugins, check out the [Plugins Troubleshooting](https://docs.fastlane.tools/plugins/plugins-troubleshooting/) guide.

## Using _fastlane_ Plugins

For more information about how the `fastlane` plugin system works, check out the [Plugins documentation](https://docs.fastlane.tools/plugins/create-plugin/).

## About _fastlane_

_fastlane_ is the easiest way to automate beta deployments and releases for your iOS and Android apps. To learn more, check out [fastlane.tools](https://fastlane.tools).

## Contributing

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Contact

We're on Twitter as [@vsappcenter](https://www.twitter.com/vsappcenter). Additionally you can reach out to us on the [App Center](https://appcenter.ms/apps) portal by using the blue Intercom button on the bottom right to start a conversation.
