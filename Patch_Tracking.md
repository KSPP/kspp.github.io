Patch Tracking
==============

# Overview

The primary place where [KSPP](/) patches are tracked is through our
[patchwork instance](https://patchwork.kernel.org/project/linux-hardening/list/).
This helps collect Reviewed-by, Acked-by, Tested-by, etc, tags in a
single place to see status.

# Process

The overview list shows patches that need some kind of work to move
through the tracking process:

  - [Action
    Needed](https://patchwork.kernel.org/project/linux-hardening/list/):
    Needs work from someone from the linux-hardening patchwork team.

The specific "state machine" we use follows this path:

  - [New](https://patchwork.kernel.org/project/linux-hardening/list/?series=&submitter=&state=1&q=&archive=&delegate=):
    No activity yet.
      - Move to "Under Review" (possibly with a delegate assigned to do
        the review).
      - Move to "Superseded" if a newer version of the same patch has
        been sent (the patchwork-bot usually does this automatically).
  - [Under
    Review](https://patchwork.kernel.org/project/linux-hardening/list/?series=&submitter=&state=2&q=&archive=&delegate=):
    Reviewers need to give feedback on the patch.
      - Move to "Changes Requested" if a new version of the patch is
        needed after review feedback.
      - Move to "Needs ACK" if another subsystem is expected to take the
        patch into their tree.
      - Move to "Handled Elsewhere" if a non-linux-hardening tree says
        they are applying the patch.
      - Move to "Queued" if a linux-hardening tree applies the patch.
      - Move to "Superseded" if a newer version of the same patch has
        been sent (the patchwork-bot usually does this automatically).
      - Move to "In Next" if the patch appears in linux-next (the
        patchwork-bot usually does this automatically).
      - In rare cases, a patch can be moved to "Rejected", but that is
        uncommon, as normally review feedback is expected to be acted
        on.
  - [Queued](https://patchwork.kernel.org/project/linux-hardening/list/?series=&submitter=&state=13&q=&archive=&delegate=):
    Going via a linux-hardening tree, but not yet in linux-next.
      - Move to "In Next" once a patch appears in linux-next (the
        patchwork-bot usually does this automatically).
  - [Needs
    ACK](https://patchwork.kernel.org/project/linux-hardening/list/?series=&submitter=&state=15&q=&archive=&delegate=):
    Going via another tree, but not yet reviewed by maintainer.
      - Move to "Handled Elsewhere" once other tree maintainer says they
        are applying the patch.
      - Move to "In Next" once a patch appears in linux-next (the
        patchwork-bot usually does this automatically).
  - [Handled
    Elsewhere](https://patchwork.kernel.org/project/linux-hardening/list/?series=&submitter=&state=17&q=&archive=&delegate=):
    Going via another tree, but not yet in linux-next.
      - Move to "In Next" once a patch appears in linux-next (the
        patchwork-bot usually does this automatically).
  - [In
    Next](https://patchwork.kernel.org/project/linux-hardening/list/?series=&submitter=&state=19&q=&archive=&delegate=):
    In linux-next, but not yet in Linus's tree.
      - Move to "Mainlined" once a patch appears in Linus's tree (the
        patchwork-bot usually does this automatically).
  - [Mainlined](https://patchwork.kernel.org/project/linux-hardening/list/?series=&submitter=&state=11&q=&archive=&delegate=):
    Done\! In Linus's tree.
