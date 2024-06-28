# Governance of the Biotite project and related projects

This document describes the decision-making processes for all repositories within the
[`biotite-dev`](https://github.com/biotite-dev) organization, which will be called
'*the project*' in short throughout the document.

## Overview

The purpose of project governance is to formalize decision-making.
This is especially necessary in cases of conflicting opinions.
On the other side, the ordinary development work should ideally not be impeded by
formal decision-making processes.
Thus, the project employs a lazy-consensus based meritocracy:
In short, developers who have earned merit are able to contribute changes without
requiring consent - unless someone is objecting.

## Roles

### User

A user is a person that makes use of the project.
They also may propose changes or report bugs.
A change may comprise e.g. a new feature, a fixed bug or improvements to the
documentation.

### Contributor

A contributor is a person, who has already introduced at least one change to the
project.
A contributor is eligible to be elected into the project board.

### Board member

The project board [makes decisions](#lazy-consensus) on whether changes to the project
are accepted, rejected, or require modification.
Hence, they are responsible for the moderation of the project development.
The board may comprise up to ten persons, called board members.

A contributor, who is not part of the project board yet, may be nominated by a board
member for election into the project board.
Nominees should be chosen based on the quality and extent of their previous
contributions to the project.
If the nominee successfully passes a [majority vote](#lazy-consensus), they become
a board member.
In case of misbehavior or long-term inactivity of a board member, the board may decide
to dismiss that board member.
This again requires a successful majority vote among the board members.

### Maintainer

The project has a maximum of two maintainers.
If the project currently has less than two maintainers, the project board should elect
a willing board member to become maintainer.
A nominated board member must pass a majority vote among the board members to become
a maintainer.

Each maintainer has a veto right on any decision made by the project board.
A maintainer has also the sole privilege to create a new software release and update
the documentation websites.
A maintainer cannot be dismissed by the project board, but still may decide to resign.
Furthermore, maintainers also have the board member role.
Hence, all points from the ['Board member' section](#board-member) apply to maintainers
as well.

## Decisions

### Lazy consensus

Changes to the project are decided based on lazy consensus:
Any board member may propose a change and the project automatically accepts the
decision after a retention time of 48 hours, if no other board member declares their
objection.

If an objection was declared, the board members should try to find a consensus on the
matter.
If a consensus is found, the change is accepted again after 48 hours, if no further
objection is declared in that time.
If no consensus is found, the proposing board member may invoke a majority vote among
the board members.
In the following two weeks each board member may vote for (*pro*) or against (*contra*)
the proposed change.
If a board member does not vote within these two weeks, their consent is assumed and
the vote is counted as *pro*.
If the *pro* votes outnumber the *contra* votes, the vote passes and the proposed change
is accepted.
A maintainer may use their veto right to reject a change independent of the vote
results.
In case of rejection the proposing board member may modify the proposed change and
invoke a majority vote again.

If a change was accepted without a vote, any board member may declare an objection
within two weeks after its acceptance.
In this case a majority vote is invoked about this change as described above, as if the
change has never been accepted.
If the majority vote does **not** pass, the change is reverted.
As reverting a previously accepted change means lost effort for the proposing board
member, declaring an objection within the retention time is strongly preferred.

A change may also be proposed by a user or contributor.
In this case the retention time starts after the proposal.
However, at least one board member must express their approval, for the change to be
accepted.

### Strict majority vote

There are exceptions to the lazy consensus:

  - changes to the governance document
  - election or dismissal of a board member
  - election of a maintainer

For those decisions the board members start a majority vote for two weeks.
Absence is neither counted as *pro* or *contra*.
A maintainer can use their veto right to reject a change or election.

## Implementation

This section describes how the processes depicted above are technically implemented.

### Collaboration and communication

The central place for collaboration is the
[`biotite-dev`](https://github.com/biotite-dev) organization.
Communication about certain topics is carried out in *issues*, *pull requests* and
*discussions* in the respective repository.
Changes are proposed and accepted via pull requests.

### List of board members and maintainers

The members of the project board and the maintainers are identified by their
[roles](https://github.com/orgs/biotite-dev/people) the `biotite-dev` organization.

- Board members get the *Member* role.
- Maintainers get the *Owner* role.

Elected or dismissed persons are added or removed accordingly.

### Voting

Voting is conducted via reviews in pull requests.
The proposing board member can invoke a majority vote by asking for it in a comment.
Leaving a review with '*Approve*' means *pro*, while '*Request changes*' means *contra*.

### Election, dismissals and resignation

Board member and maintainer elections and board member dismissal votes are held in
pull requests in the [`biotite-dev/.github`](https://github.com/biotite-dev/.github)
repository and may be invoked by any board member.
Board members and maintainers may also announce resignation from their role via an issue
in that repository.

### Accepting code changes

A code change is proposed by opening a pull request.
It is accepted by merging it.
The merge conditions are explained in ['*Lazy consensus*'](#lazy-consensus).

An exception to the retention time condition are critical cases that require immediate
changes followed by a short-term software release.
These cases include

  - security vulnerabilities,
  - bugs that make large parts of the software unusable or
  - bugs that lead to wrong/corrupted results that cannot be obviously identified by the
    user.

The two-week rejection period after the merge remains untouched.

### Software releases

Maintainers have the task of releasing new versions of *Biotite* and its extension
packages along with its documentation.
To fulfill these responsibilities, all maintainers must have full access to

- the GitHub repositories under [`biotite-dev`](https://github.com/biotite-dev),
- the [*Zotero* library](https://www.zotero.org/groups/5533833/biotite_documentation),
- the package in [*PyPI*](https://pypi.org/project/biotite/),
- the [`conda-forge` feedstocks](https://github.com/conda-forge/) and
- ~the [documentation website domain](https://www.biotite-python.org/)~
  (currently not possible as *.org* domains require a single owner).
