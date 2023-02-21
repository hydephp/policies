# Backwards Compatability

## Versioning Scheme

HydePHP and its other first-party packages follow [Semantic Versioning](https://semver.org). Major framework releases may contain breaking changes. Minor and patch releases should never contain breaking changes.

When referencing the HydePHP framework or its components from your application or package, you should always use a version constraint such as ^1.0, since major releases of HydePHP do include breaking changes. However, we strive to always ensure you may update to a new major release in one day or less.

### Version coupling

The major versions of the two core packages, [`hyde/hyde`](github.com/hydephp/hyde`) and [`hyde/framework`](github.com/hydephp/framework) are tied together; meaning that both versions get their major version number bumped at the same time. So if your framework version is v1.x, so should your Hyde version be. Minor and patch versions are handled independently within the packages.

## Named Arguments
[Named arguments](https://www.php.net/manual/en/functions.arguments.php#functions.named-arguments) are not covered by Hyde's backwards compatibility guidelines. We may choose to rename function arguments when necessary in order to improve the Hyde codebase. Therefore, using named arguments when calling Hyde methods should be done cautiously and with the understanding that the parameter names may change in the future.

## Extra Information

This document was based on the Laravel release documentation. https://laravel.com/docs/master/releases
