# Subscribe to Users

Your attention is worth something, and the success of ad-driven social media
proves it.  But ad-driven social media is fundamentally abusive, since it intentionally
prevents you from focusing on the people you care about.  Instead, it
forces you to view ads you don't want to see, it prods you with
recommendations you didn't ask for, and it organizes your information in ways
that make it needlessly difficult to find what you want -- all in a
bid to keep you "engaged" on their site.  I find this experience very
anti-social.

Blockstack has the power to change this dynamic.  In Blockstack, users own
their identities and social media data *outside* of the
application, and application is simply one of many tools for
viewing your social data.  As a Blockstack user, I can directly list, read, and write,
and share any app data I create independently of the application, and I can
discover other users and their (public) data independently of the apps they use
as well.  This process feels more pro-social to me because it lets me
treat my data like it's my property --
*I* amd the owner and master of my data, *I* decide how to interact with it,
and *I* control who else gets to see it.

What does social media look like when users own their data?
I think there's space for a new type of social media platform --
one that doesn't involve relying on anti-social information gatekeepers.
Instead, you subscribe directly to the users you care about, and
where users control exactly what their followers get to see.

## From Siloes to Collections

When users own their own data in Blockstack, they can share access to it outside
of the application.  For example, [I can share a status update in a Twitter-like
app via an HTTP URL](https://gaia-gateway.com), and the data will be loaded from
my chosen [Gaia hub](https://github.com/blockstack/gaia) instead of an app
server.  My data is no longer ties up in a handful of data siloes.  Instead, it
all gets stored in a set of app-specific buckets in my Gaia hub, which can be
discovered via my Blockstack ID.  In other words, we've replaced data siloes
owned by a few corporations with data collections owned by the users who created
them.

What does social media look like when built around data collections?  It means
that following someone is like following a website.  You don't need to use
a particular app -- if you know the Blockstack ID of the person and have a way
to decode their data, you can just load up and view their files in the client
of your choice.  Your client is no longer coupled to the application that stored
the data, any more than a Web browser is coupled to the Web server that serves
up Web pages -- you can stream and mash up public photos from
[Travelstack](https://app.travelstack.club), blog posts from
[Graphite](https://app.graphitedocs.com), and tweets from
[Afari](https://afari.io) using nothing more than vanilla HTTP requests.

What does social media look like from the perspective of the person being
followed?  While it is true that anyone can pull files out of my Gaia hub, I can
control who gets to consume my data by encrypting it client-side before it gets
uploaded.  Since I can choose on a
per-datum basis who gets to read my data, I have fine-grained access controls
built into the system by default.  You may follow me, but unless I make data
public or I encrypt data for you specifically, you'll only see ciphertext.  This
is a win-win outcome -- you can follow me across apps using the client of your
choice, and I can control who gets to view my data without having to store it
and trust it with a third party.

## Humane Social Media

This person-to-person form of social media allows for a
marketplace of pro-social media app to emerge.  Anti-social media companies today
will no longer be able to get away with abusive client designs, since shipping abusive
features will cause them to lose marketshare to clients that *respect* the user.
They won't be able to force you to view ads or promoted content unless you want it
-- you'll just use a client that doesn't have ads.  They won't be able to do
shady things like selectively hide other users' posts or rearrange their order
either -- you'll just use a client that shows data as it is.  Opening up social
media clients to competition on who can view user data collections the best will
lead to much more humane social media experiences.

The social media client marketplace also helps content creators.  Blockstack's
technology ensures that as a content creator, I have unilateral control who
gets to see each piece of data I upload.  If my social media client does a bad 
job of exposing this power to me, I'll use a different one.  I don't have to
rely on the benevolence of the platform to keep myself safe.  Equally
importantly, social media platforms won't be making money off of my content --
if their client mines my data without my permission, I'll switch to one that
doesn't.

## Making This Real

People ask me how social media can be profitable if it can't mine your data for
ad placement.  My answer is two-fold:

* Content creators can and will find a way to monetize their content in this
  new pro-social world.  Since they control who gets to view their data, they would select
clients that encrypt content for consumption by paying customers only.  Content
creators get to cut out the middleman.

* Developers no longer have to bear the cost of hosting user data.  Since each
  user puts their data into their Gaia hub, a social media application in this
new world is simply a client-side Web app.  Once written and published, the
developer has no operational costs.  So, there's no financial need to build a data
panopticon like there is today.  Instead, developers make money on features, by developing
and selling better and better user experiences in the social media clients they
produce.

Blockstack's million-dollar bounty for a working decentralized social media platform is
meant to bootstrap these new forms of pro-social media.  If you're interested, I
encourage you to apply.
