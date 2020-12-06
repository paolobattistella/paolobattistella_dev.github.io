---
layout: post
title: "Extension to access properties of context into twig templates of Prestashop"
categories: development
tags: php
---

I have created an extension to access properties of context into `twig` templates of Prestashop

## Setup

Create the file `src/Twig/Extension/PsContext.php` into module folder with the following content:

```php
<?php

namespace MyModule\Twig\Extension;

class PsContext extends \Twig_Extension
{
    /**
     * {@inheritdoc}
     */
    public function getFunctions()
    {
        return array(
            new \Twig_SimpleFunction('from_context', [$this, 'getFromContext']),
        );
    }

    /**
     * {@inheritdoc}
     */
    public function getName()
    {
        return 'ps_context';
    }

    /**
     * {@inheritdoc}
     */
    public function getFromContext(?string $property = '')
    {
        $context = \Context::getContext();
        return array_reduce(
            explode('.', $property),
            function($o, $p) {
                return is_numeric($p) ? ($o[$p] ?? null) : ($o->$p ?? null);
            },
            $context
        );
    }
}
```

Add `Twig` extension to services of your module.

Add following lines to `services.yml`:

```
  mymodule.twig.ps_context_extension:
    class: MyModule\Twig\Extension\PsContext
    tags:
      - { name: twig.extension }
```


## Contributor

Thanks to [alterphp] for the tip

[alterphp]: https://github.com/alterphp/components/blob/master/src/AlterPHP/Component/Twig/Extension/Reflection.php