baked.js
========

A static website generator in JS, powerered by prismic.io.

## Use

- at the root of the project:
- put your files into `/to_generate/`
- clean `/generated/`
- (run `npm install` if needed)
- `node src/server.js to_generate/ generated/`
	- ⇒ generate the static files into `/generated/static/`
	- you can add options `--debug --no-async` to make it easier to debug
- `grunt`
	- ⇒ generate the JS lib (used for dev mode—source files directly opened in the browser)
- À table !

## Notes

- page in dev mode don't have the global map of exiting pages, so:
	- the page a URL `http://host/foo/bar.html` could be
		- the file `foo/bar.html` (if the generated files are put at the root of `host`)
		- the file `bar.html` (if the generated files are put in the dir `foo` of `host`)
	- `url_to` have to be relative (how to link to a global file without knowning what is the origin point?)
	- the custom routes can't be honored, even simple rename (how can we know which route should be used without reading the called file?)
- the server build a DOM structure (using JSDOM) in order to navigate inside it, so:
	- The tags `<% %>` can't be used, because JSDOM doesn't like them
