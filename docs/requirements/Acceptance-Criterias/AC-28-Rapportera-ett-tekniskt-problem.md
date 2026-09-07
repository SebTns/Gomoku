### AC-28-01: Rapportera ett tekniskt problem

**Relaterade krav:** FR-28.1–FR-28.7

**Given** att spelaren befinner sig i spelet  
**And** spelaren har upptäckt ett tekniskt problem  

**When** spelaren öppnar funktionen "Rapportera problem"  
**And** beskriver problemet  
**And** skickar rapporten  

**Then** ska systemet kontrollera att en beskrivning finns  
**And** registrera problemrapporten  
**And** tilldela rapporten ett unikt rapport-ID  
**And** visa en bekräftelse på att rapporten har registrerats

### AC-28-02: Problemrapporten kan inte registreras

**Relaterade krav:** FR-28.8, FR-28.9

**Given** att spelaren har fyllt i en beskrivning av ett tekniskt problem

**When** spelaren försöker skicka rapporten
**And** rapporten inte kan registreras

**Then** ska systemet informera spelaren om att rapporten inte har registrerats
**And** låta spelaren försöka skicka rapporten igen.
