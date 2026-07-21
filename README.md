# HTML-ahref
Hypertext Markup Language's "a href" link/anchor command.

```
<a href="URL">anchor text</a>
```

```
<a href="URL" title="Linktitle">anchor text</a>
```
## What values can href have?
The values for href in HTML are clearly defined to ensure that linking works properly. The au­tho­rized values for href are as follows:
<ul>
	<li>An absolute URL: When using a href, the absolute URL is the classic example. It redirects directly to an external website and contains the domain name, the path and (if available) the file name. Example: &lt;a href=&quot;www.examplesite.com/topic/index.html&quot;&gt;Absolute link to the example page&lt;/a&gt;</li>
	<li>A relative URL: In a relative URL, you only specify the path (the file name is optional). For this reason, relative URLs are much shorter than absolute ones. Example: &lt;a href=&quot;/topic/index.html&quot;&gt;Relative link to example page&lt;/a&gt;</li>
	<li>Link to an element: The direct link to an element is possible if it has a defined ID. This allows you to in­ter­nal­ly link different sections of your website. Example: &lt;a href=&quot;#section3&quot;&gt;Direct link to an element&lt;/a&gt;</li>
	<li>Other protocols: href is also suitable for other protocols, such as linking directly to an email address. This works via mailto:. Other protocols may include https://, ftp://, or file:.</li>
	<li>Scripts: Scripts, such as JavaScript, are also au­tho­rized values for a href. Example: href="javascript:alert('Do you have any further questions?');"></li>
</ul>

## Five examples for how to use a href
You can use a href for different purposes. Below we’ll show you some of the most common use cases for href in HTML.

### 1. Use an image as a link
Use the following code to set an image as a link to a subpage:
```
<a href="https://www.examplesite.com"><img src=" /exampleimage.jpg" alt="image description"></a>
```
### 2. Link to an email address
Use mailto: to link an email address:
```
<a href="mailto:smith@examplesite.com">smith@examplesite.com</a>
```
The visitor’s email client will open when they click the link and the address (smith@ex­am­ple­site.com) will au­to­mat­i­cal­ly be inserted as the recipient. Al­ter­na­tive­ly, they can also copy and paste the email address into the program or to another location.

### 3. Link to a phone number
You can also link a phone number with a href. This is useful if someone accesses your site using a smart­phone and wants to contact you directly. The link looks like this:
```
<a href="tel:+11231234567">0123 1234567</a>
```
It is important to add a plus sign and the in­ter­na­tion­al dialing code after the telephone reference tel:. The zero in the area code is not included.

### 4. Link to JavaScript
You can also link to JavaScript using href. The cor­re­spond­ing code is:
```
<a href="javascript:Example ( )">example</a>
```
### 5. Open a link in a new tab or window
While links are useful, be careful not to send your visitors to an external site directly from your website. With this in mind, it is useful for the link to open in a new tab or a new window. Users will then remain on your site and can look at any ad­di­tion­al in­for­ma­tion at another time. The code for opening a link in a new tab or window looks like this:
```
<a href="http://www.example.org" target="_blank">http://www.example.org</a>
```
### Tip
Create your perfect website in just a few steps! The <a href="https://www.ionos.com/websites/website-builder">Website Builder</a> from IONOS offers useful tools that are easy to manage, allowing you to easily create a pro­fes­sion­al online presence. If you would rather leave it up to our experts, they can take over the design for you and build a website according to your in­di­vid­ual re­quire­ments. Choose a solution that fits your needs.

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
## href="#"
Scrolls to the top of a document. I knew that.

But I’m writing because #top will also scroll to the top if there isn’t another element with id="top" in the document. I didn’t know that.

(Spec: “If decodedFragment is an ASCII case-insensitive match for the string top, then return the top of the document.”)

Update: HTeuMeuLeu pointed out to me on Mastodon that you can use #page= to deep-link to a specific page in a PDF, e.g. my-file.pdf#page42 would like to page 42 in the file.

## href=""
Reloads the current page, preserving the search string but removing the hash string (if present).

URL					Resolves to
/path/				/path/
/path/#foo			/path/
/path/?id=foo		/path/?id=foo
/path/?id=foo#bar	/path/?id=foo

## href="."
Reloads the current page, removing both the search and hash strings (if present).

Note: If you’re using href="." as a link to the current page, ensure your URLs have a trailing slash or you may get surprising navigation behavior. The path is interpreted as a file, so "." resolves to the parent directory of the current location.

URL					Resolves to
/path				/
/path#foo			/
/path?id=foo		/
/path/				/path/
/path/#foo			/path/
/path/?id=foo		/path/
/path/index.html	/path/

Update 2025-08-15: as pointed out by @AmeliaBR on Mastodon, “reloads the current page” probably isn’t the best terminology for this. It’s more like “loads the default index page for the current directory, based on the URL structure” which might be a reload, but might be something else based on the current URL (see my note and table above).

## href="?"
Reloads the current page, removing both the search and hash strings (if present). However, it preserves the ? character.

Note: Unlike href=".", trailing slashes don’t matter. The search parameters will be removed but the path will be preserved as-is.

URL					Resolves to
/path				/path?
/path#foo			/path?
/path?id=foo		/path?
/path?id=foo#bar	/path?
/index.html			/index.html?

## href="data:"
You can make links that navigate to data URLs. The super-readable version of this would be:
```
<a href="data:text/plain,hello world">
  View plain text data URL
</a>
```
But you probably want data: URLs to be encoded so you don’t get unexpected behavior, e.g.
```
<a href="data:text/plain,hello%20world">
  View plain text data URL
</a>
```
Go ahead and try it (FYI: may not work in your user agent). Here’s a plain-text file and an HTML file.

## href="video.mp4#t=10,20"
Media fragments allow linking to specific parts of a media file, like audio or video.

For example, video.mp4#t=10,20 links to a video. It starts play at 10 seconds, and stops it at 20 seconds.

(Support is limited at the time of this writing.)

## See For Yourself
I tested a lot of this stuff in the browser and via JS. I think I got all these right.

Thanks to JavaScript’s URL constructor (and the ability to pass a base URL), I could programmatically explore how a lot of these href’s would resolve.

Here’s a snippet of the test code I wrote. You can copy/paste this in your console and they should all pass 🤞
```
const assertions = [
  // Preserves search string but strips hash
  // x -> { search: '?...', hash: '' }
  { href: '', location: '/path',               resolves_to: '/path' },
  { href: '', location: '/path/',              resolves_to: '/path/' },
  { href: '', location: '/path/#foo',          resolves_to: '/path/' },
  { href: '', location: '/path/?id=foo',       resolves_to: '/path/?id=foo' },
  { href: '', location: '/path/?id=foo#bar',   resolves_to: '/path/?id=foo' },
  
  // Strips search and hash strings
  // x -> { search: '', hash: '' }
  { href: '.', location: '/path',              resolves_to: '/' },
  { href: '.', location: `/path#foo`,          resolves_to: `/` },
  { href: '.', location: `/path?id=foo`,       resolves_to: `/` },
  { href: '.', location: `/path/`,             resolves_to: `/path/` },
  { href: '.', location: `/path/#foo`,         resolves_to: `/path/` },
  { href: '.', location: `/path/?id=foo`,      resolves_to: `/path/` },
  { href: '.', location: `/path/index.html`,   resolves_to: `/path/` },
  
  // Strips search parameters and hash string,
  // but preserves search delimeter (`?`)
  // x -> { search: '?', hash: '' }
  { href: '?', location: '/path',              resolves_to: '/path?' },
  { href: '?', location: '/path#foo',          resolves_to: '/path?' },
  { href: '?', location: '/path?id=foo',       resolves_to: '/path?' },
  { href: '?', location: '/path/',             resolves_to: '/path/?' },
  { href: '?', location: '/path/?id=foo#bar',  resolves_to: '/path/?' },
  { href: '?', location: '/index.html#foo',    resolves_to: '/index.html?'}
];

const assertions_evaluated = assertions.map(({ href, location, resolves_to }) => {
  const domain = 'https://example.com';
  const expected = new URL(href, domain + location).toString();
  const received = new URL(domain + resolves_to).toString();
  return {
    href,
    location,
    expected: expected.replace(domain, ''),
    received: received.replace(domain, ''),
    passed: expected === received
  };
});

console.table(assertions_evaluated);
```

