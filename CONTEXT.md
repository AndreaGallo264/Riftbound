# Riftbound Collection Assistant

This context describes the game information and player-owned records used to manage a Riftbound collection and ask grounded questions about play.

## Language

**Card**:
A stable gameplay identity shared across its physical publications. It is distinct from a Printing and from any player-owned copy.

**Card revision**:
The official gameplay attributes and text effective for a Card during a stated period. A newer Card revision supersedes an older one without changing the Card's identity.

**Printing**:
A physical publication of a Card distinguished by release, collector number, or artwork. Language and finish belong to the individual Owned copy in the MVP.

**Card catalog**:
The shared reference set of known Cards and their published attributes. It is distinct from what any player owns.

**Collection**:
The single inventory of Owned copies maintained by one player. Quantities are derived by counting those copies rather than stored independently.

**Owned copy**:
One physical Card copy in a Collection, identified by its Printing and described by language, finish, physical condition, and an optional note.

**Deck**:
A named selection of Card identities and quantities, grouped into Deck sections for a Deck format. It may include unowned Cards and does not reserve or reference particular Owned copies.

**Deck format**:
The rules context under which a Deck's sections, composition, and legality are interpreted.

**Deck section**:
A format-defined grouping of Card entries within a Deck.

**Deck legality**:
The derived result of checking a Deck against its Deck format and the Current rules state. It is independent of whether the player owns the required Cards.

**Collection coverage**:
The derived comparison between the Card quantities required by one Deck and the Owned copies in its player's Collection. Missing Cards do not make a Deck illegal.

**Knowledge source**:
An identifiable publication from which a rule, clarification, Card fact, deck list, or metagame observation originates.

**Knowledge revision**:
An immutable representation of a Knowledge source as observed at a particular time, including its provenance and extracted claims. A later correction or source change creates another Knowledge revision.

**Knowledge publication**:
The audited approval that makes a Knowledge revision available to the Assistant. It can later be superseded or withdrawn without erasing its history.

**Official rules source**:
A current rules document, FAQ, patch note, erratum, legality notice, or event addendum published by Riot. Forum posts and community publications are not Official rules sources, regardless of their author's role or popularity.

**Current rules state**:
The rules effective now after applying the explicit precedence and supersession relationships among Official rules sources. Historical rules states are outside the MVP.

**Ruling**:
A rule interpretation or clarification contained in an Official rules source whose publication, authority, and current applicability can be inspected.

**Grounded answer**:
An Assistant response whose factual claims are supported by the Current rules state, the Card catalog, or the Beta tester's latest saved Collection and Deck data.

**Recommendation**:
Non-authoritative advice derived from stated evidence and context. It is distinct from a rule or other factual claim and may include Cards the player does not own.

**Metagame**:
Source-scoped evidence about competitive Decks within a particular environment. The MVP represents it through official observations, not through derived rankings or aggregate performance statistics.

**Competitive environment**:
The combination of time period, region, Deck format, legal Card pool, rules revision, and ban state in which competitive evidence was produced.

**Competitive reference deck**:
A Deck list published by Riot with an identifiable event and Competitive environment. It is evidence of participation or performance in that event, not proof of general popularity or future results.

**Beta tester**:
An invited player who maintains their own Collection, Decks, and Conversations and consults the Assistant. A Beta tester cannot access another tester's data or curate shared game knowledge.

**Admin**:
A product operator who manages beta access and shared game knowledge. An Admin may inspect Beta tester data for support, but cannot present private data as shared knowledge.

**Conversation**:
A persisted exchange between one Beta tester and the Assistant. It belongs to that tester, remains isolated from other testers, and is not a Knowledge source.

**Assistant**:
The conversational capability that answers using shared game knowledge and the current Beta tester's Collection and Decks. It may recommend changes but does not modify player-owned records.
