# Evaluatie Enterprise Linux

| :---          | :---                                                |
| Student       | Benjamin VAN LIERDE                                 |
| Klasgroep     | aalst                                               |
| Email         | <mailto:benjamin.vanlierde.w2339@student.hogent.be> |
| Hoofdopdracht | SME                                                 |
| Repo          | <git@github.com:BenVlie/elnx-sme.git>               |

## Hoofdopdracht

W4:

- nog bezig met labo 0! Tandje bijsteken!
    - "nog niet serieus aan begonnen"
    - installatie software nog slechts deels klaar
    - testscript nog nooit uitgevoerd
- maak `host_vars/pu004.yml` aan voor instellingen specifiek voor pu004 (bv. firewall)

W9:

- Nog geen laboverslagen geschreven. Graag zsm aanvullen!
- Bezig met DNS of afgewerkt?

Eindevaluatie:

- Acceptatietests:
    - LAMP, DNS ok
    - Fileserver: NIET ok
        - Wachtwoorden `rhbase_users` in plain text, moeten gehashed zijn
- Integratie-opdracht niet gerealiseerd

### Eindbeoordeling

O1: Nog niet bekwaam

## Troubleshooting

### Eerste troubleshooting-opdracht

- Algemeen:
    - Let op correct gebruik van Markdown!
- "Fysieke laag" -> "Datalinklaag" (of network access layer)
    - Is de VM aangesloten op een HO-interface met correcte instellingen
- Internetlaag
    - resultaten ping?
    - controle netwerkinstellingen onvolledig
- Transportlaag:
    - controle of nginx-service draait ontbreekt
    - poort 8080 toevoegen aan firewall-instellingen is overbodig (en introduceert zelfs een potentieel beveiligingsprobleem)
- Applicatielaag:
    - Controle logbestanden?
- Resultaat (demo):
    - ping host -> VM werkt niet
    - Service start niet

### Tweede troubleshooting-opdracht

- t/m internetlaag: ok
- Transportlaag:
    - Controle waarom service niet opstart ahv logs???
- Service start niet op

Beoordeling: nog niet bekwaam

### Derde troubleshooting-opdracht

Ok

### Eindbeoordeling

O2: Bekwaam

## Opdracht Actualiteit

Niet gerealiseerd

### Eindbeoordeling

O3: Nog niet bekwaam

## Rapportering

### Laboverslagen

Geen laboverslagen gevonden.

R1: Nog niet bekwaam

### Demonstraties

Dit aspect kan op dit moment nog niet geëvalueerd worden. Omdat niet alle taken gerealiseerd waren, is het ook niet duidelijk in hoeverre de criteria behaald zijn.

R2: Nog niet bekwaam

### Cheat sheet

Niet bijgehouden

R3: Nog niet bekwaam

## Tweede zittijd

- Hoofdopdracht afwerken
- Actualiteitsopdracht realiseren
- Extra opdracht: Webserver met Docker (details op Chamilo)
