# Responsive Design in KandL
what is it, why do we need it, when are we getting it, how will we get it?

Glossing over a lot of issues here to give you an overview of responsive design, why it's important and how we're going to implement it.

One of the buzzwords of the day, like Progressive Enhancement, HTML5, gamification, web standards, social

lots of people using the phrase, lots of people using it wrongly, and there are a lot of variations in the actual meaning too.

also lots of people looking into it, we've got responsive news, the new channel sites, a new weather site coming and there's responsive aspects to both the new radio product and the mobile homepage

the UX&D Gel team and separately the TA team are both independently trying to get a consistent approach across all the products.

so what is it?


## the sizemore
and here's the editorial requirement, do mobile first then do desktop - this recognises that it's easier to add content/complexity/stuff to a mobile view than to take it away from a desktop view

defines an approach we may want to take, but needn't be Responsive by the two definitions following


## zeldman's view
Jeffrey Zeldman is the Godfather of web design
this definition is perhaps what we could call the UX definition
it was presented as the definition in a UX working group on RWD

it's a good definition, but doesn't work for me from a technical standpoint.

## the adams definition
i've made this up.
it includes the zeldman definition, but is more technology focused.
I think it's pretty good

but there are some implications for product development. Are we delivering a responsive product by this definition


## the standard approach
the golden path as defined by the platform and the frameworks team

1. do device detection in varnish/PAL and route requests to an appropriate sub-domain (www.bbc for desktop, m.bbc for mobile)
2. serve the sites via different applications (typically for large products) or via different controller/view combinations
3. do desktop first and support mobile separately

we don't really do this for food though

CDN Failover

### problems
1. what's a tablet?
2. what if i'm browsing via a laptop and 3g dongle? - slow!
3. mobile device != mobile context
4. mean time to mobile parity

which leads us neatly onto...

## mobile?
webviews in twitter/facebook clients, device fragmentation in android, etc. etc. means the idea of building one mobile site fails to scale.  We actually need to deliver a responsive design.

## browser support
we are also faced with this, 390 different web browsers

and here is our *current* browser support standards.

We're fighting a losing battle if we chose to list the browsers we explicitly support.

here's a interesting thought about our future.

So we're going to change our support model, to this:

# We will support all browsers. Just not equally.

and how are we going to do that?

# in three ways.

1. media queries - the core of RWD. flexible widths, layout shifting as space changes
2. cutting the mustard - only serving enhanced features to devices that are capable
3. assembling pages in the browser, sending html/js snippets from PAL to browser for rendering in the browser depending on capability

targeted css - still not entirely clear how we target browsers
cutting the mustard - from responsive news, may not suit our audience - we're testing this
js assembly - lots of benefits from a modular approach, caching, page layout. but some issues too - search engines

# so we'll support all browsers.
This is how we intend to develop the application. layering design and behaviour on top of content. So all browsers will get something, most browsers will get a super-enhanced version, and some will get a lesser experience.

this needs validation and some details worked out.


# Finally, the prototyping
here's what we worked on.

demo and some learning...

 

