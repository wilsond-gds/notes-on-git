# Useful nunjucks snippets

## Find out what’s in an object

```
{{ hmpoPageKey | dump }}
```

## Add things to the expected output of a block

If you want to keep the original content of a block, but then add extra code to it, use the `super()` command. This will add the original content at the point you specify, like so:

```
{% block standardBlock %}
<p>My extra code</p>
{# Then call super to add the content generated in the other definition of standardBlock. You could do this before your addition as well. #}
{{ super() }}
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