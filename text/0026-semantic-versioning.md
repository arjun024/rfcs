# Semantic Versioning of Buildpacks and Builders

## Summary

As of date all Paketo buildpack releases use the semver syntax for versioning, but does not necessarily follow semver semantics.

The [CNB Buildpacks spec](https://github.com/buildpacks/spec/blob/buildpack/v0.6/buildpack.md) says:

> The buildpack version:
>
> - MUST be in the form <X>.<Y>.<Z> where X, Y, and Z are non-negative integers and must not contain leading zeros.
> 
>    - Each element MUST increase numerically.
> 
>    - Buildpack authors will define what changes will increment X, Y, and Z.


It does not define what changes will increment the Major (`X`), Minor (`Y`) and Patch (`Z`) versions
of buildpack releases.

This RFC attempts to set guidelines and good practices for Paketo Buildpack
authors/maintainer to follow when a buildpack's major, minor, and patch version has to be bumped.

## Semantics

Semantic Versioning 2.0.0 defines versioning syntax as follows [semver.org](https://semver.org/):

> Given a version number MAJOR.MINOR.PATCH, increment the:
> 
>   - MAJOR version when you make incompatible API changes,
> 
>   - MINOR version when you add functionality in a backwards compatible manner, and
> 
>   - PATCH version when you make backwards compatible bug fixes.

The idea is to conform to the above semantics as much as possible.
<br/><br/>
In terms of Paketo Buildpacks/Builders, this translates to:

* Bumping MAJOR is analogous to an "`app or related buildpacks may not work without change`" relation between releases.
* Bumping MINOR is analogous to an "`updates or adds features`" relation between releases.
* Bumping PATCH is analogous to a "`fixes issue`" relation between releases.
<br/><br/>


The following table lists the usual circumstances/events where bumping a particular component is expected.

| `Major` | `Minor` | `Patch` | `Notes` |
|-|-|-|-|
| <Any incompatible change> | <Feature additions but compatible with previous release> | <Fixes but no major feature changes> |  |
| Change in Provides/Requires API | Addition/removal of dependency but default version not changed to incompatible version |  |  |
| Change in supported Stacks | Buildpack runs a new command the causes change in behavior |  |  |
| Change in Buildpack API version | Change of expected build tool version to package buildpack (e.g. go version) |  |  |
| Change in Buildpack ID | New Configuration option (e.g. new environment variable support) |  |  |
| Default version of dependency bumped to incompatible version |  |  |  |
| (For language-family buildpacks) Implementation buildpack major bumps that cause incompatible change |  |  |  |
| (For Builders) Buildpack major bumps |  |  |  |
| (For Builders) Incompatible change in lifecycle, stack images |  |  |  |
