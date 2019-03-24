# Transferleistung-LaTeX

Typesetting ist eine Sache für sich. Studenten dazu zu zwingen, das Rad stets
neu zu erfinden, ist eine schlechte Idee. Der folgende Guide richtet sich,
entsprechend, an Studenten, die bisher noch keine Erfahrungen auf diesem Gebiet
angesammelt haben. Einen sehr viel Umfassenderen Ansatz verfolgt TheMegaTB unter
https://github.com/TexNAK/Science-Paper-Template. Dieser Guide entspringt
persönlicher Erfahrung, den Arbeiten meines Bruders sowie den Arbeiten von
FWellers (https://gitlab.com/fwellers/texfornak) und OleKoring
(https://gitlab2.nordakademie.de/OleKoring-I16/LaTeX-Transferleistung/)
Ziel ist es letztlich, Minimalbeispiele für die häufigsten Problemstellungen
bieten zu können und diese übersichtlich aufzubereiten.


Softwarestack: Atom, TeX Live, pdfTex Plan - LaTeX &
Entwicklungsumgebung

### Aussprache: LaTeX: Latech < - 'frech'.

### Installation von Packages
Um Atom zu nutzen, muss nun noch latexmk über den Packagemanager installiert
werden. Das ist in Ordnung, so kann dieser Prozess direkt durchgegangen werden.
TeX Live Manager starten -> unter Treffer -> latexmk
In der Liste suchen, anhaken, unten rechts Installation
Todo: Docker Tutorial

### Lokale Packages
1. Entscheiden, ob das Package für den aktuellen oder Systemweit
installiert werden soll.
2. Pfad finden:
  Aktueller Nutzer: cmd -> kpsewhich -var-value TEXMFHOME
  Systemweit: cmd -> kpsewhich -var-value TEXMFLOCAL
  Falls sich ein Package in beiden Verzeichnissen befindet,
  gewinnt das zuerst gefundene, in der Regel das des aktuellen Nutzers.
  (vgl. https://tex.stackexchange.com/questions/73016/how-do-i-install-an-individual-package-on-a-linux-system)
3. in den Ordner tex gehen.
4. In der Regel -> LaTeX
5. Unzipped Ordner kopieren.
6. cmd -> 'latex <package-name>.ins'
7. cmd -> 'mktexlsr'
In der Regel kommen Packages mit einem readme.md, einfach mit Notepad öffnen
und in der Installationsbeschreibung nachschlagen.

### LaTeX & Entwicklungsumgebung

Das Anfang der 80.-Jahre von Leslie Lamport entwickelte LaTeX (Lamport Tex) ist
eine Erweiterung des ursprünglichen Textsatzsystems TeX. Für LaTeX selbst
existieren ebenfalls zahllose Zusatzprogramme, die von unterschiedlichen Gruppen
zu Distributionen zusammengefasst wurden. Deren Bekannteste MikTeX und TeX Live.
Weiterführend hierzu: https://www.schlosser.info/miktex-vs-texlive/ Im Folgenden
soll die Installation von TeX Live unter Win10 durchexerziert werden.   Da ich
bereits über eine MikTeX Installation verfüge, ist es gut möglich, dass
spezifische Probleme bei mir nicht - oder zusätzlich auftreten.

Weitere Informationen über https://www.latexbuch.de/latex-windows-installieren/

### TeX Live Installation

http://www.tug.org/texlive/ -> download -> install-tl-windows.exe
oder direkt: http://mirror.ctan.org/systems/texlive/tlnet/install-tl-windows.exe
Optional auch als zip verfügbar, das Archiv entpacken und install-tl-windows.bat
ausführen.

Standard-Papierformat: A4
TeXworks wird in dieser Einleitung nicht benötigt, als Editor wird Atom genutzt.
Es ist unbedingt auf eine Stabile Internetverbindung zu achten, da der Setup
bei einem Disconnect komplett abbricht.

Da Tex Live ursprünglich per CD vertrieben wurde (und auch weiterhin wird),
fehlen der Distribution einige grundsätzlich kostenlose Fonts (Schriftarten).
Diese werden im nächsten Schritt nachgeladen.
1. Hierzu install-getnonfreefonts
(http://tug.org/fonts/getnonfreefonts/) herunterladen.
2. Kommandozeile öffnen (win+r: cmd oder win+x->Kommandozeile/Command Prompt)
3. cd '<download-pfad>'
4. texlua install-getnonfreefonts
   getnonfreefonts --sys --all (falls keine Admin-Rechte, statt --sys:--user)
5.

### Atom Installation und Packages

Da mich hässliche Editoren deprimieren (oberflächlich), nutze ich Atom. Atom hat
viele Nachteile, insbesondere Bugs und Performanceprobleme, - ist dafür
allerdings auch wirklich hübsch.

### Das einbinden von Grafiken Installation von Ghostscript

https://www.latexbuch.de/latex-windows-installieren/#x1-70002 (Postscript)

### Hinweise zu Schriftarten

Mit \usepackage{fontspec} können die auf dem PC verwendeten Schriftarten
verwendet werden. \setmainfont{Arial} wählt dann Arial als Schriftart aus. So
kann auch Times New Roman ausgewählt werden.

Alternativ kann auch \usepackage{lmodern} genutzt werden. Damit werden
Schriftarten genutzt, die eigentlich wie Arial und Times New Roman aussehen.
Standardmäßig ist eine Schrift mit Serifen ausgewählt.
\renewcommand*\familydefault{\sfdefault} setzt dann eine serifenlose Schriftart.

### Hinweise zum Zitieren

\usepackage[backend=biber, style=apa, citestyle=authoryear-ibid]{biblatex}  Die
Option style setzt den Stil des Literaturverzeichnisses, citestlye setzt den
Stil bei Zitaten.

Zitiert werden kann dann zum Beispiel mit \cite{bibid} oder mit
\footcite{bibid}. Wenn noch ein Vgl. davor und eine Seitenangabe dahinter soll
geht das mit \cite[Vgl.][150]{bibid}.

Dokumentation Biblatex:
https://mirror.hmc.edu/ctan/info/translations/biblatex/de/biblatex-de-Benutzerhandbuch.pdf

### Hinweise für Tabellen

Um Tabellen optimal zu nutzen, muss eine normale "table"-Umgebung für caption
und label erstellt werden. In diese kommt dann eine "tabularx"-Umgebung, dessen
Breite (bsp. \linewidth) und Zellenausrichtung (X oder Y) angegeben werden kann.
Mit \toprule, \midrule und \bottomrule zieht man horizontale Linien.

Bsp.:

\begin{table}[!htb] \begin{tabularx}{\linewidth}{@{}XX@{}} \toprule
\textbf{Überschrift 1} & \textbf{Überschrift 2} \\ \midrule Punkt 1 & Punkt 2 \\
\bottomrule \end{tabularx} \caption{Testüberschrift} \label{Testlabel}
\end{table}

### Absätze

Mit \par können Absätze eingefügt werden.

\setlength{\parindent}{0em} formatiert die Einrückung der nächsten Zeile.

\setlength{\parskip}{0.5em} formatiert den Abstand zur nächsten Zeile.

### Fragen und Verbesserungen

Schreibt mir bei Fragen und Verbesserungsvorschlägen einfach an meine NAK Mail.
