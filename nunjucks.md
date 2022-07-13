# Useful nunjucks snippets

This is a short list of some useful nunjucks commands. [Find the official nunjucks documentation](https://mozilla.github.io/nunjucks/templating.html) at the Nunjucks website. Nunjucks is a powerful templating language.

## Find out what’s in an object

```
{{ hmpoPageKey | dump }}
```

## Add things to the expected output of a block

If you want to keep the original content of a block, but then add extra code to it, use the `super()` command. This will add the original content at the point you specify, like so:

```
{% block standardBlock %}
<p>My extra code</p>
{# Then call super to add the content generated in the other definition of standardBlock. #}
{{ super() }}
{# You could do this before your addition as well. #}
{% endblock %}
```

## Retrieve content from a yaml file (GDS only)

```
{% set yourVar = translate("firstLevelvar.secondLevelvar.thirdLevelvar") %}

{% if 'condition' in translate(yourVar) %}
{# for example #}
{% include "[path-to-content]" %}
{% endif %}
```
Set can either be used on a single line (as above) or enclose multiple lines, like so:
```
{% set longHTML %}
 <p>This is some content</p>
{% endset %}
{{ longHTML }}
```