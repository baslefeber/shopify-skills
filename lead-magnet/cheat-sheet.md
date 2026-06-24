# The Shopify Liquid Cheat Sheet

The constructs you reach for daily, with the production-correct choice highlighted. Every filter, tag, and object path here is validated against the official Shopify docs. If it's on this page, it's real.

Part of the Shopify Developer Starter Kit from [learnshopify.dev](https://learnshopify.dev).

---

## Delimiters

```liquid
{{ output }}              {# prints a value #}
{% logic %}              {# does something, prints nothing #}
{{- trimmed -}}          {# dashes strip surrounding whitespace #}
{% comment %} ... {% endcomment %}
{% # inline comment %}
```

## Variables

```liquid
{% assign name = 'value' %}
{% assign total = product.price | times: quantity %}
{% capture block %}{{ product.title }} - {{ product.price | money }}{% endcapture %}
```

## Control flow

```liquid
{% if product.available %}In stock{% elsif product.tags contains 'preorder' %}Preorder{% else %}Sold out{% endif %}
{% unless cart.item_count == 0 %}{{ cart.item_count }} items{% endunless %}

{% case product.type %}
  {% when 'Shirt' %}Apparel
  {% when 'Mug' %}Drinkware
  {% else %}Other
{% endcase %}

{% for variant in product.variants %}
  {{ forloop.index }}: {{ variant.title }} - {{ variant.price | money }}
{% endfor %}
```

`forloop`: `.index`, `.index0`, `.first`, `.last`, `.length`. Loops cap at 50 iterations: use `{% paginate %}` for more.

> No parentheses in conditions, no ternary operator, no filters inside a comparison. Assign the computed value first, then compare.

## Money (never output a raw price)

```liquid
{{ product.price | money }}                    {# $19.99 #}
{{ product.price | money_with_currency }}       {# $19.99 CAD #}
{{ product.price | money_without_trailing_zeros }}
```

`product.price` is in cents. Never `divided_by: 100` yourself; currencies differ.

## Images (never a raw <img>)

```liquid
{{ product.featured_image
   | image_url: width: 800
   | image_tag: loading: 'lazy', widths: '300, 600, 900', sizes: '(min-width: 750px) 50vw, 100vw' }}
```

The above-the-fold hero is the exception: `loading: 'eager', fetchpriority: 'high'`, and preload it:

```liquid
{{ image | image_url: width: 1600 | preload_tag: as: 'image' }}
```

## Translations (never a hardcoded string)

```liquid
{{ 'products.product.add_to_cart' | t }}
{{ 'cart.general.items' | t: count: cart.item_count }}
```

Add the key to `locales/en.default.json`. Do not use `| t: default: '...'`; it fails the theme push.

## Everyday filters

```liquid
{{ value | default: 'Fallback' }}
{{ article.published_at | date: '%B %d, %Y' }}

{# String #}
{{ product.description | strip_html | truncate: 120 }}
{{ product.title | upcase }} {{ title | downcase }} {{ title | capitalize }}
{{ 'Hello World' | handleize }}          {# hello-world #}
{{ text | replace: 'old', 'new' | append: '!' | prepend: '> ' }}

{# Math #}
{{ price | times: 2 }} {{ n | plus: 1 }} {{ n | minus: 1 }} {{ n | round: 2 }}
{{ n | at_least: 1 }} {{ n | at_most: 10 }} {{ n | modulo: 2 }}

{# Array #}
{{ collection.products | where: 'available', true | size }}
{{ collection.products | map: 'title' | join: ', ' }}
{{ array | first }} {{ array | last }} {{ array | sort: 'price' }} {{ array | uniq }}
```

## Key objects

```liquid
{{ shop.name }} {{ shop.url }} {{ shop.currency }}
{{ product.title }} {{ product.vendor }} {{ product.url }} {{ product.available }}
{{ product.selected_or_first_available_variant.id }}
{{ product.featured_image }} {{ product.metafields.custom.material.value }}
{{ collection.title }} {{ collection.products.size }}
{{ cart.item_count }} {{ cart.total_price | money }}
{{ customer.first_name }} {{ customer.email }}
```

URLs that survive markets and locales (never hardcode `/cart`):

```liquid
{{ routes.cart_url }} {{ routes.all_products_collection_url }} {{ routes.account_url }}
{{ product.url }} {{ collection.url }}
```

## Metafields and metaobjects (never parse titles or tags)

```liquid
{{ product.metafields.custom.material.value }}

{% if product.metafields.custom.is_handmade.value %}Handmade{% endif %}

{# A metaobject reference returns the object; read its fields with .value #}
{% assign designer = product.metafields.custom.designer.value %}
{{ designer.name.value }}
```

Define the metafield in Settings → Custom data first, or it won't be exposed to the storefront.

## The product form and line-item properties

```liquid
{% form 'product', product %}
  <input type="hidden" name="id" value="{{ product.selected_or_first_available_variant.id }}">
  <input type="text" name="properties[Engraving]">
  <button type="submit" name="add">{{ 'products.product.add_to_cart' | t }}</button>
{% endform %}
```

Custom per-line data goes in `properties[...]`. A property starting with `_` is hidden from the customer but kept on the order. Other form types: `contact`, `customer_login`, `create_customer`, `cart`, `localization`.

## Sections, blocks, snippets

```liquid
{# Render a reusable snippet (isolated scope, pass variables) #}
{% render 'price', product: product %}

{# Render nested theme blocks in a section/block #}
{% content_for 'blocks' %}

{# Put this on every block wrapper for theme-editor drag-and-drop #}
<div {{ block.shopify_attributes }}>...</div>

{# Scoped CSS/JS (sections, blocks, snippets only) #}
{% stylesheet %} .card { color: var(--color-foreground); } {% endstylesheet %}
{% javascript %} /* component JS */ {% endjavascript %}
```

A section needs a `{% schema %}` with a `presets` entry to appear in the theme editor. Use `{% comment %}` in sections (`{% doc %}` is only valid in snippets and blocks).

## Gotchas that pass local checks and fail `shopify theme push`

- `"default": ""` is rejected. Provide a real default or omit `default`.
- `{% doc %}` in a section (only valid in snippets/blocks).
- A filter inside a comparison: `{% if i == n | plus: 1 %}`. Assign first.
- A `for` loop over a big collection with no `{% paginate %}`.
- A block `"type"` that doesn't resolve to a real `blocks/<type>.liquid` file.
- Inline `style="..."` inside `text`/`richtext` settings (sanitized away).
- `| t: default: '...'` (reserved-name error).

---

The golden rule: **if a filter, tag, or object path isn't in the official Shopify docs, it doesn't exist.** Validate with the Shopify Dev MCP `validate_theme` before you ship. Memory is not a substitute for the docs.

Want this as hands-on practice? [learnshopify.dev](https://learnshopify.dev) teaches every line above by having you write it against a live storefront.
