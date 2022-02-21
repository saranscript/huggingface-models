---
widget:
- text: " htmlOn ||| <div"
---

# Work In Progress

# How to use?

To generate text with HTML, the sentence must start with ` htmlOn |||` (note the space at the beginning 😉). To generate normal text, you don't need to add anything. 
 
# Training details

We continued the pre-training of [gpt2](https://huggingface.co/gpt2).

Dataset:[Natural_Questions_HTML_reduced_all](https://huggingface.co/datasets/SaulLu/Natural_Questions_HTML_reduced_all)
50% of the examples in the training data contained all HTML tags with only their `id` and `class` attributes. 50% of the examples were just plain text.

Training example with metadata: 
```
 htmlOn |||
<li id:n-sitesupport><a>Donate to Wikipedia</a></li>
<li id:n-shoplink><a>Wikipedia store</a></li>
</ul></div></div><div class:portal id:p-interaction><h3 id:p-interaction-label>Interaction</h3>
<div class:body><ul><li id:n-help><a>Help</a></li>
<li id:n-aboutsite><a>About Wikipedia</a></li>
<li id:n-portal><a>Community portal</a></li>
<li id:n-recentchanges><a>Recent changes</a></li>
<li id:n-contactpage><a>Contact page</a></li>
</ul></div></div><div class:portal id:p-tb><h3 id:p-tb-label>Tools</h3>
<div class:body><ul><li id:t-whatlinkshere><a>What links here</a></li>
<li id:t-recentchangeslinked><a>Related changes</a></li>
<li id:t-upload><a>Upload file</a></li>
<li id:t-specialpages><a>Special pages</a></li>
<li id:t-permalink><a>Permanent link</a></li>
<li id:t-info><a>Page information</a></li>
<li id:t-wikibase><a>Wikidata item</a></li>
<li id:t-cite><a>Cite this page</a></li>
</ul></div></div><div class:portal id:p-coll-print_export><h3 id:p-coll-print_export-label>Print/export</h3>
<div class:body><ul><li id:coll-create_a_book><a>Create a book</a></li>
<li id:coll-download-as-rdf2latex><a>Download as PDF</a></li>
<li id:t-print><a>Printable version</a></li>
</ul></div></div><div class:portal id:p-lang><h3 id:p-lang-label>Languages</h3>
<div class:body><ul><li class:interlanguage-link interwiki-ca><a class:interlanguage-link-target>Català</a></li>
<li class:interlanguage-link interwiki-da><a class:interlanguage-link-target>Dansk</a></li>
<li class:interlanguage-link interwiki-de><a class:interlanguage-link-target>Deutsch</a></li>
<li class:interlanguage-link interwiki-es><a class:interlanguage-link-target>Español</a></li>
<li class:interlanguage-link interwiki-eu><a class:interlanguage-link-target>Euskara</a></li>
<li class:interlanguage-link interwiki-fa><a class:interlanguage-link-target>فارسی</a></li>
<li class:interlanguage-link interwiki-fr><a class:interlanguage-link-target>Français</a></li>
<li class:interlanguage-link interwiki-id><a class:interlanguage-link-target>Bahasa Indonesia</a></li>
<li class:interlanguage-link interwiki-nl><a class:interlanguage-link-target>Nederlands</a></li>
<li class:interlanguage-link interwiki-pt><a class:interlanguage-link-target>Português</a></li>
<li class:interlanguage-link interwiki-fi><a class:interlanguage-link-target>Suomi</a></li>
<li class:interlanguage-link interwiki-vi><a class:interlanguage-link-target>Tiếng Việt</a></li>
<button class:mw-interlanguage-selector mw-ui-button>5 more</button>
</ul><div class:after-portlet after-portlet-lang><span class:wb-langlinks-edit wb-langlinks-link><a class:wbc-editpage>Edit links</a></span></div>
</div></div></
```
