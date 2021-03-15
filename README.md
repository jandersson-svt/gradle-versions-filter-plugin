# Gradle Versions Filter Plugin

A simple Gradle plugin, built on the [Gradle Versions Plugin](https://github.com/ben-manes/gradle-versions-plugin) with sane no-configuration-defaults and customization options.


## Why?

The Gradle Version Plugin leaves it to the user to configure what is a valid release.

It became tiresome to copying a include or exclude policy to every project in a big codebase, so why not make a plugin out of it.
Having less configuration in the build scripts, is better.
It is fun to write a Gradle plugin with Kotlin :)

## How?

The plugin sets a sane default on what should be seen as the latest release. It either does this by having an inclusive (only include versions with these qualifiers) or the opposite, an exclusive policy.

It can also optionally (default actually) use only SemVer-compatible releases.

## Usage

Add the plugin to your build.gradle.kts (or build.gradle)

```kotlin
plugins {
   id("se.ascp.gradle.gradle-versions-filter") version "x.y.z"
}
```


```shell
$ ./gradlew dependencyUpdates
```

And that should be fine enough for most.

Options:

Option               | Default                                    | Description
-------------------- | -----------------------------------------  | --------------
defaultInclusive     | false                                      | The default strategy, excludes as default i.e. use the exclusiveQualifiers
inclusiveQualifiers  | "RELEASE","FINAL","GA"                     | The default inclusive qualifiers (if inclusive strategy is used) 
exclusiveQualifiers  | "alpha","beta","rc","cr","m","preview","b" | The default exclusive qualifiers (if exclusive strategy is used) 
strictSemVer         | true                                       | Only show strict SemVer-validated versions

.Example Configuration
```kotlin
versionsFilter {
    exclusiveQualifiers = ["rc", "alpha", "beta", "m"]
    defaultInclusive = true
}
```

This plugin should probably be deprecated at some point, if the options are given as a Pull Request (and accepted) to the original plugin.

## License

Released under the Apache License 2.0

[LICENSE](LICENSE)



