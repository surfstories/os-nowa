---
title: Connections
tier: 1
---

# Connections

What this system can actually reach, and how. One row per tool or service the user has connected.

Empty is the correct starting state. OS_Nowa ships with nothing connected; the user adds a row when
they connect something, and the row is a note to future sessions, not a configuration file — nothing
reads it to establish a connection.

| What | How it connects | Can do | Added |
|---|---|---|---|

**Never put a password, an API key or a token in this file.** A row records that a connection
exists and what it is good for. It never records how to authenticate.

**A registry that understates what the system can do is worse than no registry**, because every
future session then works from a shrunken map. If you discover a capability that has no row, add it.
If a row turns out to be wrong, correct it — do not append a second row saying the opposite.

**Onboarding does not fill this file, and that is not an oversight.** OS_Nowa ships with nothing
connected, so an empty table is the honest starting state. A health check should not report this file
as unfinished while the table is empty.
