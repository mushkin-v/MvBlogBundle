MvBlogBundle
============

Blog Bundle for symfony2 v2.1 &amp; v2.2

## INSTALLATION with COMPOSER 

You need have installed Symfony2 with Composer or have a composer.json file

1)  Add to composer.json to the `require` key  

``` 
"mv/mv-blog-bundle": "1.0.*",
"Trsteel/ckeditor-bundle": "master@dev"
``` 
The second requirement here because only dev version available for Symfony 2.1 and composer won't install with alpha minimal stability

you need also have the root key:
``` 
"minimum-stability": "alpha",
``` 
Because this is an alpha version

2)  Add to your AppKernel.php

```
new Mv\BlogBundle\MvBlogBundle(),
new Trsteel\CkeditorBundle\TrsteelCkeditorBundle(),
new Knp\Bundle\PaginatorBundle\KnpPaginatorBundle(),
```

3)  Add to routing.yml

```
mv_blog:
    resource: "@MvBlogBundle/Controller/"
    type:     annotation
    prefix:   /
```

4)  See Resources/Example/security.yml.example to configure access to the admin panel

This is for dev tests only.

Ensure you have in your AppKernel.php

```
new JMS\AopBundle\JMSAopBundle(),
new JMS\SecurityExtraBundle\JMSSecurityExtraBundle(),
```

5)  See Resources/Example/config.yml.example

This bundle send mails, a parameter is required for the email from.

Ensure you have in your AppKernel.php

```
new Symfony\Bundle\SwiftmailerBundle\SwiftmailerBundle(),
```

6)  Comments are SoftDeleteable, see Resources/Example/config.yml.example

Run update with composer

```
php path/to/composer.phar update
```

7)  You have to implement (if you don't have yet) an user management

You have access to admin panel in dev mode to see it, but you can't keep it in production mode.
ex: FOSUserBundle can help you.

Surcharge app/Resources/MvBlogBundle/views/_logout-link.html.twig to have your logout link.
See original in Mv/BlogBundle/Resources/views/_logout-link.html.twig

You can also surcharge base.admin-layout.html.twig & base.layout.html.twig to change CSS, JS or this templates inherit from (ex: to integrate your header, footer or what you need)

8)  Build Database

ex:
```
app/console doctrine:schema:update
```
or to have dump sql:
```
app/console doctrine:schema:update --dump-sql
```

9)  Blog is accessible on /blog and Admin panel on /badp

Enjoy...

To be continued