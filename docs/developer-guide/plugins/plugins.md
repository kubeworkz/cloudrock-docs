# Cloudrock plugins

## Plugin as extension

Cloudrock extensions are developed as auto-configurable plugins. One plugin
can contain several extensions which is a pure Django application by its
own. In order to be recognized and automatically connected to Cloudrock
some additional configuration required.

Extensions' URLs will be registered automatically only if
`settings.CLOUDROCK_CORE['EXTENSIONS_AUTOREGISTER']` is `True`, which is
default.

Create a class inherited from
`cloudrock_core.core.CloudrockExtension`. Implement methods which
reflect your app functionality. At least `django_app()`
should be implemented.

Add an entry point of name `cloudrock_extensions` to your package
`setup.py`. Example:

> ``` python
> entry_points={
>     'cloudrock_extensions': ('cloudrock_demo = cloudrock_demo.extension:DemoExtension',)
> }
> ```

## Plugin documentation

1. Keep plugin's documentation within plugin's code repository.

1. The documentation page should start with plugin's title and
    description.

1. Keep plugin's documentation page structure similar to the Cloudrock's main documentation page:

    **Guide** - should contain at least **installation** steps.
    **API** - should include description of API extension, if any.
