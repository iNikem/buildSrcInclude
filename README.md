This project tries to demonstrate a problem with including a Grade precompiled script plugin from another project using composite build.

`projectA` hosts a script plugin `com.example.codegen.gradle.kts`.

`projectB` tries to use it in its `buildSrc`.

When building `projectB`:

```
cd projectB
./gradlew build --console plain --include-build ../projectA
```

I get the following error:

```
> Task :buildSrc:compileKotlin FAILED
e: /Users/nsalnikovtarnovski/Documents/workspace/buildSrcInclude/projectB/buildSrc/src/main/kotlin/com.example.user.gradle.kts: (7, 3): Unresolved reference: compileOnly
```

When I remove `id("com.example.codegen")` from `com.example.user.gradle.kts` then error dissappears as well.
