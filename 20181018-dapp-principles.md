# What's in a Dapp?

There are as many definitions for a decentralized app as there are dapp
developers.  I don't expect this one will be the canonical definition, but I'm
writing it down anyway since it serves as my "north star" as I work on the
Blockstack platform.

An application can be considered a dapp if it adheres to the following three principles.

## Principle 1: Users Own Their Data

The most important property of a dapp is that the user owns their application
data *outside of* the application.  The application is not the authoritative
source of user data, nor does it host the primary replica.  An application can
only be considered decentralized if the *user* gets to decide where the primary
replicas of their data get hosted, and if the *user* can non-repudiably prove
that they created it.

Blockstack applications all have this property if they use Gaia, since each user
gets to choose on an app-by-app basis which Gaia hub serves their app-specific
data.  Users may sign and/or encrypt their data in Gaia end-to-end to prove
ownership and restrict access.

## Principle 2: Users Own Their Identities

Users must be distinguishable within the dapp by a unique identifiers, such that
each identifier is solely administrated by the user.  The dapp cannot mask or
take away the user's identifier, and the user must be able to bind their
identifier to the data they create.

Blockstack applications have this property because Blockstack assigns each user
one or more Blockstack IDs, which are owned by a private key under the user's
control.  Blockstack cannot hide Blockstack IDs since they are replicated to all
peers via a blockchain.  Blockstack IDs each have a public key assigned to them
via the blockchain records that encode their operational history, thereby
allowing users to bind data to their Blockstack IDs through cryptographic
signatures.

## Principle 3: Users Have Free Choice of Clients

It's not enough that the user owns their identity and data -- the user needs to
also be able to choose which programs they use to interact with them and
administer them.  In the limit, the user needs to have the freedom to write
their own client.  An application cannot be considered a dapp unless it
allows users to interact with their identities and data such that the user can
later do so via a different dapp.

This principle is distinct from the first two because there can exist
applications that have the first two principles but not this one.  For example,
a Web app can allow users to store their data to their server of choice and can
allow users to sign in with open authentication protocols like OpenID, but can
also encrypt their data in-transit between their client and chosen storage
provider.  Unless the app divulges the key to the user, then the user cannot
have free choice of clients -- they can only use clients that the app's servers
choose to interact with.

Existing Blockstack applications have this property today simply because they
don't have any irreplaceable server-side logic.  Blockstack's APIs and SDKs make
it easy to build applications that adhere to this principle.

## Non-Principles

While there are many definitions of dapps, I think it's fair to say that
there are some things that often get attributed to dapps that are
actually irrelevant.  These non-principles speak to the implementation of dapps
instead of their overall design goals.  Chief among them, they are:

### Non-Principle 1: Dapps Have Smart Contracts

Decentralized apps pre-date blockchains and smart contracts,
and even today there are popular dapps
that do not need them.  Examples include pre-Microsoft Skype (which was
peer-topeer), Mastadon, IRC, and email.  All Blockstack dapps do not use
smart contracts at all.

Another word for "smart contract" is "replicated state machine."  Some dapps
need each peer to execute the same sequence of operations in order to fulfill
their business needs (in which case a smart contract would be appropriate),
but many do not.

### Non-Principle 2: Dapps Have Tokens and/or Non-Fungible Assets

Same as non-principle 1, dapps pre-date these things.  While having a
crypto token or asset can help incentivise dapp deployment and usage, they
are not strictly necessary for their operation.

### Non-Principle 3: Dapps Use A Blockchain

Blockchains are a new tool for dapp developers to help coordinate peers, but
they are just that -- a tool.  Sometimes they're the right tool for the job, and
sometimes they are not.

## Dapps Serve the User

It is important to notice that these principles are centered around preserving
the autonomy of users, instead of adhering to a particular network topology or
architecture.  This is because I fundamentally believe that the role of dapps
is to serve the user, and to do so my principles should
prevent developers from profiting from either (a) building
abusive features into dapps like ad networks, or (b)
neglecting users by failing to build vital safety features like shadowbans.

This isn't to say that dapps can't be profitable
Dapps can still make money for their developers,
such as by offering content subscriptions or paid-for
add-ons.  However, developers cannot profit from abusive features or neglectful
designs -- since the user owns their identity and data and has free choice of clients, the
user can simply stop or avoid using bad dapps with near-zero switching cost.
