Android Coding Best Practices
=============================

This is a set of 'nice to follow' guidelines useful when working in larger teams. Helps to keep the code nice, clean and uniform. It also gives new people joining the project a flat learning curve; once they're familiar with the principles, it's much easier to get acquainted with the codebase.

Strive to follow these rules when working on STRV projects. Each rule has a special # 6-chars identifier, allowing us to easily refer to it.

Code
----

- <a name="PRNCPL"></a>Follow OOP principles, SOLID principles, DRY and KISS. [#PRNCPL](#PRNCPL)
- <a name="GODCLS"></a>Avoid God classes. A class with hundreds of lines is probably doing too much. Each class should have only one responsibility. [#GODCLS](#GODCLS)
- <a name="GODFUN"></a>Avoid complicated functions. Every function should be doing only one thing. If possible, don't mix side effects with computation logic inside one function. [#GODFUN](#GODFUN)
- <a name="CONSIS"></a>Be consistent in naming classes, methods, properties, resources, etc. [#CONSIS](#CONSIS)
- <a name="MNGFUL"></a>Use meaningful names for variables. For example, "e" is a bad name. [#MNGFUL](#MNGFUL)
- <a name="POSITN"></a>Don't add new classes, methods, properties, resources, etc. automatically at the end of a file. Consider the proper position in the file where the element should be added. Order lifecycle methods chronologically. [#POSITN](#POSITN)
- <a name="UNUSED"></a>Don't comment out unused code, just delete it. [#UNUSED](#UNUSED)
- <a name="LIBINI"></a>Be careful with initializing multiple libraries in `Application.onCreate()`. Do this stuff off the main thread whenever possible to speed up the start of the app. [#LIBINI](#LIBINI)
- <a name="LOGPRD"></a>Don't show any logs in production build. [#LOGPRD](#LOGPRD)
- <a name="LOGCRA"></a>Enhance crash reporting with custom logs from your app. Make sure to filter out any sensitive data. [#LOGCRA](#LOGCRA)
- <a name="FACTRY"></a>Use factory pattern for creating a new Intent or for creating a new instance of a Fragment. [#FACTRY](#FACTRY)
- <a name="PARCEL"></a>Use Parcelable rather than Serializable. [#PARCEL](#PARCEL)
- <a name="RECYCL"></a>Use RecyclerView rather than ListView. [#RECYCL](#RECYCL)
- <a name="STABID"></a>Use stable ids in RecyclerView adapter whenever possible. You will achieve better performance because ViewHolders can be reused after `notifyDataSetChanged()` and you will get animations. [#STABID](#STABID)
- <a name="DIFFUT"></a>Don't call `notifyDatasetChanged()` on adapters directly. Use DiffUtil for optimized calculations of adapter data. [#DIFFUT](#DIFFUT)
- <a name="ARRMAP"></a>Consider using ArrayMap/ArraySet instead of HashMap/HashSet. It's designed to be more memory efficient. [#ARRMAP](#ARRMAP)
- <a name="DATBND"></a>Consider using the Data Binding library from Android Jetpack. [#DATBND](#DATBND)
- <a name="BNDFND"></a>Don't use `findViewById()` whenever possible. Use the Data Binding library, Kotlin Android Extensions or auto generated View Binding. [#BNDFND](#BNDFND)
- <a name="BNDEXP"></a>Don't use complicated expressions in data binding. Views should be as dumb as possible. ViewModel is responsible for display logic. [#BNDEXP](#BNDEXP)
- <a name="BNDADP"></a>Leverage the power of custom BindingAdapters. [#BNDADP](#BNDADP)
- <a name="BNDSTR"></a>Don't use `String.format()` in data binding. Use `@string/example_text(data.foo, data.bar)` instead. [#BNDSTR](#BNDSTR)

Architecture
------------

- <a name="DEPINJ"></a>Use a dependency injection framework to make code reusable, easily maintainable and testable. [#DEPINJ](#DEPINJ)
- <a name="MVVMAR"></a>Use MVVM or MVI architecture. UI logic should be implemented in ViewModel. Activity/Fragment serves as a View. [#MVVMAR](#MVVMAR)
- <a name="VIEWDT"></a>The View layer should keep neither data nor state. These should be stored in some persistent object, such as ViewModel or Redux Store. [#VIEWDT](#VIEWDT)
- <a name="VMLOGI"></a>ViewModel should contain only presentation logic. Business logic should be implemented in other classes (e.g. repository pattern). [#VMLOGI](#VMLOGI)
- <a name="VMCNTX"></a>ViewModel must not access Activity Context. [#VMCNTX](#VMCNTX)
- <a name="VMWIDG"></a>ViewModel must not access `android.view` nor `android.widget` classes. That is View's responsibility. [#VMWIDG](#VMWIDG)
- <a name="SAVSTA"></a>Always check whether the app handles saving the persistent state. When the system kills the app, ViewModel doesn't save the state. Use plain `onSaveInstanceState()` or Saved State module for ViewModel. [#SAVSTA](#SAVSTA)
- <a name="LIVDAT"></a>Consider using LiveData for holding the current state of a screen. [#LIVDAT](#LIVDAT)
- <a name="UNIDIR"></a>Strive to have a unidirectional flow of data with observer patterns. Don't imperatively set stuff if observing is possible. Leverage MediatorLiveData or similar transformations. [#UNIDIR](#UNIDIR)
- <a name="RETFRG"></a>Don't use retained Fragments. [#RETFRG](#RETFRG)
- <a name="LOADER"></a>Don't use Loaders. [#LOADER](#LOADER)
- <a name="SERVIC"></a>Don't use long-standing Service if it is not absolutely necessary. Better to use JobScheduler or WorkManager. [#SERVIC](#SERVIC)
- <a name="NAVIGA"></a>Consider using Android Navigation Component. [#NAVIGA](#NAVIGA)

Kotlin
------

- <a name="KTSTYL"></a>Follow [Android Kotlin Style Guide](https://developer.android.com/kotlin/style-guide). [#KTSTYL](#KTSTYL)
- <a name="KTXAND"></a>Use Android KTX extensions. [#KTXAND](#KTXAND)
- <a name="KTCORO"></a>Consider using Kotlin Coroutines. [#KTCORO](#KTCORO)
- <a name="KTEXPR"></a>Don't write unreadable monster expressions. Obsessing over getting by with a single expression and over utilizing smart casts can lead to pretty unreadable code. [#KTEXPR](#KTEXPR)
- <a name="KTNULL"></a>Don't use non-null assertion `!!` if it's not absolutely necessary. [#KTNULL](#KTNULL)
- <a name="KTLATE"></a>Don't use nullable types for non-null variables with delayed initialization. Use `lateinit` for this. [#KTLATE](#KTLATE)
- <a name="KTWHEN"></a>Use `when` expression instead of long `if-else-if` chain. [#KTWHEN](#KTWHEN)
- <a name="KTDATA"></a>Use data classes for entity objects. [#KTDATA](#KTDATA)
- <a name="KTSCOP"></a>Use Kotlin scope functions from the standard library (`let`, `run`, `also`, `apply`, `with`) to structure the code in a more idiomatic way. [#KTSCOP](#KTSCOP)
- <a name="KTEXTF"></a>Extension functions are not a replacement for all utility functions. Extension functions are good for extending existing abstractions. Don't abuse them if an extension semantically doesn't make sense. For example, `Int.px()` is a semantically wrong extension. [#KTEXTF](#KTEXTF)
- <a name="KTINLN"></a>Consider using inline classes instead of plain primitives (e.g. currency, time). [#KTINLN](#KTINLN)

Resources
---------

- <a name="HCDRES"></a>Don't hardcode resource values with the exception of 8dp grid dimen values (`8dp`, `16dp`, `24dp`, `32dp`, `48dp`, etc.). Put resource values in separate XML files. [#HCDRES](#HCDRES)
- <a name="DEEPLA"></a>Be careful with an overly deep hierarchy of layouts and views. Leverage the power of ConstraintLayout. [#DEEPLA](#DEEPLA)
- <a name="OVRDRW"></a>Watch out for overdraws. [#OVRDRW](#OVRDRW)
- <a name="VCTDRW"></a>Use vector drawables whenever possible. Ask your designer to provide you with SVG files. [#VCTDRW](#VCTDRW)
- <a name="ADPICO"></a>Use adaptive launcher icons. [#ADPICO](#ADPICO)
- <a name="IMGRES"></a>Use PNG only for graphics (not vectors) and JPEG for photos to optimize APK size. Consider using WebP image format and an image compression tool. [#IMGRES](#IMGRES)
- <a name="THMSTY"></a>Distinguish between themes and styles. Put them in separate XML files. [#THMSTY](#THMSTY)
- <a name="THMOVR"></a>Use `ThemeOverlay` theme descendants to apply local changes to themes. [#THMOVR](#THMOVR)
- <a name="TXTAPR"></a>Use `android:textAppearance` for text style. [#TXTAPR](#TXTAPR)
- <a name="TXTSTY"></a>Use predefined text sizes and try to avoid using custom values. Use directly or extend [Material text appearance](https://material.io/design/typography/the-type-system.html#type-scale) styles from `TextAppearance.AppCompat`. [#TXTSTY](#TXTSTY)
- <a name="TOOLAT"></a>Use XML attributes in the `tools` namespace (`tools:src`, `tools:listitem`, `tools:visibility`, etc.) that enable useful design-time features. [#TOOLAT](#TOOLAT)
- <a name="SAMPLE"></a>Use `@tools:sample/*` resources to inject placeholder data or images into views. Avoid using custom sample resources which increase APK size. [#SAMPLE](#SAMPLE)

Project
-------

- <a name="SEMVER"></a>Follow [Semantic Versioning](http://semver.org/) for app versioning. [#SEMVER](#SEMVER)
- <a name="DYNVER"></a>Don't use dynamic versions for dependencies, such as "1.0.+". [#DYNVER](#DYNVER)
- <a name="TGTSDK"></a>Target SDK should be set to the maximum API level. [#TGTSDK](#TGTSDK)
- <a name="GRDMOD"></a>Separate the project into multiple Gradle modules by layer and feature. Modules can be built in parallel or isolated, which reduces build time. [#GRDMOD](#GRDMOD)
- <a name="GRDBRF"></a>Keep the `build.gradle` file brief and don't overfill it with config that is not relevant to this specific module or app. You can extract some common tasks or settings to a separate file. [#GRDBRF](#GRDBRF)
- <a name="GRDSRC"></a>Consider using `buildSrc` folder with `Versions`, `Dependencies` and custom tasks or plugins for the whole project. [#GRDSRC](#GRDSRC)
- <a name="CONFIG"></a>Use a config class to store all configuration values (API URLs, API keys, log settings, etc.) in one place. Avoid defining config values in multiple places, like `build.gradle`, `AndroidManifest.xml`, config class, etc. [#CONFIG](#CONFIG)
- <a name="CONINT"></a>Use a continuous integration service to build your project, test your code and deploy APK file to the Play Store. [#CONINT](#CONINT)

Git
---

- <a name="GITGDL"></a>Follow [STRV Git Guidelines](https://github.com/strvcom/strv-guidelines/blob/master/git.md). [#GITGDL](#GITGDL)
- <a name="GITMSG"></a>Follow [How to Write a Git Commit Message](http://chris.beams.io/posts/git-commit/). [#GITMSG](#GITMSG)
- <a name="GITCAP"></a>Capitalize the subject line in commit message. [#GITCAP](#GITCAP)
- <a name="GITIMP"></a>Use the imperative mood in the subject line of a commit message. [#GITIMP](#GITIMP)
- <a name="GITFLO"></a>Consider using Git Flow or a similar branching system. [#GITFLO](#GITFLO)

UI & UX
-------

- <a name="MATERL"></a>Follow [Material Design Guidelines](https://material.io/design/). [#MATERL](#MATERL)
- <a name="LANDSC"></a>The app should support both landscape and portrait mode, even in a situation where the portrait mode is forced in production build. [#LANDSC](#LANDSC)
- <a name="SPLTSC"></a>The app should support split screen mode. [#SPLTSC](#SPLTSC)
- <a name="STATES"></a>Handle all possible edge cases and states: content, progress, offline, empty, etc. [#STATES](#STATES)
- <a name="PRGIND"></a>Show progress indicator when something is loading. [#PRGIND](#PRGIND)
- <a name="PRGDLG"></a>Don't use progress dialogs. [#PRGDLG](#PRGDLG)
- <a name="RIPPLE"></a>Clickable views should have a ripple touch feedback. [#RIPPLE](#RIPPLE)
- <a name="CLCSIZ"></a>Clickable views should have at least `48dp` width/height. [#CLCSIZ](#CLCSIZ)
- <a name="ORIDLG"></a>Dialogs should not disappear after an orientation change or Activity restore. [#ORIDLG](#ORIDLG)
- <a name="ORISCR"></a>ScrollView or RecyclerView should keep the scroll position after an orientation change, Activity restore or popping the backstack. [#ORISCR](#ORISCR)
- <a name="ORISEL"></a>Selectable views should keep the select state after an orientation change or Activity restore. [#ORISEL](#ORISEL)
- <a name="ORILOA"></a>If it's already loaded, don't load data again after an orientation change or Activity restore. [#ORILOA](#ORILOA)
- <a name="OFFLIN"></a>Strive to make the app offline first by using a caching method (e.g. Room, Firestore, Realm). [#OFFLIN](#OFFLIN)
- <a name="TSTAPP"></a>Always test the app on various screen sizes, densities and Android versions. [#TSTAPP](#TSTAPP)
- <a name="TSTKIL"></a>Always test if the app works properly when the system kills it on inactivity. You can use ADB Idea plugin, "Don't keep activities" in developer options or [ADB script](https://gist.github.com/mlykotom/18d48ec6cc75f935ed7658867cedad5f). [#TSTKIL](#TSTKIL)
