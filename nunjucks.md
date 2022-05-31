# Useful nunjucks snippets

## Find out what’s in an object

```
{{ hmpoPageKey | dump }}
```

## Add things to the expected output of a block

```
{% block standardBlock %}
Before super is called
{# will contain the content generated in standardBlock #}
{{ super() }}
After super is called
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