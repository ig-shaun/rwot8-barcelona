# Journalistic use-cases for SSI:  signatures, verified claims, and canonical-text registries

## DrafT: RWoT 8 Topic Paper

by Juan Caballero & Jefferson Sofarelli (Berlin, DE)

# Abstract

The goal of this paper is to compare notes with the SSI technical community and hopefully to model some possible solutions for middleware systems and/or SSI-powered widgets for CMS systems.  Some of these could, we hope, be built soon on current platforms, to start benefitting journalists, factcheckers, and publics as soon as possible.  Others, at industry-wide, national-scale, or semi-global scale, could not be built as quickly, but planning them in dialogue with the broader community is also a priority for us. 

## Background

This paper originates from a few separate working-groups with journalists to identify pain points and to imagine possible use-cases for SSI, drawing in particular from the experiences of developing-world journalists and editors battling misinformation, misattribution, and other identity issues in the press.  The "

[]: https://motherboard.vice.com/en_us/article/pakxby/silicon-valley-is-inserting-its-biases-into-nearly-every-technology-we-use	"first world bias"

" of tech platforms and social media has been discussed at length, so we will take it for granted, but would add that the journalistic pain points around misattribution, misinformation, and privacy are felt much more acutely in developing nations with potential regime-changes imminent and more fraught relations between journalists and government, and in many case the journalists working in these contexts prove themselves to be early-adopters of privacy tech and publishing tools compared to their developed-world analogues.

One basic problem exacerbated by social-media manipulation and other misinformation campaigns is misattribution-- from doctored twitter screengrabs, to altered soundbytes to citations invented wholesale, this is a growing nuisance in the election cycles of the developing world.  Many journalists have expressed a desire to extend the "verification" scheme of a closed platform (Twitter being the most common example) to something more cross-platform, such that with some degree of certainty whole articles could be cryptographically signed by a keyholder who has also signed public profiles like a twitter page, a facebook page, etc.  Given that many news platforms are currently upgrading and expanding the technical capabilities of their CMS systems and backends, especially in countries battling misinformation proactively like Brasil and India, the timing would seem to be urgent.

Our long-term proposal is to design an SSI-platform-agnostic DID widget or middle-ware system for CMSs such that at the time of committing a canonical version of a published piece on a given publication's CMS, that canonical version could be hashed and signed, with signature and hash being stored in an immutable, external record against which the signature could later be checked (i.e., making a verifiable claim of authorship linking the article's original published form to a DID controlled by its author).  We have broken up the building blocks to be discussed at RWoT as:

## 1.) SSI capabilities for binding DIDs to articles in journalistic CMSs

A simple first step would simply be a way of attaching a DID signature both to each author's user profile in a CMS (assuming industry-standard, i.e. not very complex CMS access control model), and also to their individual signed works.  We were assuming we would work first with a a few specific proprietary CMSs, and eventually consider an exportable/agnostic widget across multiple CMS systems.



A) For the sake of prototyping and division of labor/code control, would be to have an extra field in the CMS system in the profile for the author to manually add their DID as a string. This manual-DID capacity, perhaps obsoleted later, would circumvent the need to 'Login with DID button' in a working prototype-- what's more, only a CMS admin, not each individual author, would need this direct access, and could be done once per account.  This presents its own issues (particularly if the DID needs to be alterable/updatable in the case of rotation/recovery), but for the sake of prototyping and early adoption, implementors would likely prefer they not have to execute ANY external code in the backend. This would thus allow authors to confirm/sign individual pieces/articles afterwards against the DID thus saved in the system. In addition, the hash / finterprint of that article could still be stored *externally* (see below, component 3), so a *later* verfication is still possible. 

B) From a UX point of view, it's worth explicitly stating that regardless of whether (C) DID is presented at login and/or (A) DID is stored manually or programmatically alongside other account credentials in the access control model of the CMS, this session-level and account-level signature is NOT enough for the journalistic use cases we've studied-- there needs to be a unique signature for EACH ARTICLE in the CMS.  (Perhaps even for each version of the article depending on the costs and structure of the CMS and of component #3!).  The vulnerabilities of an open session (cookie hijacks, or even just physical control of the computer while the session is open) make a unique DID authentication at time of article commitment essential. By analogy to amazon (which requires password confirmation/re-entry before purchase), DID-pegged publishing should reaffirm/authenticate at time of finalizing any publication.  Cell-phone-based SSI authentication (say, by QRCode) is our working draft thesis, although we want all the tires kicked and all the alternatives discussed if there's time!

C) One SSI capability could be a "Sign in with SSI button" alongside other at point of CMS author login.  We would like to hear from the SSI community if there are interoperable standards emerging of the kind proposed [publically](https://hackernoon.com/launch-a-decentralized-identity-application-using-the-developer-friendly-uport-react-truffle-box-95d1ddf176ea) by uPort for various major CMS systems commonly used in journalism, such that a DID holder could verify their identity and account across publications.  This is more important to UX and uptake of a finished solution than to the actual verification needs the broader system could meet, but there are also use-cases where a publication might want to attest that an author uploaded their own work directly/themselves, or when.  For these reasons, 

## 2.) SSI for casual journalists and occasional contributors

Similarly, many controversial and influential pieces of journalism are not written by professional journalists, but by experts and technicians from various other fields.  For these kinds of authors only occasionally publishing open letters, "op-ed"s, and other public statements, it is sometimes necessary to be able to make verifiable claims about education, expertise, and employment, rather than linking back to a short trail of publications.  For this reason, our group would like to check in with the Verified Claims for Education working group and the representatives of government on the status of various registries that soon be online for these purposes.  Anything we design and pilot would need to be maximally interoperable with emerging Verified Claims (#VC) standards to be useful in this corner case.  The idea is to imagine a minimal meta-ID system or middleware, along the model of "Twitter verification," whether that be powered by DID #VCs or otherwise. 

## 3.) An SSI-powered immutable publication registry

Immutable registries of articles (technically, of canonical versions of article, with later corrections stored elsewhere) are increasingly becoming popular projects among journalists for many reasons.  The Ethereum-based startup Civic (and its subsidiary/partner, Popula) has been piloting a program to actually encode all of its published pieces immutably in the ethereum chain itself, while other publications have discussed other immutable and/or decentralized alternatives to traditional, hosted RSS or XML.  An assessment of technical options and costs at different scales will probably be beyond the scale of a single RWoT meeting, but sketching out the parameters for such an assessment in consultation with the community might be a reasonable goal for this RWoT.

## Other ramifications

We are not yet at the stage of actively researching GDPR or eIDAS ramifications, but we are hoping to learn more about those from other, further along projects and welcome any input.
