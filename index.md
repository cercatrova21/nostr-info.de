---
layout: resources
title: nostr Info
image: /assets/images/cover.png
description: nostr ist neu und verwirrend, aber auch wirklich cool.
redirect_from: resources
---

**TL;DR:** nostr[^fn-nostr] ist ein Protokoll, das das Zeug hat, Twitter, Telegram und andere Dinge zu ersetzen.

[^fn-nostr]: nostr = Notes and Other Stuff Transmitted von Relays

---

## WTF ist nostr?

nostr ist neu und verwirrend, aber auch ziemlich cool. Es ist **das einfachste offene Protokoll, das in der Lage ist, eine
zensurresistentes globales "soziales" Netzwerk** ein für alle Mal zu schaffen.

- Es verlässt sich nicht auf einen vertrauenswürdigen zentralen Server und ist daher widerstandsfähig.
- Es basiert auf kryptografischen Schlüsseln und Signaturen und ist daher fälschungssicher.
- Es stützt sich nicht auf P2P-Techniken, darum funktioniert es.

---

<center>
  <p><small><a href="#toc">↓ Inhaltsübersicht ↓</a></small></p>
</center>

---

Das Design von nostr ist sehr einfach:

- Es besteht aus zwei Komponenten: **Clients** und **Relays**. Jeder Benutzer betreibt einen Client. Jeder kann ein Relay Server betreiben.
- Jeder Nutzer wird durch einen öffentlichen Schlüssel identifiziert und jeder Beitrag wird signiert. Jeder Client validiert dann diese Signaturen.
- Clients holen Daten von Relays ihrer Wahl ab und veröffentlichen Daten an andere Relays ihrer Wahl. Ein Relay spricht nicht mit einem anderen Relay, sondern nur direkt mit den Clients.

Um nostr zu verwenden, benötigst du einen [key](#keys) und einen [client](#clients).

- Jeder hat einen Client. Das kann ein nativer Client oder ein Web-Client usw. sein. 
- Um etwas zu veröffentlichen, schreibst du einen Beitrag, signierst ihn mit deinem Schlüssel und sendest ihn an mehrere Relays (Server, die von jemand anderem oder von dir selber gehostet werden). 
- Um Aktualisierungen von anderen Personen zu erhalten, fragst du mehrere Relays ab, ob sie etwas über diese anderen Personen wissen. 
- Jeder kann ein Relay betreiben. Ein Relay ist sehr einfach und dumm. Er tut nichts anderes, als Beiträge von einigen Leuten anzunehmen und an andere weiterzuleiten.
- Relays müssen nicht vertrauenswürdig sein. Signaturen werden auf der Client-Seite verifiziert.

## Schlüssel

Deine Schlüssel sind deine Identität. Du kannst dich deinen öffentlichen Schlüssel (`npub...`) als
deinen Benutzernamen und deinen privaten Schlüssel (`nsec...`) als dein Passwort vorstellen. 

Zwei kurze Hinweise:
- ⚠️ **DEN PRIVATEN SCHLÜSSEL NICHT IN WEBSEITEN EINFÜGEN**[^fn-xss] ⚠️
- Bewahre deinen Schlüssel sicher auf und gib ihn nicht weiter

Schlüssel gibt es in zwei Formaten, `hex` und dem oben erwähnten npub/nsec. Du kannst ein
ein [Schlüsselkonvertierungsprogramm](https://github.com/rot13maxi/key-convertr)[^fn-keys] verwenden, um
zwischen den beiden Formaten zu konvertieren.

[^fn-keys]: Es gibt auch das Tool [damus.io/key](https://damus.io/key/), aber verwende es NICHT für die Konvertierung privater Schlüssel. Füge deinen privaten Schlüssel nie in Webseiten ein. Tu das es einfach nicht.

[^fn-xss]: Du musst natürlich dem Betreiber der Website vertrauen und einige Clients sind anfällig für XSS-Angriffe. Viele Leute wurden bereits gerekt und mussten ihre nostr Identität deswegen neu aufbauen.

Verwende [Alvon](https://getalvon.com) oder [nos2x](https://github.com/fiatjaf/nos2x), um
deinen Schlüssel zu generieren, oder generiere ihn mit einem speziellen Tool wie
[rana](https://github.com/grunch/rana). Die vorgenannten Erweiterungen speichern
deine Schlüssel sicher (oder zumindest sicherer).

- [Nostr in der Alvon-Erweiterung](https://blog.getalvon.com/nostr-in-the-alvon-extension/)
- [Die nos2x-Browsererweiterung und warum du sie verwenden solltest](https://youtu.be/IoLw-3ok3_M)

Du kannst deine Schlüssel auch auf andere Weise generieren, wenn du weisst, was du tust.[^bip85]

[^bip85]: [BIP-85](https://bip85.com/) ist zum Beispiel eine Möglichkeit.

## Clients

Überprüfe regelmäßig [nostr.net](https://www.nostr.net/), wo aktuelle Clients gelistet sind,  oder wirf einen Blick auf die [client Vergleichstabelle](https://github.com/vishalxl/Nostr-Clients-Features-List). 

Hier sind einige, die ich mag:

- [astral.ninja](https://astral.ninja/) - Fork von Branle mit anderem UI & globalem Feed
- [snort.social](https://snort.social/) - Sehr einfacher Feed mit automatischem Bild-Upload
- [iris.to](https://iris.to/) - Saubere Oberfläche, unterstützt Blocklisten und Webtorrents
- [yosup.app](https://yosup.app/) - Handy-freundlich und twitter-ähnlich
- [hamstr.to](https://hamstr.to/) - Twitter-Schnittstelle, Unterstützung für mehrere Konten

Mobile clients:
- [Damus](https://testflight.apple.com/join/CLwjLxWl) - Twitter-style iOS client, funktioniert auch auf MacOS
- [Amethyst](https://play.google.com/store/apps/details?id=com.vitorpamplona.amethyst) - Twitter-style Android client
- Unter Android kannst du auch den [Kiwi Browser](https://kiwibrowser.com/) verwenden, mit dem Alvon oder nos2x installiert werden können, was wiederum die Verwendung eines beliebigen Webclients ermöglicht. [Yosup](https://yosup.app/) und [Hamstr](https://hamstr.to/) haben zum Beispiel gute mobile Erfahrungen.

Amethyst ist nun im Play Store verfügbar. Nosky[^nosky] und Nostros[^nostros] befinden sich in der Entwicklung und sollten bald zum Testen verfügbar sein.

[^nosky]: [KotlinGeekDev/Nosky](https://github.com/KotlinGeekDev/Nosky)
[^nostros]: [KoalaSat/nostros](https://github.com/KoalaSat/nostros)
[^amethyst]: [vitorpamplona/amethyst](https://github.com/vitorpamplona/amethyst/)

Da gibt es auch noch die [Nostr Konsole](https://github.com/vishalxl/nostr_console),
[noscl](https://github.com/fiatjaf/noscl), und
[nostr-commander](https://github.com/8go/nostr-commander-rs) wenn dir die kommandozeile besser gefällt.


## Relays

Relays sind dumme Server, die man jederzeit weglassen kann (damit sie nicht
böse werden). Du musst deinen Client mit mindestens einem Relay verbinden damit er funktioniert. Es gibt
viele Relays und du kannst dein eigenen betreiben.

- [nostr.watch](http://nostr.watch/)
- [nostr.info](https://nostr.info/relays/)

Betreibe dein eigener:

- [Einrichten eines Nostr-Relay-Servers in weniger als 5 Minuten](https://andreneves.xyz/p/set-up-a-nostr-relay-server-in-under)[^fn-fork]

[^fn-fork]: Fork mit kleinen Änderungen/Fixes: [Installiere ein Nostr-Relay](https://www.massmux.com/install-a-nostr-relay/)

## Tools

nostr kann mehr als nur soziale Medien :)

- [Sendstr](https://sendstr.com/) - gemeinsame Zwischenablage zwischen Geräten über Nostr
- [nosbin](https://nosbin.com/) - pastebin über nostr


## Spiele

Spiele? WTF? Ja, Spiele:

- [Jester](https://jesterui.github.io/) - Schach über nostr von theborakompanioni

## Profi-Tipps

Einige Dinge funktionieren ein bisschen anders und sind nicht offensichtlich.


### Andere finden

Benutze diese Suchanfrage, um nostr-Schlüssel von Leuten zu finden, denen du auf Twitter folgst:

- [🔎 "verifying my account on nostr" (ppl you follow)](https://twitter.com/search?q=%22verifying%20my%20account%20on%20nostr%22&f=live&pf=1)

Dies verwendet die [nostr.directory](https://www.nostr.directory/) Verifizierung
Nachricht, aber das `&pf=1` schränkt die Twitter-Suche auf die Personen ein, denen man folgt.

### Bilder posten

Die meisten Clients zeigen Bild-URLs als Bilder an, du kannst also einfach ein beliebiges Bild
auf Bildfreigabeseiten hochladen und die URL wie folgt posten:

```
https://i.ibb.co/w4WvnYb/image.png
```

Das funktioniert auch für Videos oder Gifs.

Hier sind einige kostenlose Bilder-Hoster:

- [nostr.build](https://nostr.build/)
- [imgbb.com](https://imgbb.com/)
- [imgur](https://imgur.com/)
- [postimages.org](https://postimages.org/)

### Sich selbst verifizieren

Wenn du eine Domain hast und ein "verifiziertes" Häkchen haben willst, findest du hier einige
nützliche Informationen:

- [NVK's Anleitung (verwendet Github Seiten)](https://nvk.org/n00b-nip5)
- [metasikander's Anleitung](https://gist.github.com/metasikander/609a538e6a03b2f67e5c8de625baed3e)

## Statistiken

Seitdem [Jack](https://twitter.com/jack/status/1603945963944480768) beigetreten ist
(und einige Nostr-Entwickler finanziert hat), kam eine Flut von Leuten zu nostr. Da nun alles offengelegt ist, kann man dies schön
in den Statistiken sehen.

- [nashboard.space](https://nashboard.space/)
- [nostr.io](https://nostr.io/stats)
- [nostr.band](https://nostr.band/stats.html)

## Sats

Einige Clients können Lightning-Invoices nativ darstellen und den Empfänger anzeigen, 
Betrag und eine Schaltfläche zum Bezahlen. Ein solcher Client ist Damus, der ein nettes 
[kleines Widget und eine Zahlungsschaltfläche](https://i.ibb.co/zhd4Fbs/damus-invoice-render.png) hat.

## Suche

Die meisten Clients unterstützen die Suche, aber es gibt auch:

- [brb.io/search](https://brb.io/search)
- [nostr.band](https://nostr.band/)
- [nostrview.com](https://nostrview.com)

### Bots

Du kannst einen Suchbot unter [sb.nostr.band](https://sb.nostr.band) erstellen und ihm dann folgen, um neue Beiträge, die zu einem Stichwort oder Hashtag passen, direkt in deinem Feed zu erhalten.

- [Wie du einen GM bot programmierst](https://dergigi.com/2023/01/19/how-to-build-a-nostr-gm-bot/) von [Gigi](https://www.nostr.guru/p/npub1dergggklka99wwrs92yz8wdjs952h2ux2ha2ed598ngwu9w7a6fsh9xzpc)
- [nostr_bot](https://docs.rs/nostr-bot/latest/nostr_bot/)

## Podcasts

- [Pleb's Taverne - TechTuesday](https://anchor.fm/plebs-taverne/episodes/TechTuesday---nostr-erklrt-e1t7q66) - einfache Erklärung wie nostr funktioniert
- [EINUNDZWANZIG - Euer nostr Podcast Folge](https://einundzwanzig.space/podcast/news-166-euer-nostr-podcast/) - Newsfolge #166
- [nostrovia](https://nostrovia.org/) - wöchentliche Zusammenfassung
- [BR018](https://bitcoin.review/podcast/episode-18/) - [jack](https://www.nostr.guru/p/npub1sg6plzptd64u62a878hep2kev88swjh3tw00gjsfl8f237lmu63q0uf63m), [fiatjaf](https://www.nostr.guru/p/npub180cvv07tjdrrgpa0j7j7tmnyl2yr6yr7l8j4s3evf6u64th6gkwsyjh6w6), und [jb55](https://www.nostr.guru/p/npub1xtscya34g58tk0z605fvr788k263gsu6cy9x0mhnm87echrgufzsevkk5s) sprechen mit [nvk](https://www.nostr.guru/p/npub1az9xj85cmxv8e9j9y80lvqp97crsqdu2fpu3srwthd99qfu9qsgstam8y8) ([Transkript](https://Archiv.is/wip/Qoh4M), [Archiv](https://Archiv.is/wip/dkQj2))
- [Lightning Tidbits 769571](https://pod.link/1586346643/episode/33f509c2a1990640334b48739c59e31f) - [fiatjaf](https://www.nostr.guru/p/npub180cvv07tjdrrgpa0j7j7tmnyl2yr6yr7l8j4s3evf6u64th6gkwsyjh6w6) sprechen über nostr mit [André Neves](https://www.nostr.guru/p/npub1rvg76s0gz535txd9ypg2dfqv0x7a80ar6e096j3v343xdxyrt4ksmkxrck)
- [CD63 - building nostr](https://pod.link/1546393840/episode/112bd2a52d54e203ec0c11022b5aaf11), eine zensurresistente Alternative zu Twitter, mit [fiatjaf](https://www.nostr.guru/p/npub180cvv07tjdrrgpa0j7j7tmnyl2yr6yr7l8j4s3evf6u64th6gkwsyjh6w6), [jb55](https://www.nostr.guru/p/npub1xtscya34g58tk0z605fvr788k263gsu6cy9x0mhnm87echrgufzsevkk5s), und [kukks](https://github.com/Kukks), gehosted von [ODELL](https://www.nostr.guru/p/npub1qny3tkh0acurzla8x3zy4nhrjz5zd8l9sy9jys09umwng00manysew95gx) ([Transkript](https://Archiv.is/wip/Qoh4M), [Archiv](https://Archiv.ph/Qoh4M))
- [BA691 - A Native Protocol for Social Media](https://pod.link/1359544516/episode/8e647d338c79265bed63dfb06dd71e7b) von [jack](https://www.nostr.guru/p/npub1sg6plzptd64u62a878hep2kev88swjh3tw00gjsfl8f237lmu63q0uf63m)
- [BTC111 - Decentralized Social Media & Bitcoin](https://www.theinvestorspodcast.com/bitcoin-fundamentals/nostr-decentralized-social-media-william-casarin/) mit [jb55](https://www.nostr.guru/p/npub1xtscya34g58tk0z605fvr788k263gsu6cy9x0mhnm87echrgufzsevkk5s) gehosted von [Preston Pysh](https://www.nostr.guru/p/npub1s5yq6wadwrxde4lhfs56gn64hwzuhnfa6r9mj476r5s4hkunzgzqrs6q7z) ([Transkript](https://chowcollection.medium.com/preston-pysh-btc111-nostr-decentralized-social-media-bitcoin-w-william-casarin-352f6dedce46), [Archiv](https://Archiv.ph/uCSDQ))
- [What's new with Stacker.News and Nostr?](https://www.curiousdk.com/p/whats-new-with-stackernews-and-nostr) ein Gespräch mit Keyan Kousha und Max Webster ([Transkript](https://chowcollection.medium.com/david-king-whats-new-with-stacker-news-e49e3256eddc), [Archiv](https://Archiv.is/wip/wGrb8))

## Explorer

- [nostr.guru](https://www.nostr.guru/)

---

## Weitere Infos

- [nostr.net](https://www.nostr.net/) aka awesome-nostr von @aaaljaz
- [nostr-protocol/nostr](https://github.com/nostr-protocol/nostr) von fiatjaf

Artikel und Erklärungen:

- [Nostr: Eine dezentrale Alternative zu Twitter — und mehr](https://hey-bitcoin.de/anleitung/nostr-dezentrale-twitter-alternative/) von Dennis
- [Was ist Nostr und wie verwende ich es??](https://www.btctimes.com/news/what-is-nostr-and-how-do-i-use-it) von Walker V.
- [usenostr.org](https://usenostr.org/) von Pluja
- [Was ist Nostr und wie kann man Nostr nutzen?](https://github.com/vishalxl/nostr_console/discussions/31) von Vishal
- [Nostr, eine Einführung](https://wiki.wellorder.net/post/nostr-intro/) von Greg Heartsfield
- [Nostr Newcomers Häufigste Fragen und Antworten](https://uselessshit.co/resources/nostr/) von pitiunited

nostr ist ein offenes Protokoll und die meisten Clients sind Open-Source.
Du kannst jederzeit Fehler melden und PRs erstellen!

## Übersetzungen

- [Chinesisch](https://mp.weixin.qq.com/s/RoO-oOgGAXpcGyjD8IYBdw) von Cakksakkas
- [Französisch](https://nostr.fr) von Marco.BTC.fr
- [Spanisch](https://bitcoinnostr.com/recursos-de-nostr/) von [BitvonBit](https://nostr.guru/p/npub1luhyzgce7qtcs6r6v00ryjxza8av8u4dzh3avg0zks38tjktnmxspxq903)
- [Englisch](https://nostr-resources.com/)
- [Italienisch](https://gist.github.com/theRescuer/717295270a35b4641081b6ef2cdf3025) von [avallanosterza](https://nostr.guru/p/npub1l0cwargp532n6x62pdcetkau783sxhpfhwu9d6qgpqm8r0mvt0eqqhlf2c)

## Über diese Ressourcen

Der größte Teil des obigen Textes ist kopiert aus
[nostr-protocol/nostr](https://github.com/nostr-protocol/nostr) and
[nostr.net](https://www.nostr.net/). 

Diese Seite ist open source. [Verbessere diese Seite.](https://github.com/cercatrova21/nostr-info.de)

---
