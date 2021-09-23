---
layout: Post
title: Benutzerzentrierte Leistungskennzahlen
authors:
  - philipwalton
date: '2019-11-08'
description: |2

  Benutzerzentrierte Leistungskennzahlen sind ein wichtiges Werkzeug zum Verständnis und

  Verbessern Sie die Erfahrung Ihrer Website auf eine Weise, die der Realität zugute kommt

  Benutzer.
tags:
  - Leistung
  - Metriken
---

Wir alle haben gehört, wie wichtig Leistung ist. Aber wenn wir über Leistung sprechen – und darüber, Websites „schnell“ zu machen – was genau meinen wir damit?

Die Wahrheit ist, dass Leistung relativ ist:

- Eine Site kann für einen Benutzer schnell sein (in einem schnellen Netzwerk mit einem leistungsstarken Gerät), aber für einen anderen Benutzer langsam (in einem langsamen Netzwerk mit einem Low-End-Gerät).
- Zwei Sites können das Laden in genau der gleichen Zeit beenden, aber eine *scheint* schneller zu laden (wenn Inhalte nach und nach geladen werden, anstatt bis zum Ende zu warten, um etwas anzuzeigen).
- Eine Site *scheint* schnell zu laden, reagiert dann aber langsam (oder überhaupt nicht) auf Benutzerinteraktionen.

Wenn es also um Leistung geht, ist es wichtig, präzise zu sein und sich auf Leistung in Bezug auf objektive Kriterien zu beziehen, die quantitativ gemessen werden können. Diese Kriterien werden als *Metriken bezeichnet* .

Aber nur weil eine Metrik auf objektiven Kriterien basiert und quantitativ gemessen werden kann, bedeutet dies nicht unbedingt, dass diese Messungen nützlich sind.

## Metriken definieren

In der Vergangenheit wurde die Webleistung mit dem Ereignis <code>[load](https://developer.mozilla.org/en-US/docs/Web/API/Window/load_event)</code> Obwohl das <code>load</code> ein wohldefinierter Moment im Lebenszyklus einer Seite ist, entspricht dieser Moment jedoch nicht unbedingt dem, was den Benutzer interessiert.

Zum Beispiel könnte ein Server mit einer minimalen Seite antworten , dass „Lasten“ sofort , aber dann aufschiebt Abrufen von Inhalten und auf der Seite , bis einige Sekunden nach dem etwas anzeigt `load` - Ereignisse ausgelöst wird . Während eine solche Seite technisch gesehen eine schnelle Ladezeit haben könnte, würde diese Zeit nicht dem entsprechen, wie ein Benutzer das Laden der Seite tatsächlich erlebt.

In den letzten Jahren haben Mitglieder des Chrome-Teams in Zusammenarbeit mit der [W3C Web Performance Working Group](https://www.w3.org/webperf/) daran gearbeitet, eine Reihe neuer APIs und Metriken zu standardisieren, die genauer messen, wie Nutzer die Leistung einer Webseite erleben.

Um sicherzustellen, dass die Metriken für die Nutzer relevant sind, rahmen wir sie um einige Schlüsselfragen:

<table id="questions">
  <tr>
    <td><strong>Geschieht es?</strong></td>
    <td>Wurde die Navigation erfolgreich gestartet? Hat der Server geantwortet?</td>
  </tr>
  <tr>
    <td><strong>Ist es nützlich?</strong></td>
    <td>Wurden genügend Inhalte gerendert, damit die Benutzer damit interagieren können?</td>
  </tr>
  <tr>
    <td><strong>Ist es verwendbar?</strong></td>
    <td>Können Benutzer mit der Seite interagieren oder ist sie beschäftigt?</td>
  </tr>
  <tr>
    <td><strong>Ist es entzückend?</strong></td>
    <td>Sind die Interaktionen reibungslos und natürlich, frei von Lags und Jank?</td>
  </tr>
</table>

## Wie Metriken gemessen werden

Leistungskennzahlen werden im Allgemeinen auf zwei Arten gemessen:

- **Im Labor:** Verwenden von Tools zum Simulieren eines Seitenladevorgangs in einer konsistenten, kontrollierten Umgebung
- **Im Feld** : bei echten Benutzern, die die Seite tatsächlich laden und mit ihr interagieren

Keine dieser Optionen ist unbedingt besser oder schlechter als die andere – tatsächlich möchten Sie im Allgemeinen beide verwenden, um eine gute Leistung zu gewährleisten.

### Im Labor

Das Testen der Leistung im Labor ist bei der Entwicklung neuer Funktionen unerlässlich. Bevor Features in der Produktion freigegeben werden, ist es unmöglich, ihre Leistungsmerkmale an echten Benutzern zu messen. Daher ist es am besten, sie im Labor zu testen, bevor das Feature veröffentlicht wird, um Leistungsrückgänge zu verhindern.

### Im Feld

Auf der anderen Seite ist das Testen im Labor zwar ein angemessener Indikator für die Leistung, spiegelt jedoch nicht unbedingt wider, wie alle Benutzer Ihre Website in freier Wildbahn erleben.

Die Leistung einer Site kann je nach den Gerätefunktionen eines Benutzers und seinen Netzwerkbedingungen stark variieren. Sie kann auch variieren, je nachdem, ob (oder wie) ein Benutzer mit der Seite interagiert.

Außerdem sind Seitenladevorgänge möglicherweise nicht deterministisch. Beispielsweise können Websites, die personalisierte Inhalte oder Anzeigen laden, von Benutzer zu Benutzer sehr unterschiedliche Leistungsmerkmale aufweisen. Ein Labortest wird diese Unterschiede nicht erfassen.

Die einzige Möglichkeit, wirklich zu wissen, wie Ihre Website für Ihre Benutzer funktioniert, besteht darin, ihre Leistung tatsächlich zu messen, während diese Benutzer sie laden und mit ihr interagieren. Diese Art der Messung wird allgemein als [Real User Monitoring](https://en.wikipedia.org/wiki/Real_user_monitoring) – oder kurz RUM – bezeichnet.

## Arten von Metriken

Es gibt mehrere andere Arten von Metriken, die für die Wahrnehmung der Leistung durch Benutzer relevant sind.

- **Wahrgenommene Ladegeschwindigkeit:** Wie schnell eine Seite geladen und alle ihre visuellen Elemente auf dem Bildschirm dargestellt werden kann.
- **Reaktionsfähigkeit beim Laden:** wie schnell eine Seite den erforderlichen JavaScript-Code laden und ausführen kann, damit Komponenten schnell auf Benutzerinteraktionen reagieren können
- **Reaktionszeit zur Laufzeit:** Wie schnell kann die Seite nach dem Laden der Seite auf Benutzerinteraktionen reagieren?
- **Visuelle Stabilität:** Verschieben sich Elemente auf der Seite auf eine Weise, die Benutzer nicht erwarten, und beeinträchtigen sie möglicherweise ihre Interaktionen?
- **Glätte:** Rendern Übergänge und Animationen mit einer konstanten Bildrate und fließen sie fließend von einem Zustand zum nächsten?

Angesichts all der oben genannten Arten von Leistungsmesswerten ist hoffentlich klar, dass kein einzelner Messwert ausreicht, um alle Leistungsmerkmale einer Seite zu erfassen.

## Wichtige zu messende Metriken

- **[First Contentful Paint (FCP)](/fcp/) :** Misst die Zeit vom Beginn des Ladens der Seite bis zur Wiedergabe eines beliebigen Teils des Seiteninhalts auf dem Bildschirm. *( [Labor](#in-the-lab) , [Feld](#in-the-field) )*
- **[Largest Contentful Paint (LCP)](/lcp/) :** misst die Zeit vom Beginn des Ladens der Seite bis zum Rendern des größten Textblocks oder Bildelements auf dem Bildschirm. *( [Labor](#in-the-lab) , [Feld](#in-the-field) )*
- **[First Input Delay (FID)](/fid/) :** misst die Zeit von der ersten Interaktion eines Benutzers mit Ihrer Website (dh wenn er auf einen Link klickt, auf eine Schaltfläche tippt oder ein benutzerdefiniertes, JavaScript-gesteuertes Steuerelement verwendet) bis zu dem Zeitpunkt, zu dem der Browser tatsächlich in der Lage ist. um auf diese Interaktion zu reagieren. *( [Feld](#in-the-field) )*
- **[Time to Interactive (TTI)](/tti/) :** misst die Zeit vom Beginn des Ladens der Seite bis zur visuellen Darstellung, dem Laden der anfänglichen Skripts (sofern vorhanden) und kann zuverlässig schnell auf Benutzereingaben reagieren. *( [Labor](#in-the-lab) )*
- **[Gesamtblockierungszeit (TBT)](/tbt/) :** misst die Gesamtzeit zwischen FCP und TTI, in der der Hauptthread lange genug blockiert war, um die Reaktionsfähigkeit der Eingabe zu verhindern. *( [Labor](#in-the-lab) )*
- **[Kumulative Layoutverschiebung (CLS)](/cls/) :** misst die kumulative Bewertung aller unerwarteten Layoutverschiebungen, die zwischen dem Beginn des Ladens der Seite und dem [Wechsel des Lebenszyklusstatus](https://developers.google.com/web/updates/2018/07/page-lifecycle-api) in ausgeblendet auftreten. *( [Labor](#in-the-lab) , [Feld](#in-the-field) )*

Obwohl diese Liste Metriken enthält, die viele der verschiedenen Aspekte der Leistung messen, die für Benutzer relevant sind, enthält sie nicht alles (zB Reaktionsfähigkeit und Laufruhe zur Laufzeit werden derzeit nicht behandelt).

In einigen Fällen werden neue Metriken eingeführt, um fehlende Bereiche abzudecken, aber in anderen Fällen sind die besten Metriken diejenigen, die speziell auf Ihre Website zugeschnitten sind.

## Benutzerdefinierte Messwerte

Die oben aufgeführten Leistungskennzahlen sind gut, um ein allgemeines Verständnis der Leistungsmerkmale der meisten Websites im Web zu erhalten. Sie sind auch gut geeignet, um gemeinsame Metriken für Websites zu haben, um ihre Leistung mit der ihrer Konkurrenten zu vergleichen.

Es kann jedoch vorkommen, dass eine bestimmte Website in irgendeiner Weise einzigartig ist und zusätzliche Messwerte erforderlich sind, um das vollständige Leistungsbild zu erfassen. Mit der LCP-Metrik soll beispielsweise gemessen werden, wann der Hauptinhalt einer Seite fertig geladen wurde. Es kann jedoch Fälle geben, in denen das größte Element nicht Teil des Hauptinhalts der Seite ist und daher LCP möglicherweise nicht relevant ist.

Um solche Fälle anzugehen, hat die Web Performance Working Group auch standardisierte APIs auf niedrigerer Ebene, die für die Implementierung Ihrer eigenen benutzerdefinierten Metriken nützlich sein können:

- [Nutzer-Timing-API](https://w3c.github.io/user-timing/)
- [API für lange Aufgaben](https://w3c.github.io/longtasks/)
- [Element-Timing-API](https://wicg.github.io/element-timing/)
- [Navigations-Timing-API](https://w3c.github.io/navigation-timing/)
- [Ressourcen-Timing-API](https://w3c.github.io/resource-timing/)
- [Server-Timing](https://w3c.github.io/server-timing/)

Lesen Sie den Leitfaden zu [benutzerdefinierten Messwerten](/custom-metrics/) , um zu erfahren, wie Sie diese APIs verwenden, um die für Ihre Website spezifischen Leistungsmerkmale zu messen.
