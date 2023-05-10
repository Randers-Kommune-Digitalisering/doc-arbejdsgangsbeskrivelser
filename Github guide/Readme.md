## Guide til brugen af Github som projektstyringsværktøj i Digitaliseringsteamet.

I Digitaliseringsteamet bruger vi Github som projektstyringsværktøj, samt til overblik over vores leverancer. Det følgende er en trin-for-trin guide til at bruge vores digitaliserings- og leveranceoverblik.

## Begreber

### Inden for projektstyring eksisterer der en række begreber. Herunder er en sammenstilling af begreber fra projektstyrings verdenen med det man møder i GitHub Projects

#### Sag | Issue:

> PRINCE2 modellen har et begreb kaldet “Issue” som kan oversættes til “problem” eller “sag” på dansk. [Ifølge PRINCE2 kan en “Issue” være en anmodning om ændring, en afvigelse fra specifikationen eller et problem/bekymring_1_](https://prince2.wiki/management-products/issue-report/). Der er en procedure til at håndtere “Issues” i PRINCE2 modellen, som er defineret i Change Management Approach under Initieringsfasen og navnet på denne procedure er Issue and Change Control procedure[_1_](https://prince2.wiki/management-products/issue-report/).
> 
> Begrebet “Issue” fra PRINCE2 modellen kan relateres til “Issues” i GitHub.

#### Sagsregister | Repository

> I PRINCE2 modellen findes der et begreb kaldet “Issue Register” som kan oversættes til “Sagsregister” på dansk. “Issue Register” er en oversigt over alle formelle sager og opdateres regelmæssigt af projektlederen gennem hele projektet[_1_](https://prince2.wiki/management-products/issue-register/). Det kan forestilles som en regneark, hvor hver linje er en sag og der er kolonner for sagens ID, type, dato for oprettelse, oprettet af, beskrivelse, nuværende status og lukningsdato[_1_](https://prince2.wiki/management-products/issue-register/).
> 
> Issue Register begrebet i PRINCE2 modellen  kan relateres til “repositories” i GitHub i den forstand at det er et sted hvor man samler sager og det relaterede arbejde til sagerne.

#### Ændringsanmodning | Pull Request

> I PRINCE2 modellen findes der en proces kaldet “Change Control Approach” som kan oversættes til “Ændringskontroltilgang” på dansk. “Change Control Approach” er en retningslinje for, hvordan og af hvem projektets produkter vil blive kontrolleret og beskyttet under projektet. [Dette inkluderer både ændrings- og sagshåndtering_1_](https://prince2.wiki/management-products/change-control-approach/).
> 
> Så ja, der findes en proces i PRINCE2 modellen der kan relateres til “pull requests” i GitHub i den forstand at det er en metode til at håndtere ændringer og sager i projektet.

## Oprettelse af nyt projekt/proces i Digitaliseringsoverblikket

Alle henvendelser vedrørende Digitaliseringsteamet ydelser skal oprettes i Digitaliseringsoverblikket. Dette gøres på følgende måde:

1.  Tryk på 'add item' nederst i henvendelsesfanen.
2.  Indsæt navn på projekt. Det anbefales, at navnet på projektet matcher navnet i SBSYS eller Topdesk.
3.  Indsæt SBSYS sagsnummer i parentes efter projektnavn.
4.  Tilføj navn på den person, som varetager pågaven under 'Assigness'.
5.  Vælg status fra drop-down menuen under 'Status'.
6.  Indtast gerne en kommentar omkring, hvad status er.
7.  Hvis der er en opstarts- og afslutningsdato for projektet indtastes dette i felterne 'opstart' og 'afslutning'.
8.  Indtast navnet på bestilleren/rekvirenten af henvendelsen.

Efter at henvendelsen er oprettet skal selve opgaven laves om til et issue. Dette gøres ved:

1.  Tryk på navnet på opgaven du lige har oprettet.
2.  Nederst i højre hjørne trykker du på 'convert to issue'.
3.  I rullemenuen der kommer frem vælger du 'doc-arbejdsgangsbeskrivelser'.

Herefter kan du oprette en taskliste ved at trykke på ikonet, som illustrere en opgaveliste med et flueben. Der hvor der står "Add a draft title or issue reference here", kan du erstatte teskten med en opgave - eksempelvis 'kortlægning af arbejdsgang'. HVis du ønsker at tilføje flere opgaver trykker du blot på 'enter' på tastaturet. De af opgaverne på denne liste, som ender ud i leverancer, skal markeres som 'issues' og tilføjes en person, som er ansvarlig for det pågældende issue.

## Oprettelse af mappe til arbejdsgangsbeskrivelser

Ved henvendelser der drejer sig om procesautomatiseringer, skal der oprettes en mappe til dokumentation af arbejdsgangsbeskrivelser (procestegninger).  
Alle arbejdsgangsbeskrivelser skal dokumenteres i det repository, som hedder 'doc-arbejdsgangsbeskrivelser'.  
Fremgangsmåden for dette er følgende:

1.  Åben 'doc-arbejdsgangsbeskrivelser'.
2.  Tryk på 'Add file' og herefter 'create new file'.
3.  I feltet hvor der står: "Name your file" skriver du navnet på projektet og afslutter med skråstreg.
4.  I næste felt (der kommer frem efter du har indtastet filens navn) skriver du: "Readme.md".