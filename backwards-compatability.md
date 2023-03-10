# Backwards Compatability

## Abstract

Ensuring that HydePHP projects can be upgraded smoothly is a top priority for us. For that reason, we have a backwards compatability promse, that guarantees that only major versions contain breaking changes. This document details how we operate and adhere to this, as well as what code is covered and what is not.

## Versioning Scheme

HydePHP and its other first-party packages follow [Semantic Versioning](https://semver.org). Major framework releases may contain breaking changes. Minor and patch releases should never contain breaking changes.

When referencing the HydePHP framework or its components from your application or package, you should always use a version constraint such as ^1.0, since major releases of HydePHP do include breaking changes. However, we strive to always ensure you may update to a new major release in one day or less.

### Version coupling

The major versions of the two core packages, [`hyde/hyde`](github.com/hydephp/hyde`) and [`hyde/framework`](github.com/hydephp/framework) are tied together; meaning that both versions get their major version number bumped at the same time. So if your framework version is v1.x, so should your Hyde version be. Minor and patch versions are handled independently within the packages.

Other first-party packages are independently versioned.

## Named Arguments

[Named arguments](https://www.php.net/manual/en/functions.arguments.php#functions.named-arguments) are not covered by Hyde's backwards compatibility guidelines. We may choose to rename function arguments when necessary in order to improve the Hyde codebase. Therefore, using named arguments when calling Hyde methods should be done cautiously and with the understanding that the parameter names may change in the future.

## Packages Covered

### Abstract

The HydePHP ecosystem consists of a couple parts, or packages, some of which have differing backwards compatability promises.

### Overview

Here is an overview of these packages and their adherance to this policy

| Package                | BC Coverage? | Details                                 |
|:-----------------------|:-------------|:----------------------------------------|
| Hyde/Hyde              | Yes |                                         |
| Hyde/Framework         | Yes | Some namespaces are excluded, see below |
| Hyde/Realtime-Compiler | Partial      |                                         |
| Hyde/Testing           | None         |                                         |

## Exceptions

In general, public class members and interfaces, as well as base/abstract classes intended to be extended are covered by the BC promise. However, there are some exceptions. These apply to all packages in the ecosystem.

Here is a quick overview: (See further information below)

| Code Type                   | Covered by BC? | Details                                                           | 
|:---------------------------|:--------------|:-----------------------------------------------------------------|
| Private class members       |                | No                                                                |
| Protected class members     | Partially      | Only in classes designed to be extended)                          | 
| Public class members        | Yes            |                                                                   | 
| Unreleased code             | No             |                                                                   | 
| Code marked as experimental | Never          |                                                                   | 
| Code marked as internal     | Never          |                                                                   | 


### Code excluded from the BC promise

Tests and code within testing namespaces are not covered by the BC promise. Nor are classes or code marked as `@internal` or `@experimental`.
Any package in the 0.x version range has, per the SemVer spec, no backwards compatability promise and may be unstable.
Prereleases such as alpha, beta, and dev releases may also be unstable and should not be relied upon.

### Code only partially covered by BC

In general, protected class members (methods and properties) have limited BC support. This means that they may be refactored and changed when the need arises. However, care should be taken when changing protected class members of classes that are designed to be extended (for example base/abstract classes like BuildTasks and the Extensions API)
 
Command classes are only partly covered by the BC promise as most of their class members are protected. In general, the console commands are not designed to be extended, and should be done so at your own risk.

### Unreleased code

As the backwards compatabilty promise only kicks in upon the release of the given code, any code t that is unreleased, for example on the development branches, is not yet covered by the BC promise. You should always use the latest stable version when building something that depends on the framework code. 


### Security fixes

If a security vulnerability which can only be resolved using a breaking change is discovered, we may consider a BC break to be acceptable. In that case this change will be clearly communicated, and may be accompaniade with a security advisory.

## Extra Information

This document was based on the Laravel release documentation. https://laravel.com/docs/master/releases,
and inspired by the Symfony BC promise. https://symfony.com/doc/current/contributing/code/bc.html
