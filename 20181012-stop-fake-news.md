# Stopping Fake News with Decentralized Shadowbans

The problem with fake news is that, due to its ability to flair up the emotions
of uncritical readers, it tends to spread a lot faster across the Internet than
real news.  This is made worse by the presence of bot armies that act as
automated provocateurs and agitators to maximize its spread.  Left unchecked,
fake news creates real problems, like outbreaks of preventable diseases or the
rise of fascism.

Unfortunately, the operators of the major social media systems have a perverse incentive to *tolerate*
and even *encourage* fake news since it not only drives engagement of these illiterate users,
but also the engagement of users who argue with them.  This is a natural outcome of 
the Faustian bargain of ad-driven revenue systems -- by valuing engagement at all costs,
social media amplifies the worst of humanity (but that's the
subject of another blog post).  The topic I want to focus on today is how to use
Blockstack to isolate fake news promoters in order to minimize the damage they
can cause.

## Direct Access To User Data

Blockstack makes it easy to build applications where users own their identities
and data -- they not only own their username and private keys independently of their applications, 
but they also control where their data is stored and who gets to see it.  One
byproduct of this design is that your username and data are
directly accessible outside of the application.  For example, one of my
usernames is `judecnelson.id`, and you can look up my data by crawling files for
applications listed in my profile by following [these
instructions](https://gaia-gateway.com).

This is advantageous to 3rd party developers, since it makes it very easy to make new
application clients.  Every user's app data is hosted outside of the app and 
accessible in the same standard way, so **a single app can have many competing
clients with no way to lock users in.**  This property is what we're going to
leverage to stop fake news.

## Cross-app Shadowbans

Shadowbanning is a moderation technique in social media whereby a user gets to
continue using the app and posting data, but no one else will see their posts.
It is more effective at deterring abusive users than outright blocking, because
the user will continue to waste their time posting data without knowing that
they're being ignored.  The only way to circumvent the moderation is to create
a new user acount, and there are several moderation techniques to make it hard
for abusive users to even figure out that they're being shadowbanned.

Because Blockstack apps are structured the way they are, it's trivial to
implement shadowbanning not only within apps, but *across the entire Blockstack network*.
This is because of the way Blockstack apps load data.  Whenever the client goes to read data,
it first looks up that user by username, finds out where they keep their data,
and then fetchs the data by path.
If you know that a particular user (let's say `eviltroll.id`) is malicious, you
simply make the username lookup step fail.  Since Blockstack IDs are used across applications,
you can shadowban abusive users out of all the applications you use -- whether the
application supports it or not.

This is somewhat straightforward to do.  Blockstack's Web SDK
implements a `getFile()` method for loading data.  You could simply monkey-patch
the method so it first checks the username against your personal block list, and
then cause the method to fail.  You might also have the method return a default
piece of data, like "`this content is hidden`".  Other options are possible,
like modifying your Blockstack Core node to not service requests for
your blacklisted usernames.

## Democratizing the Fight Against Fake News

Because of the way Blockstack is structured, one application can read data from
another application (provided it's been propertly encrypted).  This yields a way
for users to work together to identify and block bots across the Blockstack
network:  create a **decentralized shadowban app** that lets users create and
share shadowban lists.

Conceptually, the app is very simple:  it lets you load and store a list of
Blockstack IDs belonging to people who you never want to hear from again.  You
store this list to the shadowban app's Gaia bucket, and other applications that
are aware of this app's data can automatically load your shadowban list and
filter content out.  Moreover, you can view *other people's* shadowban lists via
this app and automatically merge them with yours.  So, if your friend shadowbans
someone abusive, that person will be shadowbanned for you too.

There are lots of ways you can tweak this app, like making shadowbans apply on a
per-app basis, apply for for a particular amount of time, and so on.  The gist
of it is that you can curate a list of known bots, trolls, and other
Internet creeps and share them with your friends, so neither you nor yours have
to deal with them.  Moreover, you won't have to wait for apps to adopt this
functionality -- if they're too slow at dealing with this problem,
you have the power to fork the Blockstack app and add it
yourself (or write your own).  If you go so far as to instrument your Blockstack
Core node or your browser, you don't even need to modify the app at all --
simply make the HTTP request to look up the name fail if it's blacklisted.

## What's Next?

This is a feature I'd very much like to see in the decentralized social
media apps I'll be using.  Given how bad centralized moderation platforms like
Reddit, Facebook, Twitter, and others are at dealing with fake news and other 
forms of abuse, users will inevitably need ways to deal with it themselves in
their decentralized replacements.  By decentralizing and democratizing
shadowbans, decentralized social media has the opportunity to
*empower* users to create a *better* user experience than they receive today
-- with no extra effort from the developers.
