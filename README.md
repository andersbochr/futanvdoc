# FUT Infrastruktur

Dette dokument beskriver FUT Infrastrukturen, som indeholder applikations- og teknologiservices til udviklere af telemedicinske løsninger i Danmark. Dokumentet henvender sig til forretningsanalytikere, arkitekter og udviklere, der ønsker en introduktion til, hvad FUT Infrastrukturen indeholder. Den har særligt fokus på, hvordan telemedicinske løsninger (kaldet anvenderløsninger) bygges.

Dokumentet introducerer først de rammer, FUT Infrastrukturen er bygget indenfor, hvorefter den overordnede forretningsarkitektur præsenteres. På baggrund heraf beskrives applikationsarkitekturen for FUT Infrastrukturen og det præciseres hvad en anvenderløsning er, og hvad den skal indeholde. Heraf vil det fremgå, at FUT Infrastrukturen understøtter en række processer (forretningsvendte såvel som tekniske), som anvenderløsninger skal indplacere sig i og tilbyde konkrete, brugervendte løsninger for. Disse processer er centreret omkring borgeres forløb, som består af veldefinerede aktiviteter og opfølgning med henblik på at nå eller vedholde et mål. Det er netop anvenderløsningens ansvar at understøtte brugeroplevelsen for såvel borgere som sundhedspersonale i de processer, der knytter sig til disse forløb. Dokumentet fortsætter ved at beskrive den overordnede brug af den proces- og datamodel, som FUT Infrastrukturen tilbyder anvenderløsninger. I disse beskrivelser angives referencer til mere detaljerede og instruerende beskrivelser.

# Rammesætning

I dette afsnit introduceres formålet med FUT Infrastrukturen samt de principper og politikker forretnings- og applikationsarkitekturen er bygget omkring.

## Formål

FUT Infrastrukturens formål er at understøtte hjemmebehandling med borgeren i centrum på tværs af sektorer, specifikt udmøntet gennem:

* samarbejde om patienten gennem teams, der går på tværs af regioner, kommuner og primærsektoren

* fælles udvikling og vedligehold af funktionalitet, der understøtter anvenderløsninger indenfor monitorering, forebyggelse og behandling

* etablering af best practices for udvikling og drift af nye anvenderløsninger

* sikker adgang baseret på eksplicitte adgange til data (f.eks. borgers egne data eller sundhedspersonales adgang via teams)

* strømlining af mulighederne for at udvinde yderligere værdi af data via ensartet og kvalitetssikret proces- og datamodel

* fælles deployment, drift og overvågning på standardiseret teknologi-infrastruktur (herunder hosting af anvenderløsninger)

## Principper

* For at understøtte formålet følges nedenstående principper:

* Borgeren i Centrum: Borgerens behov er i centrum for alle beslutninger og funktioner

* Sammenhængende Sundhedsforløb: Borgerne oplever et sammenhængende forløb på tværs af sektorer og sundhedsfaglige teams

* Datadrevet Beslutningstagning: Beslutninger skal baseres på data og evidens for at sikre kvalitet og effektivitet i behandlingen

* Sikkerhed og Privatliv: Beskyttelse af borgernes data skal følge gældende lovgivning

* Fleksibilitet og Skalerbarhed: Platformen skal være fleksibel og skalerbar for at kunne tilpasse sig fremtidige behov og teknologiske fremskridt

* Anvendelse af eksisterende Offentlige Data: Anvendelse af nationale og internationale standarder for offentlige data for at sikre konsistens, kvalitet og interoperabilitet. Dette inkluderer referencedata (f.eks. klassifikationer og terminologier), masterdata (f.eks. organisationer) og snitflader (f.eks. medcom)

* Åbenhed og Interoperabilitet: Understøtte gængse teknologier for anvenderløsninger og herved en flerleverandørstrategi for anvenderløsninger

## Politikker

Principperne udmøntes konkret i de nedenstående politikker, som udgør de mest konkrete input til realiseringen af FUT-Infrastrukturen:

* Adgangskontrol og Autorisation: Varetage rollebaseret adgangskontrol for at sikre, at kun autoriserede sundhedsfaglige personer har adgang til relevante data

* Datastyring og Kvalitet: Sikre klare retningslinjer for datastyring, herunder datakvalitet, dataintegritet og databeskyttelse

* Sikkerhedspolitik: Vedligeholde en sikkerhedspolitik, der dækker alle aspekter af platformens drift

* Compliance: Sikre, at platformen overholder alle relevante love og reguleringer, herunder GDPR og sundhedslovgivning

* Brugerinvolvering og Feedback: Aktivt inddrage anvenderløsningerne i udviklingen og forbedringen af platformen gennem regelmæssig feedback og brugerundersøgelser

* Kontinuerlig Forbedring: Implementere en politik for kontinuerlig forbedring, hvor infrastrukturen løbende evalueres og opdateres baseret på brugerfeedback og teknologiske fremskridt

* Standardisering i forhold til Offentlige Data: Infrastrukturen skal de godkendte standarder fra relevante myndigheder. Dette inkluderer datastandarder, snitfladestandarder, terminologier og klassifikationer.

# Begreber

Af nedenstående tabel fremgår de mest anvendte begreber i FUT Infrastrukturen.

| Begreb | Beskrivelse | Forkortelse | Kilde |
| --- | --- | --- | --- |
| FUT Infrastruktur | Den samlede tekniske løsning, der tilbyder services til anvenderløsninger | FUT-I | FUT-S |
| FUT Systemforvaltning |   | FUT-S | FUT-S |
| Anvenderløsning | En borger og/eller klinikerrettet applikation, der bygger på FUT-I |   | FUT-S |
| FHIR | En standard for modellering og anvendelse af sundhedsdata | FHIR |   |
| Kubernetes | En moderne løsning for drift af IT Systemer | K8S, k8s |   |
| Borger | En person, der er bosat i Danmark og kan være i et telemedicinsk forløb |   |   |
| Person | En person fra det centrale personregister |   |   |
| Patient | En person, der omtales i behandlingsmæssig sammenhæng |   |   |
| Måledata | Resultatet af en aktivitet, typisk efter borger har udført den. F.eks. Blodtryk eller en spørgeskemabesvarelse |   |   |
| Bundle | En samling af flere ressourcer i FHIR |   |   |
| Borgertilstand | Kodede tilstande, som udtrykker blandt andet en borgers behov og forudsætninger for omsorg |   | FSIII |
| KAM | En brugergrænseflade, der stilles til rådighed af FUT-I som giver mulighed for at definere planer, aktiviteter, spørgeskemaer og teams bestående af sundhedsperonale |   |   |
| Trifolia | Et system (med en brugergrænseflade) der anvendes til at vedligeholde terminologi, kodesystemer (f.eks. diagnoser) og værdisæt, der "plukker" værdier fra et eller flere kodesystemer |   |   |
| SEB | Sundhedsvæsenets elektroniske brugerstyring, som samler alle sundhedsfaglige brugere på tværs af organisatoriske og sektorielle skel |   |   |



# Forretningsarkitektur

FUT Infrastrukturens formål er omsat til en forretningsarkitektur, der består af kapabiliteter, der hver stiller data, services og processer til rådighed for udviklingen af en anvenderløsning. I nedenstående figur introduceres kapabiliteterne inddelt i tre grupperinger:

![Billede](images/forretningsarkitektur.png)

De applikationsvendte kapabiliteter, som giver mulighed for at bygge en anvenderløsning på baggrund af adgang til data med en veldefineret model og tilhørerende services.

* Basiskapabiliteter, der sikrer at de mere tekniske aspekter af FUT infrastrukturen kan realiseres. Det drejer sig fortrinsvist om integration til data og services i det øvrige IT-landskab for sundhed, sikkerhed , analyse og rapportering og drift.

* Governance, Risc og Compliance, som er den organisatoriske og dokumentations-baserede støtte til en målrettet, stabil og sikker anvendelse og videreudvikling af FUT Infrastrukturen.

* Konkret anvendes FHIR forretningsobjekter og services til realisering af de tekniske aspekter, mens driftsaspekterne håndteres ved hjælp af containerization i kubernetes.

Tilføj data og proces capability, gør drift, support og devops tydligere (evt eget lag?) og huske også koder og terminologi, tilføj også planer og spørgeskemaer

omdøb til eksterne data og services

I de følgende afsnit introduceres hovedprocesserne for forretningskapabiliteterne kort. Senere i dokumentet gennemgås de vigtigste processer set fra en anvenderløsnings perspektiv.

## Patienter og Pårørende

Vedligehold af borgeres data, som støttes af

* Integration til eksterne data og services: Import af data fra CPR

* Vedligehold af pårørende-relationer

* Uddelegering af fuldmagt til pårørende

* Udsendelse af beskeder til borgere, som støttes af

* Kommunikation med borgere: Afsendelse via NemSMS

## Aktører og Ansvar

Vedligehold af Organisatoriske data, som støttes af

* Integration til eksterne data og services: Blandt andet SOR, Fælleskommunale Organisationssystem og Yderregisteret

* Vedligehold af Careteams bestående af sundhedspersonale på tværs af organisationer, der varetager omsorg for borgere

## Beslutningsstøtte

Definition af forretningslogik for beslutningsstøtte, eksempelvis til triagering

Afvikling af forretningslogikken på baggrund af data fra borgeres aktiviteter og oprettelse af FHIR-ressourcer, der repræsenterer beslutningsstøtte

## Planer, Aktiviteter og Spørgeskemaer

Vedligehold af plandefinitioner, der beskriver hvordan omsorgen konkret udføres for en konkret diagnose, herunder inkluderede aktiviteter og anvendelse af beslutningsstøtte

Vedligehold af aktivitetsdefinitioner, der kan indgå i en eller plandefinitioner (herunder spørgeskemaer) samt grænseværdier for aktiviteterne (f.eks. højeste tilladte puls) til brug under afvikling af beslutningsstøtte

Vedligehold af spørgeskemadefinitioner, der kan indgå i en eller flere aktivitetsdefinitioner

## Koder og terminologi

Vedligehold af kodesæt og terminologi, som understøttes af

* Integration til eksterne data og services: Blandt andet import af diagnoser og borgertilstande

* Definition af værdisæt, på baggrund af kodesæt, eksempelvis

## Forløb

* Oprettelse og vedligehold af telemedicinsk forløb

* Vedligehold af en eller flere planer for omsorgen i forløbet på baggrund af plandefinitioner med tilpasninger til den enkelte borger

* Udsendelse af påmindelser om forestående aktiviteter til borgere, som støttes af

 * Kommunikation med borgere

* Udførsel af aktiviteter og opfølgning på disse, blandt andet på baggrund af afvikling af beslutningsstøtte

* Oprettelse af opfølgningsopgaver til Careteams baseret på afvikling af beslutningsstøtte

## Adgange og rettigheder

Vedligehold af samlet hybrid brugerbase baseret på

Adgang for borgere og pårørende via MitID

Adgang for sundhedspersonale via SEB, herunder brugernes roller og dataafgrænsninger

Adgange for øvrige aktører, herunder systemer via lokal brugerdatabase

Adgang baseret på

Roller, der beskriver hvad en bruger må udføre og kan tildeles brugeren i den hybride brugerbase

Dataafgrænsninger, der beskriver hvilke data (primært forløbsdata) en bruger må se

Auditlogning af brugeres anvendelse af systemet

## Integration til eksterne services

Integrationerne foretages gennem NSP. De primære anvendelser er beskrevet som støtte til de øvrige processer.

## Deling af data med eksterne aktører

Deling af forløbsdata, som støttes af

Deling af data til eksterne aktører: KIH

## Kommunikation med borgere

De primære anvendelser er beskrevet som støtte til de øvrige processer

## Analyse og Rapportering (under udvikling)

Overblik over brug gennem dashboards i business intelligence

Udtræk af data til anvendelse udenfor data platformen gennem API med understøttelse af restriktioner på og maskering af data

## Drift af infrastrukturen og anvenderløsninger, der understøttes af tværgående

DevOps processer via repositories og pipelines

skalering og isolering via containerization

udstilling af services via service mesh

sporing og måling af kald via observability

monitorering til understøttelse af stabil drift og hurtig problemløsning

## Governance, Risc og Compliance

Videreudvikling og tilpasning af FUT Infrastrukturen efter behov

Opfølgning på drift og kontrakter

Anvendelse af infrastrukturen og dens data

# Applikationsarkitektur

I dette afsnit gennemgås det, hvordan forretningsarkitekturen er realiseret i en applikationsarkitektur. Først fokuseres der på, hvordan FUT-Infrastrukturen understøtter anvenderløsninger i at lave en brugervendt applikation og hvordan anvenderløsningen overordnet skal opbygges. Derefter øges detaljeringsgraden i forhold til, hvordan anvenderløsningen teknisk skal opbygges.

## FUT-Infrastrukturen

I dette afsnit introduceres det kort, hvordan forretningsarkitekturen er realiseret. Som det ses af nedenstående illustration er ansvaret for applikationen delt mellem anvenderløsningen og FUT Services. Anvenderløsningens ansvar er at lave en borger- og klinikervendt service i form af backend service med et tilhørende interface. Anvenderløsningen bruger FUT-Infrastrukturen services og leveres som en komponent, der driftes i samme miljø som infrastrukturen, konkret via Kubernetes. Desuden kan anvenderløsningen indeholde en frontend, som udstiller services til borgere og sundhedspersonale. Deployment varetages af tværgående DevOps processer og værktøjer, mens  Sikkerheden varetages af Keycloak.

![Billede](images/anvender-applikation.png)

... tilføj devops pipeline...

I de følgende afsnit introduceres services i infrastrukturen kort med henblik på at give overblik i forhold til anvenderløsninger. Der gives endvidere eksterne referencer til yderligere dokumentation.

### Brugervendte Services

KAM, som tilbyder vedligehold af careteams samt planerdefinitioner, aktiviteter og spørgeskemaer

Trifolia, som tilbyder vedligehold af terminologi, kodesystemer og værdisæt

### FUT-I Microservices

Tilbyder øvrige applikationsvendte kapabiliteter fra forretningsarkitekturen gennem:

Adgang til FHIR-baserede mikrotjenester via REST/JSON

Brug af standardiserede FHIR-profiler og -ressourcer

Understøttelse af søgning med parametre, filtrering, paging og conditional updates

### Driftsservices

Anvender Kubernetes samt tilhørende værktøjer til monitoring og fejlhåndtering

Inkluderer både FUT-Infrastrukturen og anvenderløsninger

Anvender container orchestration, skalering og rolling updates

### Platformservices

Istio Service Mesh

Gennemtvinger sikkerhed i samspil med Keycloak IdP og FUT-I Microservices

Router kald til den korrekte service i Kubernetes

Adgangsbegrænsning og observabilitet.

Keycloak  IdP

Anvendes til brugerautentifikation (OIDC)

Anvenderløsninger får et JWT-token, som anvendes ved adgang til API’er

validerer token og håndhæver adgang baseret på scopes og tilknytning til fx CareTeams

Brugere kan være sundhedsprofessionelle eller administrative medarbejdere (via SAML federation) eller patienter (via MitID integration)

Audit og event logning

### DevOps Services

CI/CD pipeline via GitLab

Image hosting i Harbor

Helm til deployment orchestration.

## Anvenderløsninger

En anvenderløsninger er en containeriserede webklient med tilhørende backend-komponenter, der interagerer med en mikroservice-baseret FHIR-platform hostet på Kubernetes (k8s). Den understøtter autentificering via Keycloak og adgang til FHIR-data gennem sikrede API-kald. Den deployes som en Helm-baseret applikation og integreres i platformens tekniske services som Istio og CI/CD pipelines.

![Billede](images/anvender-teknologi.png)


I de følgende afsnit beskrives kravene til anvenderløsningens forskellige dele.

### Frontend

Udvikling og vedligeholdelse af webbrugergrænsefladen.

Håndtering af brugerinteraktion, session og adgangsforhold via JWT.

Integration af login-flow og viderestilling til Keycloak (OpenID Connect).

### Backendkomponent

Er en containeriseret backend, som udstiller services via et web-baseret interface

Validerer JWT tokens og vælger en brugerkontekst ud fra de roller og data-adgange tokenet indeholder

Anvender API-kald for at tilgå FHIR-tjenester

Implementerer forretningslogik, regler (fx Drools) og caching.

Kommunikerer med øvrige anvenderspecifikke mikrotjenester

### Containerization, Infrastructure-as-Code og Deployment

Vedligeholdelse af Helm Chart inkl. værdikonfiguration (values.yaml) per miljø

Udgivelse af images til container registry (Harbor)

CI/CD pipelines (GitLab) til automatiseret build, test og deployment

Udarbejdelse og test af Kubernetes-specifikke artefakter som Service og VirtualService

Link til "sådan bygger du ..."

# Processer

I dette afsnit introduceres de processer, der er mest relevante for processer for anvenderløsninger. Da det overordnede ansvar for en anvenderløsning er at understøtte telemedicinske forløb tager præsentationen udgangspunkt i denne. Derefter gennemgås de vigtigste detaljer omkring definition af planer aktiviteter, da de er en væsentlig forudsætning for oprettelse af et forløb. Endelig præsenteres de konkrete underprocesser, som udgør kernen i omsorgen for borgeren. I beskrivelsen af processerne er vægten lagt på aktører, events og flow samt hvordan FUT-Infrastrukturens services understøtter dette i form af FHIR ressourcer og operations.

## Forløb

Forløbsprocessen er den centrale proces, en anvenderløsning skal understøtte. Den er illustreret i nedenstående figur, hvor selve processen er repræsenteret ved den gule kasse Forløb, som indeholder de underprocesser, anvenderløsningen er ansvarlig for. I figuren fremgår også et antal processer, som FUT Infrastrukturen tilbyder anvenderløsninger for at understøtte forløbet. Disse beskrives senere i dette afsnit.

![Billede](images/proces-forløb.png) 
Det er forløbet, der beskriver hvilken diagnose, borgeren modtager omsorg for, samt hvilke parter der er involveret. Omsorg dækker bredt over monitorering, behandling, undervisning og hjælp til selvhjælp. Parterne består dels af de sundhedsfaglige personer, der er involveret i det konkrete forløb samt de organisatoriske enheder, der har ansvaret for dem. Den konkrete omsorg er repræsenteret af en plan, der beskriver de aktiviteter, der skal udføres for eller af borgeren.

Eksempler:

En borger er i forløb for forhøjet blodtryk (diagnose) og såvel egen læge som kommunale sundhedsfaglige medarbejdere (parter) er involveret i monitorering gennem ugentlige målinger af borgerens blodtryk (plan)

En borger er i forløb med henblik på rygestop ("diagnose") og interagerer dagligt med en hjælp-til-selvhjælp løsning (plan) med mulighed for sparring hos et kommunalt sundhedscenter (part)

En borger er i forløb med henblik på overvågning af hjertelidelse (diagnose) og rapporterer dagligt puls og andre data på baggrund af udførte aktiviteter (plan). Såvel læge på sygehus samt kommunale sundhedsfaglige medarbejdere indgår i monitoreringen af borgerens tilstand (parter).

Et forløb opstår når en borger bliver tilkendt det på baggrund af en klinisk vurdering og samtale med borgeren. Efter oprettelsen af forløbet er oprettet overgår det til underprocessen Aktivitet, Måling og Opfølgning, som er de centrale begreber i den plan, der beskriver omsorgen. I forbindelse med opfølgningen kan der vise sig behov for at tilpasse planen. Forløbet kan afsluttes ved at borgeren eksplicit udtræder (herunder at borgeren afgår ved døden) eller på baggrund af opfølgningen.

Under de gule proces-elementer i figuren er det angivet, hvilke centrale FHIR ressourcer, der repræsenterer de forskellige entiteter i FUT Infrastrukturen. Som det ses er disse ressourcer opdelt i tre lag:

Det øverste lag er FHIR ressourcer, hvor det primære ansvar for vedligehold (livscyklus) ejes af FUT Infrastrukturen gennem støtteprocesser - enten via en brugergrænseflade eller baseret på hændelser

Det nederste lag er FHIR ressourcer, hvor det primære ansvar for vedligehold (livscyklus) ejes af anvenderløsninger - gennem kald af services i FUT Infrastrukturen

Det mellemste lag er FHIR ressourcer, hvor ejerskabet for vedligehold (livscyklus) er delt mellem FUT Infrastrukturen og anvenderløsningen.

Det ses således, at det er anvenderløsningen, der har ansvar for at oprette forløbet, kaldet Episode of Care i FHIR. Tilsvarende har den ansvar for at vedligeholde Careplan, som repræsenterer den enkelte borgers plan specialiseret fra den overordnede skabelon (Plan Definition), som vedligeholdes af infrastrukturen gennem brugergrænsefladen i KAM. Borgerens plan indeholder et antal Service Requests, der modsvarer de aktiviteter, der indgår i skabelonen og giver mulighed for tilpasning.

Senere i dette dokument gennemgås det, hvordan FUT Infrastrukturen understøtter anvenderløsningen i at realisere forløbsprocessen i kraft af services til data og funktionalitet i forbindelse med de omtalte FHIR ressourcer. Inden da introduceres de støtteprocesser, der er vist omkring  for at give en introduktion til de FHIR ressourcer, der stiller information om borgere, teams, organisation, planer mm. til rådighed for anvenderløsningen.

De processer, der er placeret udenfor forløbsprocessen i figuren tilbydes af FUT infrastrukturen til understøttelse af forløbsprocessen. En anvenderløsning kan (og i nogle tilfælde skal) således anvende disse. Nogle af støtteprocesserne kan afvikles via brugergrænseflader, der stilles til rådighed af FUT Infrastrukturen. Andre er kun tilgængelige via FHIR services eller afvikles på baggrund af hændelser. Støtteprocesserne beskrives i nedenstående tabel.

| Proces | Formål | Anvendelse | FHIRressourcer |
| --- | --- | --- | --- |
| Vedligehold af terminologi og koder | Sikre ensartede, veldefinererede og versionerede begreber og koder, herunder diagnoser | Vedligehold varetages gennem service requests til FUT-S, der anvender brugergrænsefladen i Trifolia. Se [brugervejledning](https://docs.ehealth.sundhed.dk/latest-released/trifolia/usermanual/index.html).| ValueSet CodeSystem |
| Vedligehold af Careteams | Sikre at sundhedsfaglige medarbejdere kan arbejde sammen på tværs af organisatoriske grænser | Oprettelse og vedligehold af teams som kan indeholde medarbejdere fra såvel regioner, kommuner samt ydersektoren. Varetages af administrative medarbejdere gennem KAM. Se [brugervejledning](https://fut-portal.rm.dk/spaces/FSD/pages/23101475/Oprettelse+af+Care+teams) | CareTeam |
| Vedligehold af Plandefinitioner | Sikre effektivitet, kvalitet og ensartethed i definition af skabeloner for planer, som definerer borgerens aktiviteter på tværs af anvenderløsninger | Varetages af sundhedsmedarbejdere tilknyttet en anvenderløsning gennem KAM. Se [brugervejledning](https://fut-portal.rm.dk/spaces/FSD/pages/23101650/Oprettelse+af+planer).    | PlanDefinition, ActivityDefinition |
| Vedligehold af Spørgeskemaer | Sikre effektivitet, kvalitet og ensartethed i definition af spørgeskemaer for planer, som definerer borgerens aktiviteter på tværs af anvenderløsninger | Varetages af sundhedsmedarbejdere tilknyttet en anvenderløsning gennem KAM. Se [brugervejledning](https://fut-portal.rm.dk/spaces/FSD/pages/23101506/Oprettelse+af+sp%C3%B8rgeskema). | Questionnaire |
| Støtte til gennemførsel af aktiviteter | Sikre effektivitet, kvalitet og ensartethed i gennemførsel af de aktiviteter, der indgår i borgerens planer på tværs af anvenderløsninger | Varetages af infrastrukturen på baggrund af præferencer for kommunikation for sundhedspersonale og borgere sat af anvender.  | Communication CommunicationRequest Task. [Dokumentation](https://ehealth-dk.atlassian.net/wiki/spaces/EDTW/pages/2415034369/Controlling+Creation+of+Messages).|
| Beslutningsstøtte for målinger | Støtte automatisering, kvalitet og ensartethed i kliniske vurderinger (herunder triagering) på baggrund af målinger fra de aktiviteter, der indgår i borgerens aktiviteter. | Definition af regler varetages af anvenderløsningen i form af udvikling af regler, der opbevares i FHIR Library. Afvikling varetages af FUT-Infrastrukturen , som på baggrund af borgerens aktiviteter og måledata producerer kliniske indtryk og opgaver, som anvenderløsningen præsenterer for de tilknyttede careteams.  | FHIR Library ServiceRequest Measurement ClinicalImpression Task. [Dokumentation](https://ehealth-dk.atlassian.net/wiki/spaces/EDTW/pages/2550661140/Automated+Processing#AutomatedProcessing-AutomatedProcessingofSubmittedMeasurement)   |
| Deling af målinger til nationalt arkiv | Dele | Varetages af FUT Infrastrukturen på baggrund af FHIR data skabt og vedligeholdt af anvenderløsninger. | [Dokumentation](https://ehealth-dk.atlassian.net/wiki/spaces/EDTW/pages/2698903576/Sharing+through+Registering+Documents+in+National+Document+Sharing+Infrastructure)   |
| Planlægning og afholdelse af videomøder | Sikre effektiv kommunikation mellem borger og sundhedspersonale | Varetages af anvenderløsning gennem FUT Microservice | Appointment [Dokumentation](https://ehealth-dk.atlassian.net/wiki/spaces/EDTW/pages/663945265/Video+endpoint+federation+VDX) |
| Vedligehold persondata i FUT | Sikre korrekte og opdaterede grunddata om borgere | Stamdata importeres af FUT-I i form af cpr-data | Person Patient RelatedPerson [Dokumentation](https://ehealth-dk.atlassian.net/wiki/spaces/EDTW/pages/3553820678/Synchronization+of+National+patient+data) |



## Opret Plandefinition

Borgerens planer tager udgangspunkt i tilpasning af en planskabelon. Skabelonerne har til formål at sikre kvaliteten i de planer, borgerne konkret tildeles. I Skabelonerne angives derfor mål og rammer for brugen af planen, såvel som instrukser for, hvilke aktiviteter, der skal udføres. En aktivitet er således karakteriseret ved hvad der skal udføres, hvornår den skal udføres og hvordan det relaterer til de mål og rammer, der er indeholdt i planen.

![Billede](images/proces-plan.png)

Selvom processen med at definere planskabeloner er understøttet af brugergrænsefladen i KAM er det alligevel værd at gennemgå hvordan opbygning sker for at understøtte forståelsen af, hvordan planskabelonerne senere bruges. Det skal bemærkes, at den proces, der illustreres herunder er logisk opbygget med henblik på at forstå FHIR ressourcerne og ikke følger det brugervendte flow i KAM. Underprocesserne i definitionen af en planskabelon beskriver i det følgende afsnit.

I nedenstående tabel beskrives formål, anvendelse og de involverede FHIR ressourcer for oprettelse af plandefinitioner, herunder aktivitetsdefinitioner og spørgeskemaer.

| Underproces | Formål | Anvendelse | Involverede FHIR Ressourcer |
| --- | --- | --- | --- |
| Definer mål og rammer | Fastlægge hvem og hvad planen skal adressere og hvilke artifakter, der skal anvendes i den | Varetages af sundhedsmedarbejder tilknyttet en anvenderløsning gennem KAM og danner derefter grundlag for tilrettede planer (CarePlan) for borgere.| [PlanDefinition](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-plandefinition.html) [UsageContext](https://hl7.org/fhir/R4/metadatatypes.html#UsageContext) Goal Subject Typer [Library](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-library.html) [DocumentReference](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-documentreference.html) |
| Definer struktur og afvikling | Fastlægge den overordnede struktur for aktiviteter i plandefintionen, herunder rækkefølge for triggere. | Varetages af sundhedsmedarbejder tilknyttet en anvenderløsning gennem KAM | [action](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-plandefinition-definitions.html#PlanDefinition.action) [ActionTrigger](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-actionTrigger.html) Role |
| Specificer aktiviteter | Udspecificere hvornår og hvordan aktiviteter skal udføres | Varetages af sundhedsmedarbejder tilknyttet en anvenderløsning gennem KAM |[ActivityDefinition ](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-activitydefinition.html) [Questionnaire](https://hl7.org/fhir/R4/questionnaire.html) ReferenceRange Timing Typer |
| Aktivér plan | Publicere planen til brug | Varetages af sundhedsmedarbejder tilknyttet en anvenderløsning gennem KAM |   |



.... Reference til vertical migration. ...

## Forløbsoprettelse

Oprettelse af et telemedicinsk forløb foretages af en sundhedsmedarbejder (kliniker) og består i at indhente samtykke fra borgeren, skabe selve forløbet med diagnose, som er et element, der udpeger en såkaldt Condition, som er et valueset, der består af diagnosekoder og borgertilstande. Derefter tilpasses og tildeles en eller flere planer til forløbet. Endelig aktiveres forløbet så omsorgen for borgeren kan begynde.
![Billede](images/proces-forløb-opret.png)


Oprettelse af forløb med tilknytning af plan

Underprocesserne i oprettelsen af et forløb beskrives i den følgende tabel.

| Proces | Formål | Anvendelse | Involverede FHIR Ressourcer |
| --- | --- | --- | --- |
| Indhent Samtykke | Sikre borgerens samtykke til forløbet | Indhentes af sundhedspersonale og dokumenteres gennem anvenderløsningen ved oprettelse af forløbet. | Consent |
| Opret Forløb | Oprette et forløb for en borger med kendt diagnose og ansvar i inaktiv tilstand | Foretages af sundhedspersonale gennem anvenderløsningen. | som opretter en EpisodeOfCare med tilhørende Patient, Condition (gennem elementet diagnosis), Consent, Careteam og Organisation |
| Tildel Planer | Oprette borgervendte planer med aktiviteter for forløbet | Foretages af sundhedspersonale gennem anvenderløsningen. Der kan tildeles planer | , som giver skaber en CarePlan med tilhørende Service Requests, der beskriver hvilke aktiviteter, borgeren skal udføre. Disse skabes ved tilpasning af en Plandefinition (med tilhørende ActivityDefinitions), som matcher en af forløbet Conditions. ReferenceRange og RerenceBase anvendes til at udtrykke grænse værdier for henholdsvis service requests og målet med careplanen. |
| Aktivér Forløb | Aktivere forløbet | Når forløbet og dets planer er klar aktiveres det af sundhedspersonalet gennem anvenderløsningen. | EpisodeOfCare |



## Aktivitet, Måling og Opfølgning

Den overordnede arbejdsgang for forløb tager udgangspunkt i, at borgeren eller en kliniker udfører de aktiviteter, der indgår i de individuelle planer for borgeren. Aktiviteterne vil ofte være gentagne (periodiske), så de skal udføres på bestemte ugedage og klokkeslæt. Selve udførelsen vil typisk bestå af besvarelse af spørgeskemaer, tekstuelle tilkendegivelser om borgerens helbred og velbefindende eller aflæsning af tal-værdier for eksempelvis blodtryk, puls eller iltmætning. 
![Billede](images/proces-akt-mål-opf.png)


Anvenderløsningen præsenterer typisk aktiviteterne for brugeren, som derefter kan udføre dem og indsende resultaterne. I FUT-I omtales disse resultater som måleresultater (measurements),der består af et antal FHIR ressourcer. Disse refererer til aktiviteten og indeholder tidspunkt for indsendelsen samt tidsperioden, som måleresultatet gælder for.

Måleresultaterne danner grundlag for, at sundhedspersonalet kan følge udviklingen i borgerens tilstand. Udover de konkrete værdier i måleresultatet tilbyder FUT-I også afvikling af beslutningsstøtte, som kan foretage eksempelvis triagering på resultaterne. Denne beslutningsstøtte bliver automatisk afviklet når en måling bliver indsendt af anvenderløsningen. 

Det er op til den enkelte anvenderløsning at specificere de regler, der skal afvikles for at realisere beslutningsstøtten. En regel kan både forholde sig til værdier i såvel den enkelte måling som i udviklingen over de seneste målinger. En regel kan for eksempel forholde sig til, at en borger har iltmætning i blodet på 89 procent eller at mætningen over de seneste målinger har udviklet sig gradvist fra 96 procent til 92 procent. 

Uanset om det er beslutningsstøtte eller sundhedspersonale, der beskriver noget om borgerens tilstand foregår det i FUT-I i form af et klinisk indtryk (clinical impression). Disse indtryk vil udpege de dele af måleresultater, som ligger til grund for dem. Både regler og sundhedspersonale kan derudover tilknytte opgaver, der skal udføres på baggrund af de kliniske udtryk. Indenfor FUT-I vil en opgave eksempelvis kunne være at afholde et videomøde med borgeren eller at foretage en justering af borgerens plan. Udenfor FUT-I vil en opgave eksempelvis bestå i bestilling af ydelser hos andre sundhedsorganisationer.

Underprocesserne beskrives i den følgende tabel.

| Proces | Formål | Anvendelse | Involverede FHIR Ressourcer |
| --- | --- | --- | --- |
| Borgeraktivetet | Give borger eller sundhedspersonale overblik over udestående aktiviteter, udføre disse og indsende måleresultatet | Anvendersløsningen henter overblik over borgerens aktiviteter og indsendte måleresultater for en given periode. Heraf kan anvenderløsningen udlede både allerede udførte og ikke udførte aktiviteter. På baggrund heraf kan den udstille muligheden for at vælge, hvilken aktivitet borgeren skal udføre, samt hvilket tidsrum måleresultatet skal gælde for. Dette tidsrum vil ofte være stærkt knyttet til det tidsrum aktiviteten er knyttet til. Eksempelvis kan det give mening at besvare et spørgeskema på en given dag, men besvare det på baggrund af, hvordan borgeren havde det dagen før.<br> Når aktiviteten er udført indsendes resultatet, hvorefter eventuel beslutningsstøtte bliver afviklet automatisk | Borgerens aktiviteter hentes med FHIR operationen [Get Patient Procedures](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/OperationDefinition--s-get-patient-procedures.html)  <br><br>Måleresultateter indsendes med FHIR operationen submit-measurement, som konkret tager mod et FHIR Bundle bestående af: <br><br><ul> <li>[ Observation](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-observation.html), der kan indeholde tal- og teksværdier</li><li>[Media](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-media.html), som kan indeholde billedmateriale </li><li>[QuestionnaireResponse](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-questionnaireresponse.html), der er en besvarelse af et spørgeskema </li><li>[Provenance](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-provenance.html), der kan beskriver, hvordan måleresultatet er blevet til</li></ul> |
| Beslutningsstøtte for måleresultater | Yde støtte til beslutninger på baggrund af borgerens målinger |  Ved indsendelse af måleresultater for aktiviteter i borgerens individuelle plan bliver de regler, som er specificeret i plandefinitionen, som er knyttet til borgerens individuelle plan afviklet af FUT-I.<br><br> | Infrastrukturen identificerer hvilke regler, der skal afvikles ud fra definitionen i Library. Resultatet af afviklingen afhænger af reglener, men kan være:<br><br> <ul><li>[Task](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-task.html) </li><li>[ClinicalImpression](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-clinicalimpression.html)  </li></ul> |
| Opfølgning |  Afklaring af nødvendige handlinger på baggrund af borgerens måleresultater og beslutningsstøtte | Sundhedspersonale kan via anvenderløsningen danne sig et overblik over borgerens tilstand og udviklingen i samme. Med afsæt heri kan sunhedspersonalet beskrive yderligere indtryk af borgeren, indkalde borgeren til en videokonsultation eller ændre i borgerens plan. |  Anvenderløsningen kalder [Search Measurement](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/OperationDefinition--s-search-measurements.html), som giver overblik over målinger. <br><br> Endvidere anvenderløsningen fremsøge og oprette [Task](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-task.html). Bemærk at der allerede kan være oprettet task ved afvikling af beslutningsstøtte. |
| Invalidering af måleresultat | Fejlmarkere et måleresultat og understøtte indsendelse af nyt|  I tilfælde hvor det konstateres, at der er indsendt et forkert måleresultat understøtter FUT-I at disse kan markeres som fejlagtige. Herved kan en ny måling udføres samtidig med, at det fejlagtige måleresultat stadig eksisterer som grundlag for sporbarhed og optimering.  | Anvenderløsningen kalder [Invalidate / Retract Invalidation of a Measurement](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/OperationDefinition-ClinicalImpression-t-set-measurement-validity.html)   |



## Støtte til Gennemførsel af Aktiviteter

FUT-I kan udsende forskellige typer af kommunikation i forbindelse med, at der indtræffer hændelser - enten baseret på tid eller udførsel af en egentlig handling. I dette afsnit beskrives den kommunikation, som understøtter gennemførsel af aktiviteter.

![Billede](images/proces-støtte.png)

Underprocesserne beskrives i den følgende tabel.

| Proces | Formål | Anvendelse | Involverede FHIR Ressourcer |
| --- | --- | --- | --- |
| Til- og framelding | Give borgere og sundhedsmedarbejdere medbestemmelse over hvilken kommunikation, de modtager, i forbindelse med borgeres gennemførsel af aktiviteter |  Det er muligt for anvendersystemet at angive om en modtager i form a borger eller sundhedspersonale ønsker at modtage kommuniktion ved konkrete hændelser. Bemærk at kommunikation udsendes som standard ved nogle kombinationer af aktør og hændelse, men ikke ved andre. Det er derfor muligt både at undertrykke og aktivere kommunikation.   | Anvenderløsningen vedligeholder [ CommunicationRequest](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-communication-request.html). |
| Kommende aktivitet | Minde borgere om deres forestående aktiviteter, så de husker at gennemføre dem |  FUT-I kan udsende kommunikation for at minde borgere om forestående aktiviteter, for at hjælpe dem til at huske dem.| [EHealthMessage](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-message.html)|
| Manglende aktivitet | |  FUT-I kan udsende kommunikation for at minde borgere om aktiviteter, der har overskredet deres deadline, så de kan gennemføre dem hurtigst muligt. Endvidere er det muligt at gøre sundhedspersonale opmærksomme på, at en borger ikke har udført sin aktivitet, så de kan hjælpe borgeren  |[EHealthMessage](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-message.html)  |
| Afslut aktivitets-relaterede opgaver | Afslutte de opgaver til sundhedspersonale, som er oprettet for tidligere konstateret manglende gennemførsel af borgeraktivitet når aktiviteten er gennemført. |  FUT-I kan under afviklingen af beslutningsstøtte konstatere, om den aktivitet, som borgeren har udført er udført senere end den var planlagt I såfald kan underprocessen manglende aktivitet have oprettet en task til careteamet. Denne tilknyttede taks kan i givet fald lukkes. | [Task](https://build.fhir.org/ig/fut-infrastructure/implementation-guide/StructureDefinition-ehealth-task.html)|



... omdøb Afslutning af tilhørende tasks i tegningen...

# Teknologi

FHIR Microservice begrænsninger

query på tværs

transactions

Miljøer



