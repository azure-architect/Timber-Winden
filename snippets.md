# Snippets

## Twig  Debug
tw-deb :

    [agnostic]
		{% set args = {
	        'post_type': 'post',
	        'posts_per_page': 10 } %}
		{% set posts = Post(args) %}
		    {% for post in posts%}
		        {% set state = post %}
		            {{ include('@partials/debug.twig')}}
		    {% endfor %}
    [/agnostic]

## Base Query

	[agnostic]

	{% set args = {
        'post_type': 'post',
        'posts_per_page': 3
    } %}
You can set the context for semantic output here if you wish ( just change 'posts' to articles, or items, products, etc):
```angular2html

{% set posts = Post(args) %}
{% for article in articles %}

{{include('@sections/from-the-blog.twig')}}

{% endfor %}
[/agnostic]
```
This pulls in a template to present the data. Here is a slice showing how you output wp post content with handlebar formatting.  The template has the following code and formatting ( posts has been altered to use the semantic term article ) For the most part 'the_title' in wordpress would be 'post.title' or in this case 'article.title':

```angular2html

 <article class="flex flex-col items-start justify-between">
                <div class="relative w-full">
                    <img src="{{ article.thumbnail.src('medium') }}" alt="{{ article.thumbnail.alt }}" class="aspect-[16/9] w-full rounded-2xl bg-gray-100 object-cover sm:aspect-[2/1] lg:aspect-[3/2]">
                    <div class="absolute inset-0 rounded-2xl ring-1 ring-inset ring-gray-900/10"></div>
                </div>
                <div class="max-w-xl">
                    <div class="mt-8 flex items-center gap-x-4 text-xs">
                        <time datetime="2020-03-16" class="text-gray-500">Mar 16, 2020</time>
                        <a href="#" class="relative z-10 rounded-full bg-gray-50 px-3 py-1.5 font-medium text-gray-600 hover:bg-gray-100">Marketing</a>
                    </div>
                    <div class="group relative">
                        <h3 class="mt-3 text-lg font-semibold leading-6 text-gray-900 group-hover:text-gray-600">
                            <a href="#">
                                <span class="absolute inset-0"></span>
                                {{ article.title }}
                            </a>
                        </h3>
                       

```
