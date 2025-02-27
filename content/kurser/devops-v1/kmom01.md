---
author:
    - aar
revision:
    "2021-10-29": "(C, aar) Slog ihop canvas inlämning med kmom02."
    "2020-10-20": "(B, aar) Uppdaterade med Azure inför HT20."
    "2019-04-17": "(A, aar) Första versionen släppt."
...
Kmom01: Introduktion till DevOps
==================================

Det är en fullspäckat kurs där vi ska lära oss många ny verktyg och koncept. I kursen ska vi lära oss både om det kulturella inom devops men även det praktiska. Vi börjar med att skaffa en produktionsmiljö och bekantar oss med ett påbörjat projekt som ska kopplas till en CI kedja och driftsätta manuellt.


<!-- more -->

## Vad är devops? {#devops}

Kolla på följande video för att få en introduktion till ämnet devops. Devops är ett brett ämne med många olika definitioner, här försöker skaparen av CM verktyget [Chef](https://www.chef.io) beskriva konceptet och komma fram till en rimlig definition.

[YOUTUBE src="_DEToXsgrPc" caption="Chef Style DevOps Kungfu - Adam Jacob Keynote - ChefConf 2015."]


<!-- Ny video https://www.youtube.com/watch?v=Me3ea4nUt0U kortare och med om arbetsflödet -->

För de som vill gräva ner sig i den teoretiska delen och företagskulturen av devops rekommenderar jag boken [Effective Devops](http://tinyurl.com/yyuw7a9w). Läs kapitel 1-6.

<!-- https://tinyurl.com/y4kyayqa the devops handbook -->


## Miljö {#miljo}

Tanken är att vi ska jobba med ett projekt igenom hela kursen och då behöver vi verktyg och program för att jobba med koden. Vi kommer ha både en lokal utvecklingsmiljö och en produktionsmiljö. Vi börjar med utvecklingsmiljön, som vi brukar kalla labbmiljö.



### Labbmiljön  {#labbmiljo}

Vi kommer att utöka vad som ingår i labbmiljön under kursen. Till en början behöver vi programmen som finns i [installera labbmiljön](./../labbmiljo).



### Produktionsmiljö {#produktionsmiljo}

När man jobbar enligt devops ska saker ofta gå snabbt och automatiskt, då underlättar det om man snabbt och enkelt kan starta upp och stänga ner servrar. Därför ska vi använda oss av en molntjänst, mer specifikt [Microsoft Azure](https://azure.microsoft.com/en-us/). OBS! logga inte in via den länken.



#### Azure {#azure}

För att få en introduktion till vad Azure är kan ni kolla in "What Is Azure?".

[YOUTUBE src="3Arj5zlUPG4" caption="What Is Azure?"]

Logga in på [Azure](https://portal.azure.com/#home) med ditt studentinlogg och kolla sen på videon nedanför och skapa din första VM på Azure.

[YOUTUBE src="xs9dMl_AE1A" caption="101 Skapa server på Azure."]



#### Domännamn {#domain}

Det underlättar dessutom om vi har ett domännamn som vi kan länka till en server. Om du inte redan har ett kolla in artikeln ["GitHub Education Pack och en server på Digital Ocean"](kunskap/github-education-pack-och-en-server-pa-digital-ocean). I den görs mer saker än vad vi behöver göra så kolla bara på de två följande delarna:

1. [GitHub Education Pack](kunskap/github-education-pack-och-en-server-pa-digital-ocean#gep)

1. [En domän till din server](kunskap/github-education-pack-och-en-server-pa-digital-ocean#domain) (Du kan sluta läsa när det börjar handla om Digital ocean).

<!-- Möjlig alternativ till namecheap, http://www.dot.tk/en/index.html?lang=en -->

När du har fixat en domän, kolla på videon för att ditt domännamn till servern du skapade ovanför.

[YOUTUBE src="CNSAT9n0554" caption="102 Koppla domän till Azure."]



#### 10 första minuterna {#10first}

Nu ska vi logga in på servern och konfigurera den. Vi utgår från en artikeln som är gjord för jsramverk kursen så några saker är inte exakt likadant.

När du loggar in på servern använd `azureuser` som användare istället för `root`.  
Du behöver även byta till root användaren efter att du har loggat in, gör det med `sudo su`.  
Du kan skippa följande kommandon:

```bash
apt-get remove --purge unscd
userdel -r debian
```

Brandväggsdelen är frivillig i och med att vi kommer styra portar till servern i Azure.

Gör nu [Första 10 minuter på en server](kunskap/github-education-pack-och-en-server-pa-digital-ocean#first10) delen. 



### Appen {#appen}

Nästa steg är att bekanta dig med appen som du ska jobba på i kursen. Läs igenom och följ:

[Introduktion till Devops appen](kunskap/introduktion_till_devops_appen).



#### Driftsätt appen {#driftsatt}

Vi har en server och vi har en app, då måste vi lära oss driftsätta den. Om något går fel när du jobbar igenom artikeln och du inte riktigt vet hur du ska ångra det, skapa om servern i Azure och använd dig av [skripten i repot](https://github.com/dbwebb-se/microblog/tree/master/scripts) för att snabbt göra de 10 första minuterna på en server och börja om med driftsättningen.

Jobba igenom ["Driftsätta en Flask app"](kunskap/driftsatta-en-flask-app).

<!-- https://askubuntu.com/questions/879437/ensurepip-is-disabled-in-debian-ubuntu-for-the-system-python -->



### Continues Integration {#ci}

Vi vill ha en CI-kedja till repot så att testerna automatiskt körs när du gör push. I kursen har jag valt att använda [CircleCi](https://circleci.com/). Nu ska du läsa igenom en artikel som visar hur vi kan använda CirclCi för python projekt. När du gjort det ska du göra det för ditt forkade repo.

Jobba igenom ["Continuous Integration With Python: An Introduction"](https://realpython.com/python-continuous-integration/).

När du pushar kod i ditt repo ska CircleCi köra alla unittester, integrationtester och validera koden. Använd dig av make kommandot `make test` för att köra det. Du ska **inte** använda dig av flake8 som de gjorde i artikeln. 

Om ni vill snabba på CircleCi jobbet kan ni cacha det installerade paketen, detta är frivilligt. Kolla in [Caching dependencies](https://circleci.com/docs/2.0/project-walkthrough/#caching-dependencies), det är i `steps:` delen det intressanta sker. En längre förklaring på hur det funkar kan ni hitta i [CircleCi's dokumentation](https://circleci.com/docs/2.0/caching/).



### Video {#video}

1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[devops streams ht21](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8g4N0v72y47OiNePhjOqqN)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 1xx i namnet.



### Lästips {#lastips}

1. Bättre commit meddelanden:
    - [The seven rules of a great Git commit message](https://chris.beams.io/posts/git-commit/#seven-rules). Ni kan också läsa stycket ovanför, i länken, om varför det är viktigt.
    - [Keeping Git Commit Messages Consistent with a Custom Template ](https://dev.to/timmybytes/keeping-git-commit-messages-consistent-with-a-custom-template-1jkm). I denna kursen kan ni t.ex. använda vilket kursmoment ni jobbar på i footern.

1. [Semantisk versionshantering](https://semver.org/lang/sv/), en bra versionsstandard för projekt. Vi inte riktigt den i kursen för att jag vill ha ny siffra för varje kursmoment.

1. [The 12 Factor App](https://12factor.net/) är en populär "standard" för att bygga Software-as-a-service och  används mycket i devops sammanhang.

1. [DevOps Roadmap](https://roadmap.sh/devops) Visar upp vanligaste verktygen man behöver kunna för att jobba med de tekniska delarna av devops.

    - Här kan ni se vilka av verktygen vi kommer använda oss i kursen, [i fylld devops roadmap](image/devops/devops-roadmap-filled.png)



Uppgifter  {#uppgifter}
-------------------------------------------

Följande uppgifter skall utföras och resultatet skall redovisas.

1. Lägg till funktionaliteten att följa andras blogginlägg. Jobba igenom [Kom igång med followers](kunskap/kom-igang-med-followers).

1. Driftsätt den nya funktionaliteten på din server.

1. Koppla ditt repo till CircleCi. När du gör en commit ska CricleCi köra alla unittester, integrationtester och validera koden. Lägg till en CircleCi badge i README filen för repot.

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v1.0.0. Om du pushar kmom01 flera gånger kan du öka siffrorna efter 1:an.

<!-- 1. Inkludera en länk till ditt GitHub repo och din webbsida (domännamn) i din inlämning på Canvas. -->



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Det är ingen inlämning på Canvas för kmom01. Kmom01 redovisas tillsammans med kmom02 istället.

<!--
Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Vad var din uppfattning av devops för en vecka sen?

1. Har det ändrats efter denna veckan?

1. Hur skulle du definiera devops?

1. Finns det något speciellt du vill lära dig i denna kursen?

1. Vad tycker du om kmom01's upplägg och storlek?
-->
