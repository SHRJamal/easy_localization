<p align="center"><img src="./logo/logo.svg" width="600"/></p>
<h1 align="center"> 
Easy and Fast internationalization for your Flutter Apps
</h1>

![Pub Version](https://img.shields.io/pub/v/easy_localization?style=flat-square)
![Code Climate issues](https://img.shields.io/github/issues/aissat/easy_localization?style=flat-square)
![GitHub closed issues](https://img.shields.io/github/issues-closed/aissat/easy_localization?style=flat-square)
![GitHub contributors](https://img.shields.io/github/contributors/aissat/easy_localization?style=flat-square)
![GitHub repo size](https://img.shields.io/github/repo-size/aissat/easy_localization?style=flat-square)
![GitHub forks](https://img.shields.io/github/forks/aissat/easy_localization?style=flat-square)
![GitHub stars](https://img.shields.io/github/stars/aissat/easy_localization?style=flat-square)
![Coveralls github branch](https://img.shields.io/coveralls/github/aissat/easy_localization/dev?style=flat-square)
![GitHub Workflow Status](https://img.shields.io/github/workflow/status/aissat/easy_localization/Flutter%20Tester?longCache=true&style=flat-square&logo=github)
![CodeFactor Grade](https://img.shields.io/codefactor/grade/github/aissat/easy_localization?style=flat-square)
![GitHub license](https://img.shields.io/github/license/aissat/easy_localization?style=flat-square)
![Sponsors](https://opencollective.com/flutter_easy_localization/tiers/backer/badge.svg?label=sponsors&color=brightgreen)

## Why easy_localization?

- 🚀 Easy translations for many languages
- 🔌 Load translations as JSON, CSV, Yaml, Xml using [Easy Localization Loader](https://github.com/aissat/easy_localization_loader)
- 💾 React and persist to locale changes
- ⚡ Supports plural, gender, nesting, RTL locales and more
- ⁉️ Error widget for missing translations
- ❤️ Extension methods on `Text` and `BuildContext`
- 💻 Code generation for localization files and keys.
- 👍 Uses BLoC pattern 

## Getting Started

### Configuration

Add this to your package's pubspec.yaml file:

```yaml
dependencies:
  # stable version install from https://pub.dev/packages
  easy_localization: <last_version>

  # Dev version install from git REPO
  easy_localization:
    git: https://github.com/aissat/easy_localization.git

```

#### Load translations from local assets

You must create a folder in your project's root: the `path`. Some examples:

> /assets/"langs" , "i18n", "locale" or anyname ...
>
> /resources/"langs" , "i18n", "locale" or anyname ...

Inside this folder, must put the _json_ or _csv_ files containing the translated keys:

> `path`/${languageCode}-${countryCode}.${formatFile}

[example:](https://github.com/aissat/easy_localization/tree/master/example)

- en.json or en-US.json
- ar.json or ar-DZ.json
- langs.csv

must declare the subtree in your **_pubspec.yaml_** as assets:

```yaml
flutter:
  assets:
    - {`path`/{languageCode}-{countryCode}.{formatFile}}
```

#### Note on **iOS**

For translation to work on **iOS** you need to add supported locales to 
`ios/Runner/Info.plist` as described [here](https://flutter.dev/docs/development/accessibility-and-localization/internationalization#specifying-supportedlocales).

Example:

```xml
<key>CFBundleLocalizations</key>
<array>
	<string>en</string>
	<string>nb</string>
</array>
```

#### A simple example

<details>

```dart
import 'package:flutter/material.dart';
import 'package:flutter_localizations/flutter_localizations.dart';
import 'package:easy_localization/easy_localization.dart';

void main() {
  runApp(
    EasyLocalization(
      child: MyApp(),
      supportedLocales: [Locale('en'), Locale('nb')],
      path: 'assets/translations',
      fallbackLocale: Locale('en')
    ),
  );
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      localizationsDelegates: context.localizationDelegates,
      supportedLocales: context.supportedLocales,
      locale: context.locale,
      home: Scaffold(
        body: Center(
          child: Text('hi').tr(),
        ),
      ),
    );
  }
}
```
</details>

#### Change Locale:

```dart
context.locale = locale;
```

#### Loading translations from other resources

You can use JSON,CSV,HTTP,XML,Yaml files, etc.

See [Easy Localization Loader](https://github.com/aissat/easy_localization_loader) for more info.

#### Code generation of localization files

Code generation supports json files, for more information run in terminal `flutter pub run easy_localization:generate -h`

Steps:
1. Open your terminal in the folder's path containing your project 
2. Run in terminal `flutter pub run easy_localization:generate`
3. Change asset loader and past import.

```dart
import 'generated/codegen_loader.g.dart';
...
void main(){
  runApp(EasyLocalization(
    child: MyApp(),
    supportedLocales: [Locale('en', 'US'), Locale('ar', 'DZ')],
    path: 'resources/langs',
    assetLoader: assetLoader: CodegenLoader()
  ));
}
...
```
4. All done!

#### Code generation of keys

If you have many localization keys and are confused, key generation will help you. The code editor will automatically prompt keys

Code generation keys supports json files, for more information run in terminal `flutter pub run easy_localization:generate -h`

Steps:
1. Open your terminal in the folder's path containing your project 
2. Run in terminal `flutter pub run easy_localization:generate -f keys -o locale_keys.g.dart`
3. Past import.

```dart
import 'generated/locale_keys.g.dart';
```
4. All done!

How to usage generated keys:

```dart
print(LocaleKeys.title.tr()); //String
//or
Text(LocaleKeys.title).tr(); //Widget
```

## Screenshots

 Arabic RTL | English LTR | Error widget
--- | --- | ---
![Arabic RTL](https://raw.githubusercontent.com/aissat/easy_localization/master/screenshots/Screenshot_ar.png "Arabic RTL")|![English LTR](https://raw.githubusercontent.com/aissat/easy_localization/master/screenshots/Screenshot_en.png "English LTR")|![Error widget](https://raw.githubusercontent.com/aissat/easy_localization/master/screenshots/Screenshot_err.png "Error widget")

## Donations

We need your support. Projects like this can not be successful without support from the community. If you find this project useful, and would like to support further development and ongoing maintenance, please consider donating.

<p align="center">
  <a href="https://opencollective.com/flutter_easy_localization/donate" target="_blank">
    <img src="https://opencollective.com/flutter_easy_localization/donate/button@2x.png?color=blue" width=300 />
  </a>
</p>

### Sponsors

<img src="https://opencollective.com/flutter_easy_localization/tiers/backer.svg?avatarHeight=48"/>


### Contributors thanks

![contributors](https://contributors-img.firebaseapp.com/image?repo=aissat/easy_localization)
<a href="https://github.com/aissat/easy_localization/graphs/contributors"></a>
