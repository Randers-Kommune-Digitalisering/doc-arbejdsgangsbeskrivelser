# Rækkebaseret sikkerhed SD

Rækkebaseret sikkerhed styrer hvem der har adgang til at se personfølsomt fravær i BI-rapporter.
Rettighederne hentes fra Silkeborgdata. Brugere med rollerne ”leder_stedfortræder m/u godkendelse” har mulighed for at se fravær i SD, og arver derfor disse rettigheder over i BI.

### Fil fra SD
SD afleverer dagligt (kl. 10.45) CSV-filen ”Brugeradministration-da” på frejaserver
Filen indeholder oplysningerne:
•	Lokalt brugernavn: 
•	AfdelingsID: 
•	Navn
•	Email
•	Rolle: Leder_stedf_godkendelse eller Leder_stedf_uden_godk
•	Niveau 09
•	Niveau 08
•	Niveau 05

Brugere med adgang til flere afdelinger vil have en række for hver afdeling. 
Udtrækket fra SD skal oversættes til nedenstående: 

### Fil til KMD
Filen SKAL kun indeholde 3 kolonner med disse overskrifter i nævnte rækkefølge: 
1.	BrugerID 
2.	Institution
3.	AfdelingsID
Filen SKAL navngives ”SDbrugerAfg_ÅÅÅÅMMDD”, hvor år, måned og dato navngives ud fra dags dato. 
Filen SKAL gemmes som CSV UTF-8 fil, hvilket kun kan gøres på pc med office 365. 
 
Filen SKAL gemmes på frejaserver. 
Filen forsvinder fra serveren, når dataloadet er kørt. Der kan derfor med fordel gemmes en kopi i en anden mappe til dokumentation og senere brug. 
Opdateringsfrekvens
Filen loades hver nat, og de nye roller træder i kraft om morgenen. 
Hvis ikke der loades en ny fil, er den foregående fil gældende. 
Dataadgang – indhold i kolonner: 
1.	BrugerID 
•	6-cifret DQ-nummer 
•	SKAL starte med DQ. Må ikke være APKD-numre. 
2.	Institution
•	2-cifret institutionskode
•	RG for Randers Kommune. Selvejende institutioner har sin egen institutionskode. 
3.	AfdelingsID
•	2-4 cifret afdelingskode
•	Kan godt være en overliggende knude, fx ÆLD for hele omsorg eller RG for hele Randers Kommune.
”Se alt” rolle: her tastes 9R i AfdelingsID, mens Institution er blank. Bruges kun til udviklerne. 
Hvis en bruger skal have flere afdelingsid’er, laves flere linjer 
 

Hvis en bruger, har brug for alle underliggende afdelingsid’er til en selvejende institution, skrives blot institutionskoden og afdelingsID er blank: 
 

Den loadede dataadgang i BI kan tjekkes i universet ”SilkeborgData - Autorisationer 90” ud fra DQ-nummer. 
Fremgangsmåde for rens og berigelse af SD fil til KMD
Omsæt alle brugerid’er til DQ-numre, formater afdeling og institution, reducer arket til 3 kolonner og gemt på 840 
Hver morgen kl. 10.45 up-loader SD listen ”Brugeradministration-da” på Frejaserver. Dagens fil erstatter tidligere fil.
Kopier ”Brugeradministration-da” og sæt den ind, hvor du vil arbejde med den – fx 
F:\BUDGET FÆLLES\BI\BI\Rækkebaseretsikkerhed – indlæsningsark

### Manuel arbejdsgang i Microsoft Excel
Åbn filen – marker kolonne A – vælg fanen ”Data” – klik ”Tekst til kolonner” – næste – flueben i semikolon – Udfør
Indsæt ny kolonne B – navngiv ”BrugerID” i øverste række
Marker række 1 – vælg fanen ”Data” klik ”Filtrer”
Filtrer kolonne A, så det kun er DQ numre, der fremgår (fjern flueben i Markér Alt - søg DQ – klik ok)
Stil dig kolonne B, sæt B = værdier i kolonne A [B1=A1] hele vejen ned (gøres let ved at klikke på lille grønne plus i nederste højre hjørne af cellemarkeringen)
Fjern filter fra Kolonne A (flueben i marker alt)
Nu skal der laves L-opslag. 
Find arket ”Omsætning til dq-numre” på \\freja\FraSD\840
Stil dig på fanen ”DQ-numre” højreklik –  vælg ”Flyt eller kopiér ark” – vælg ”Brugeradministration-da.csv”, som destination - flueben i ”opret en kopi” – OK
Sæt filter på kolonne B ”Tomme” (fjern flueben i Markér Alt og sæt flueben i ”Tomme”)
Stil dig i kolonne B 
=LOPSLAG(	=LOPSLAG(	
Marker celle A2	=LOPSLAG(A2	
Lås cellen tryk F4 3 gange	=LOPSLAG($A2	
;	=LOPSLAG($A2;	
Vælg fane DQ-numre	=LOPSLAG($A2;'DQ-numre'!	
Marker kolonne A-C	=LOPSLAG($A2;'DQ-numre'!A:C	
Lås - Tryk F4 1 gang	=LOPSLAG($A2;'DQ-numre'!$A:$C	
;	=LOPSLAG($A2;'DQ-numre'!$A:$C;	
2	=LOPSLAG($A2;'DQ-numre'!$A:$C;2	
;	=LOPSLAG($A2;'DQ-numre'!$A:$C;2;	
Falsk
	=LOPSLAG($A2;'DQ-numre'!$A:$C;2;FALSK	
)	=LOPSLAG($A2;'DQ-numre'!$A:$C;2;FALSK)	

Formlen kopieres hele vejen ned ved at klikke på det lille grønne kryds i nederste højre hjørne af cellen. VÆR OBS PÅ AT DEN KOPIERES HELE VEJEN NED 
Tjek filter i kolonne B for ’tomme’ – der må ikke være nogen tomme!  
(OBS: apkd025 og apkd158 har ikke et DQ-nummer -  de kan bare slettes)  
Kolonne B laves til tal (Kopier og indsæt special - Værdier)
Slet kolonne A
Slet fane med DQ-numre, da arket der indlæses hos KMD kun må have én fane
Fjern ’lukket enhed’ -> filtrer AfdelingsID - kolonne B ’Lukket enhed’. Marker rækker og slet
Fjerne filter
Nu skal kolonne B, AfdelingsID, renses, således at (RG_B1U) opdeles i to kolonner
Indsæt nye kolonner C+D
Navngiv C: Institution
Navngiv D: AfdelingID
Find ”Ulriks formel” i regnearket på \\freja\FraSD\840
Kopier formel i kolonne C (Ulriks ark) og indsæt i kolonne C (dit ark) 
Kopier formel i kolonne D (Ulriks ark) og indsæt i kolonne D (dit ark) 
Kopier værdier hele vejen ned
Filtrer på fejl i værdierne via filter #VÆRDI!)
Gå ind i formellinjen og erstat ”_” med ”)”. Kopier ned for alle rækkerne. 
Slet #VÆRDI! I kolonne D, så de bliver blanke
Fjern filter i kolonne C
Marker hele arket og indsæt som speciel – værdier 
¬Slet kolonne B, og E-J så du kun har BrugerID, Institution og AfdelingID tilbage
Tilføj personer, der skal have 9R-rollen (udviklere og særlige udvalgte personer) – se fil i frejamappen. Der kan også trækkes en ny opdateret liste via Opus og ”Brugere tildelt udvalgte roller” eller via filen ”Licens_DQ_navn_forvalting” (egne data arket til brugerstyrings rapport). Husk dog at tilføje personer, som ikke er udviklere. 
Indsæt deres DQ-nr nederst i kolonne A, kolonne B er tom, Skriv 9R i kolonne C 
Gem excelarket som en CSV.UTF-8 fil, navngiv: SDbrugerAfg_ååååmmdd
Tag en kopi af arket og læg kopien i mappen på Freja: \FraSD\840

