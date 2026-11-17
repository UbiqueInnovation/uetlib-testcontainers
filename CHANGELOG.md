# CHANGELOG

## 3.0.2

- Use shared Maven workflows at `v1.1.0`: wait for the SonarCloud quality gate and analyse with the
  uetlib-only Sonar token.
- Use shared Maven build and publish workflows at `v1.0.0` to enforce formatting checks in CI.

## 3.0.1

- Clarify configuration-property migration guidance for consumers.

## 3.0.0

- Move Java packages and class references from `ch.ubique.uetlib` to `ch.uetlib`.

### Breaking changes

- Move Java packages from `ch.ubique.backend` to `ch.uetlib`, including class-name resources. The combined OpenRewrite
  migration also renames known Spring configuration keys to `ch.uetlib.*`.
- Remove the inherited Ubique Artifactory repository and deployment destination; private consumers must configure their
  own registry.
- Add Apache-2.0 licensing for original code, preserve third-party licenses, and add public project metadata and
  contribution/security guidance.

- Move Maven coordinates from `ch.ubique:uetlib-*` to `ch.uetlib:uetlib-*`.
- Align uetlib parent, BOM and library references with the migration releases.

### Migration

After the migration releases and `uetlib-rewrite` are published, run this from the consuming project, then review the
diff and run its tests:

```sh
mvn -U org.openrewrite.maven:rewrite-maven-plugin:6.46.1:run \
  -Drewrite.recipeArtifactCoordinates=ch.uetlib:uetlib-rewrite:RELEASE \
  -Drewrite.activeRecipes=ch.uetlib.MigrateToPublicUetlib
```

The recipe updates Maven coordinates/versions, Java references and known class-name resources. Review application-owned
packages under the old namespace, Kotlin, reflection patterns, native-access module flags and persisted class names
separately. Use `:dryRun` instead of `:run` to preview a patch.

## 2.1.2

- latest uetlib parent
- version updates

## 2.1.1

- updated actions to not run tests twice for sonar
- update uetlib version

## 2.1.0

- NullMarked
- Add new `uetlib-testcontainers-kafka` module

## 2.0.0

- Uetlib 2.0

## 1.2.1

### Improvements

- Update `testcontainers-redis` to the new group id `org.testcontainers`.

## 1.2.0

### Improvements

- Add testcontainers-influxdb and testcontainers-redis
- Renovate Version Updates

## 1.1.0

### Improvements

- Latest uetlib dependencies with Spring Boot 3.5 support

## 1.0.0

First release.

