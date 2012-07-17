# Responsive Design in KandL

## the sizemore
and here's the editorial requirement, do mobile first then do desktop - this recognises that it's easier to add content/complexity/stuff to a mobile view than to take it away from a desktop view

We're essentially starting from scratch in K&L. Our Legacy applications will be replaced (eventually) by a greenfield application.

We're taking a fully responsive approach from the get-go.

The definition here needn't be Responsive by the two definitions following


## zeldman's view
Jeffrey Zeldman is the Godfather of web design
this definition is perhaps what we could call the UX definition

it's a good definition, but doesn't work for me from a technical standpoint.

## the adams definition
i've made this up.
it includes the zeldman definition, but is more technology focused.
I think it's pretty good

but there are some implications for product development. Are we delivering a responsive product by this definition

## Issues we face

## Mean Time to Mobile Parity
This is what we're seeking to minimise. Not picking on existing products, but they generally have this problem because of existing applications. We want the time delay between a feature appearing on desktop view and mobile view to be 0 days.

the current golden path as defined (we know this is changing, and is a combination of well meaning product and technical decisions)

1. do device detection in varnish/PAL and route requests to an appropriate sub-domain (www.bbc for desktop, m.bbc for mobile)
2. serve the sites via different applications (typically for large products) or via different controller/view combinations
3. do desktop first and support mobile separately

Responsive design doesn't require different domains for CDN failover

### problems
1. what's a tablet?
2. what if i'm browsing via a laptop and 3g dongle? - slow!
3. mobile device != mobile context

## mobile?
webviews in twitter/facebook clients, device fragmentation in android, etc. etc. means the idea of building one mobile site fails to scale.  We actually need to deliver a responsive design.

## browser support
we are also faced with this, 390 different web browsers

We're fighting a losing battle if we chose to list the browsers we explicitly support.

here's a interesting thought about our future.

So we're going to change our support model, to this:

# We will support all browsers. Just not equally.

and how are we going to do that?

# in three ways.

1. media queries - the core of RWD. flexible widths, layout shifting as space changes
2. cutting the mustard - only serving enhanced features to devices that are capable
3. assembling pages in the browser, sending html/js snippets from PAL to browser for rendering in the browser depending on capability

### There are questions here...

targeted css - still not entirely clear how we target browsers
cutting the mustard - from responsive news, may not suit our audience - we're testing this
js assembly - lots of benefits from a modular approach, caching, page layout. but some issues too - search engines, personalisation, language support & nations' editions, flash of original content


# so we'll support all browsers.
This is how we intend to develop the application. layering design and behaviour on top of content. So all browsers will get something, most browsers will get a super-enhanced version, and some will get a lesser experience.

this needs validation and some details worked out.


# Finally, the prototyping
here's what we worked on.

demo and some learning...

# points to consider
lots of different content on the same page makes for a huge payload
position on mobile and position on desktop are important, so source order, and width need to be considered together for all sizes
adding and removing interactions depending on the page layout. need to be sure we don't cause collisions
we still haven't solved the responsive image problem
big, high resolution screens from 10 feet away. too hard right now to do responsively

# modular page assembly

javascript kernel which does feature detection, loads extra content if device is capable.

both requests (initial and post-load) are cacheable. non-cacheable requests can be sent in their own request (cdn failover is easy-ish)

# what we need

ways of managing complex css (media queries, lots of modules, etc.)
we think we can do without jquery, but how can we be sure?
how do we monitor the behaviour of our pages when bits and pieces are being optionally constructed in the browser?
we're getting a responsive barlesque, so that's good!


 

