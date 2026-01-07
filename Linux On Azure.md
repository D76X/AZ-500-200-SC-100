# Linux On Azure

---

## [LinuxOnAzure](https://github.com/tomwechsler/LinuxOnAzure) \- [Tom Wecshler](https://github.com/tomwechsler?page=3&tab=repositories) \- [YouTube](https://www.youtube.com/@tomvideo2brain)

### Ressourcen 

[Deploy and administer Linux virtual machines on Azure-**Microsoft Learn-Module**](https://learn.microsoft.com/en-us/training/paths/deploy-administer-linux-virtual-machines-azure/) 

[LinuxOnAzure GitHub Repo-Tom Wechler](https://github.com/tomwechsler/LinuxOnAzure)  
[Azure Tip: Linux on Azure \- Folge 2 \- Mit SSH (Windows Terminal u. WSL) eine Remotesitzung erstellen](https://www.youtube.com/watch?v=ckhwvQezBBU)  
[Bytesource \- Wir sind Ihr DevOps Experte](https://bytesource.net/de/devops/?ppc_keyword=&gclid=CjwKCAiA_vKeBhAdEiwAFb_nrae1f9jhSqJQDwO3_9CX1bTbXyXt5egpGzDQ6_3Y4_hx1A5xuD75fRoC8QgQAvD_BwE) 

[Azure\_Cloud\_Shell](https://github.com/tomwechsler/Azure_Cloud_Shell)

---

## [LinuxOnAzure](https://github.com/tomwechsler/LinuxOnAzure) \- [Tom Wecshler](https://github.com/tomwechsler?page=3&tab=repositories) \- [YouTube](https://www.youtube.com/@tomvideo2brain)

### Ressourcen 

* #### [LinuxOnAzure GitHub Repo](https://github.com/tomwechsler/LinuxOnAzure)

* #### [01\_Überblick\_Hardware\_und\_virtuellen\_Verzeichnissen.txt](https://github.com/tomwechsler/LinuxOnAzure/blob/master/01_%C3%9Cberblick_Hardware_und_virtuellen_Verzeichnissen.txt)  

[01\. Windows und Linux Tip: Installation vom Windows Subsystem für Linux](https://www.youtube.com/watch?v=zCFq5bluhfc)   
[02\. Microsoft Tip: Windows Subsystem for Linux (WSL2) \- Konfiguration erweiterter Einstellungen](https://www.youtube.com/watch?v=N8DtdSxZFAw)  
[03\. Microsoft Tip: Windows Subsystem for Linux (WSL2) und Visual Studio Code](https://www.youtube.com/watch?v=FK1xzerf-_s)   
[04\. Microsoft Tip: Windows Subsystem for Linux (WSL2) und Notepad++](https://www.youtube.com/watch?v=bkoz_WblFew)

    
---

### [Folge 10 \- Teil 2 \- Dateisystem erstellen und mounten](https://www.youtube.com/watch?v=F2QwXICSDhA&list=PLi0MTIjZai_yi1NkwNt4YBN3mdGSlG6TS&index=11)

**Zusammenfassung**

* Wie man ein Dateisystem **anlegt bei einer** Partition  
* Wie man mit **mkfs** ein Dateisystem auf eine Partition **erzeugen** / **einsetzen** kann      
* Wie man ein Verzeichnis machen  
* Wie man den Befehl **man** nützt  
* Wie man mit de**m** Befehl **mkdir** ein neue**n [Ordner](https://www.collinsdictionary.com/dictionary/german-english/ordner) anlegen** kann  
* Wie man eine Partition **(auf den [Laufwerk](https://www.collinsdictionary.com/dictionary/german-english/laufwerk)) mounten**  
* Wie man die Linuxbefehlen **lsblk \-f** und **mkfs** und **man** nützen kann  
* Wie man de**n** Befehl **mount** einsetzt somit alle Mounts auf das System **aufgelistet werden**   
* Wie man de**n** Befehl **umount** einsetzt um **ein Mount** (n) **auf**zu**heben.**  
* Wie kann man mit de**r** **fstab** Datei einen Mount permanent machen kann.  
* Wie kann man mit fastab ein nicht-permanent mount und auch ein permanent Mount machen kann

**Herzlich wilkommen** **in der heutigen Folge (f) geht es darum**, dass wir mit unserer Partition **weiter arbeiten**. **In der letzte Folge** haben wir eine Partition angelegt, **in der** heutige**n** [Session](https://www.collinsdictionary.com/dictionary/german-english/session) (f) **geht es darum**, dass wir ein Dateisystem **anlegen bei dieser** Partition und dass wir dann diese Partition **mounten.** Lassen wir uns gleich beginnen.

Ich habe bereits **eine SSH Verbindung zu unserem Linuxsystem aufgebaut** **mit lsblk \-f ** können wir die Block Devices **aufrufen** und wir haben hier unsere Festpaltte und **daran / darin enthalten** unsere Partition sdc1. **Wegen** **\-f**  de**r** [**Option**](https://www.collinsdictionary.com/dictionary/german-english/option) **(f) erhalten** wir auch **das Dateisystem** aber nun hat die Partition **noch kein** ein Dateisystem weil das wir **noch nicht** konfiguriert haben.

**man mkfs**

**mkfs** (+ zweimal die **Tabulator**taste)

**mkfs.xfs /dev/sdc1 \> mkfs \-t xfs /dev/sdc1 \> lsblk \-f \> mkdir /demo \> ls / \> mount /dev/sdc1 /dem \> mount \> umount /demo \>** 

[**vollbringen**](https://www.collinsdictionary.com/dictionary/german-english/vollbringen) **(=ausführen) \>** dann is der Mount vollbracht**, ganz unten** werde den Mount **aufgelistet, den** Mount wurde **durchgeführt**, den Mount ist **vorhanden,** einen Mount (nicht-)**permanent durchführen**, die Partition wurde gemountet in das Verzeichnis /demo, wenn wir das System neue starten **ist** diesen Mount **wieder weg,** den Mount **[aufheben](https://www.collinsdictionary.com/dictionary/german-english/aufheben)** (von Boden),   
---

### [Folge 10 \- Teil 1- Mit gdisk Partitionen erstellen](https://www.youtube.com/watch?v=_RSgTGgW-KA)

**Zusammenfassung**

* Wie man mit gDISK [**eine Partition**](https://www.collinsdictionary.com/dictionary/german-english/partition) [**anlegen**](https://www.collinsdictionary.com/dictionary/german-english/anlegen) (=**herstellen**) kann.    
* Wie man mit gDisk ein**e Festplatte** [**partitioniert**](https://www.dwds.de/wb/partitionieren) und eine Partition **auf den [Laufwerk](https://www.collinsdictionary.com/dictionary/german-english/laufwerk)** **angelegen lässt**.  
* Wie man eine**m** RHEL VM ein**e zusätzliche** Disk [**hinzufüget**](https://www.collinsdictionary.com/dictionary/german-english/hinzufugen)   
* Wie man **mit** de**m** **Befehl** **cat /proc/partitions** oder **lsblk** die, **auf** unsere**s** [**System**](https://www.collinsdictionary.com/dictionary/german-english/system) (n) [**anleg**](https://www.collinsdictionary.com/dictionary/german-english/anlegen)**te (bestehende)** [**Partition**](https://www.collinsdictionary.com/dictionary/german-english/partition)en, **aufrufen** kann   
* Wie man es [**herausfindet**](https://www.collinsdictionary.com/dictionary/german-english/herausfinden) **wo** eine Partition **gemountet** wird d.h. **in** welche**s** **Verzeichnis gemountet** wird.  
* Wie man eine Partition [**einschränken**](https://www.collinsdictionary.com/dictionary/german-english/einschranken) und sie  **auf** den Disk **geschrieben lassen**.

 

**a[nlegen](https://www.collinsdictionary.com/dictionary/german-english/anlegen)** (Datei, Vorräte, Garten, Geländde, [**Schaubild**](https://www.collinsdictionary.com/dictionary/german-english/schaubild) **(n)**) |=\[ [**investieren**](https://www.collinsdictionary.com/dictionary/german-english/investieren) **| ausgeben\] (Kapital, Geld)**  
**sich a[nlegen](https://www.collinsdictionary.com/dictionary/german-english/anlegen) auf** etwas \- du **legst** **es** wohl **auf** einen Streit mit mir\!

**Herzlich wilkommen** zu einen neuen Linux On Azure Tip. **In den heutigen Folge geht es darum**, dass wir mit GDISK [**Partitionen**](https://www.collinsdictionary.com/dictionary/german-english/partition) [**anlegen**](https://www.collinsdictionary.com/dictionary/german-english/anlegen). Ich habe bereits eine Verbindung aufgebaut zu meinen linux-System welche im Azure ausgeführt wird. Schauen wir zuerst mal welche Partitionen, **auf** unsere**s** **System (n)**, bereits schon gibt **idem** wir **mit** de**m** **Befehl** cat /proc/partitions **rufen** sie **auf**. Normalerweise würde man finden, dass die **Festplatten** **in** viele**n** Partitione**n** (akk) [**unterteilt**](https://www.collinsdictionary.com/dictionary/german-english/unterteilen) **sein.**

cat /proc/partitions

Es zeigt die **verschiedenen [Partition](https://www.collinsdictionary.com/dictionary/german-english/partition)en** zum Beispiel sda, sda1, sdb, sdb1, dm-0, dm-1 und so weiter. Jetzt können wir den Bildschirmsinhalt aufräumen **mit** CTRL+L und dann können wir aber auch mit **lsblk** arbeiten, dann **erhalten** wir **ebenfalls** [**die Auflistung**](https://www.collinsdictionary.com/dictionary/german-english/auflistung)**.** 

lsblk

Mit diesem Befehl kann man sehen welche [**Partition**](https://www.collinsdictionary.com/dictionary/german-english/partition) **auf** welche [**Festplatten**](https://www.collinsdictionary.com/dictionary/german-english/festplatte) **(f)** und welche**s** **Verzeichnis** **gemountet** werden. Wir sehen **es bibt zwei** [**Festplatten**](https://www.collinsdictionary.com/dictionary/german-english/festplatte) und **es gibt** schon auch einige [**Partitionen**](https://www.collinsdictionary.com/dictionary/german-english/partition). Ich möchte **allerdings** nicht mit de**r bestehenden** [**Festplatten**](https://www.collinsdictionary.com/dictionary/german-english/festplatte) [**partitionieren**](https://www.dwds.de/wb/partitionieren) **sondern** ich möchte **mit** ein**er** neue**n** **Festplatte (f)** arbeiten **d.h. Also** wir müssen **zuert** unsere**m System** eine neue Festplatte [**zufügen**](https://www.collinsdictionary.com/dictionary/german-english/zufugen) **\[**\+dat**\].**

**Das System** welch**e** ich **verwende** heißt [**RHEL.** **RHEL**](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux) ist die **Abkuzung für..	In [das](https://www.collinsdictionary.com/dictionary/german-english/portal)** [Azure Portal](https://www.collinsdictionary.com/dictionary/german-english/portal) navigiere ich zu de**m Disks** und wir werden direkt hier eine **zusätsliche** Disk [**hinzufügen**](https://www.collinsdictionary.com/dictionary/german-english/hinzufugen) **indem** wir Create and Attach **verwenden**. Jetzt **geben** wir einen Name **an** usw. Es **genügt** ein ganz standard HDD weil **für das Partitioniere** brauchen wir kein**e** groß**e** [leistungsfähig**e**](https://www.dwds.de/wb/leistungsf%C3%A4hig) [Festplatte](https://www.collinsdictionary.com/dictionary/german-english/festplatte) (f) so dass ich kann es **bei** STANDARD **belassen** und shließlich die Große 16 MB **ist in Ordnung**.

Es ist ganz wichtig wenn wir ein neue**n Disc** bzw. eine neue Festplatte **hinzufügen dass** [**das Betriebssystem**](https://www.collinsdictionary.com/dictionary/german-english/betriebssystem) diese Information **bekommt** **darum** werde ich schnell diese VM **neu starten damit** das Betriebssystem**, in diesemFall,** RHEL die neue Discsinformationen **sammeln** kann **damit** wir gleich die Partitionen **anlegen** können.

Ich geht es zurück zu die SSH Session und dann werden wir **lsblk** noch mal nutzen **damit**  die neue Festplatte gezeigt wird. **Übrigens** wenn sie auch [**das Dateisystem**](https://www.collinsdictionary.com/dictionary/german-english/dateisystem) **von** de**n bestehenden** Partitionen sehen **wollen** dann verwendet man den Befehl **lsblk \-f** .

**lsblk \-f** 

D[**as Dateisystem**](https://www.collinsdictionary.com/dictionary/german-english/dateisystem) **ext4** aber auch [xsf](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/storage_administration_guide/ch-xfs), vfat sind alle **weit verbreitet** und **häufig eingesetzt.** Nun **geht es darum, dass** wir eine Partition anlegen. Es gibt **verschiedenen** **Werkzeuge** zum Beispiel sie können mit **fdisk** arbeiten um Partitionen an**zu**legen ein**e** ander**e [Option](https://www.collinsdictionary.com/dictionary/german-english/option) (f) ist gdisk.**

**sudo gdisk** /dev/sdc   
oder  
**sudo su \-**  
**gdisk** /dev/sdc 

**Im obigen Befehl** es ist ganz wichtig, dass **sdc** ist der Name der Festplatte die wir **partitionieren** möchte. Wir möchten ganz sicher **nicht** eine **bestehende Festplatte** [**aus Versehen**](https://www.collinsdictionary.com/dictionary/german-english/versehen) (=[**versehentlich**](https://www.collinsdictionary.com/dictionary/german-english/versehentlich) | [**irrtümlich**](https://www.collinsdictionary.com/dictionary/german-english/irrtumlich) ) [**formatieren**](https://www.collinsdictionary.com/dictionary/german-english/formatieren). Das könte sehr **negativ auswirken**. Mit  gdisk können wir ganz **gemütlich** mit dem **Fragezeichen ?** arbeiten **damit** wir die Hilfe **erhalten**.

Wir sehen bereits, dass wir **nicht** mit MBR \[Master Boot Record\] arbeiten möchten, weil wir können nicht so viele Petitionen anlegen **sondern** wir arbeiten mit GPT \[**GUID** Partition Table\], weil **GPT ünterstützt** mehrer**e Partitionen bis zu 128** könnten wir hier **herstellen (=anlegen)**.

Wir gehen weiter un die erste Partition **anlegen**. wir können **bis zu** **128** Partitionen **erstellen** aber ich werde nun **das Default nehmen** d.h. **1** . also wir beginnen hier **mit den Standardwert 1** für der Nummer von Partitionen wir erstellen wollen. **Jetzt müssen wir die [Größe](https://www.collinsdictionary.com/dictionary/german-english/grosse) des** erst**en [Sektor](https://www.collinsdictionary.com/dictionary/german-english/sektor) (m) angeben.**

**Die [Größe](https://www.collinsdictionary.com/dictionary/german-english/grosse) des** erst**en [Sektor](https://www.collinsdictionary.com/dictionary/german-english/sektor)** wird **vorgeschlagen** zu 2048 und das [**bellasse**](https://www.collinsdictionary.com/dictionary/german-english/belassen) ich, das [**übernehme**](https://www.collinsdictionary.com/dictionary/german-english/ubernehmen) (=**annehmen, akzeptieren**) ich, das ist [**soweit**](https://www.collinsdictionary.com/dictionary/german-english/soweit) in Ordnung. Aber jetzt möchte ich nicht **mit** dem **letzten** [**Sektor**](https://www.collinsdictionary.com/dictionary/german-english/sektor) **(m)** **arbeiten** weil dann wurde **mir** eine Partition angelegt **über** **die gesamte Festplatte**. Nein, ich möchte das etwas [**einschränken**](https://www.collinsdictionary.com/dictionary/german-english/einschranken)**.** Ich möchte zuerst einmal eine Partition **anlegen in der Größe von** 4 GB (+4G) so **erstellen** wir **eine Partition 4 GB [groß](https://www.collinsdictionary.com/dictionary/german-english/gross_1)**.

Jetzt **werden wir gefragt** welche**s** Label wollen wir [**hinzufügen**](https://www.collinsdictionary.com/dictionary/german-english/hinzufugen) **(=[addieren](https://www.collinsdictionary.com/dictionary/german-english/addieren)).** Schauen wir mal diese Label genauer an **indem** wir diese größes L verwenden**.** Es zeigt die verschiedenen Labels und das System hat **uns** doch **[vorgeschlagen](https://www.collinsdictionary.com/dictionary/german-english/vorschlagen),** wir sollen **das Label** 8300 **verwenden** (Linux filesystem) **ich denke das macht Sinn.**

**Wir könnten theoretisch** auch ein andere**s** Label **auswählen** aber **das macht kein Sinnes es ist sicherlich sinvoll** wenn wir **eine Partition anlegen** **und** dann später [**formatieren**](https://www.collinsdictionary.com/dictionary/german-english/formatieren) mit EXT4 mit XFS, dass sie auch das Label 8300 **bekommt**., also geben wir das code an 8300\.

Jetzt immer mehr **ein [Fragezeichen (n)](https://www.collinsdictionary.com/dictionary/german-english/fragezeichen)** **damit** wir den näschte Befhel zeigen können. Beispielsweise das P, es **steht für** PRINT Partition Table also geben wir P an und drücken die Entertaste und  **in der Tat** haben wir hier unsere Partition. Wie können wir diese**s Werkzeug** **korrekt verlassen (**\=EXIT**) damit** diese Partition **geschrieben wird?**

Das steht hier das klein **w** \[WRITE TABLE TO DISK AND EXIT\] also wenn wir die Partition **nicht** so **verlassen** wird die Partition **nicht geschrieben\!**

**Darum** verwenden wir das klein **w**, [drücken](https://www.collinsdictionary.com/dictionary/german-english/drucken_2) wir die Entertaste, wollen Sie das ganze **übernehmen (=akzeptieren)** ? Ja, wir geben das Y an und jetzt **wird diese Partition auf den Disk geschrieben**. Nun verwenden wir **lsblk \-f** und wir sehen was wir gemacht haben. Wir haben eine Partition angelegt **auf den [Laufwerk](https://www.collinsdictionary.com/dictionary/german-english/laufwerk)** und mit de**r [Option](https://www.collinsdictionary.com/dictionary/german-english/option) (f)** **\-f** sehen wir auch das die neue Partition **noch** **kein** Dateisystem hat und auch **noch nicht** gemountet wurde.

 

---

### [Folge 9 \- Mit sed (Stream Editor) Text-Datenströme bearbeiten](https://www.youtube.com/watch?v=2udv6JCQp1Y)

[SED a stream editor](https://www.gnu.org/software/sed/manual/sed.html) | [Ubuntu \- sed \- stream editor](https://manpages.ubuntu.com/manpages/jammy/man1/sed.1plan9.html) 

**Zusammenfassung**

Wie man mit dem Werkzueg  Stream Edit SED Textdateien editieren kann.   
**Wie funktioniert** SED?  
Wie mann SED **verwenden** um Konfiguration**sdatei** **an**zu**passen.**  
   
In den heutig**e** [**Session**](https://www.collinsdictionary.com/dictionary/german-english/session) (f) möchte ich ihnen den Stream Edit SED **vorstellen**. Wie sie mit dem Werkzeug SET Textdateien editieren können. Ich habe bereiits eine Verbindung aufgebaut **zu** eine**m** **linux-System.** Ich **verwende dazu** das Windows Terminal. Wie sie eine Verbindung aufbauen [**schlussendlich**](https://www.collinsdictionary.com/dictionary/german-english/schlussendlich) ist **selbsverständlich** ihnen [**überlassen**](https://www.collinsdictionary.com/dictionary/german-english/uberlassen). Das Windows Terminal bietet sich in meinen Fall an um direkt mit einem linux-System zu arbeiten zu können.

**Wie funktioniert** SED? SED das Stream Editor **hat die Möglichkeit das Wörter setzen werden können** und das beginnt [**folgendermaßen**](https://www.collinsdictionary.com/dictionary/german-english/folgendermassen) **(=wie folgt).** Wir brauchen **dazu** ein**er** spezifische **Syntaxt**. Wir verwenden das Folgendes.

sed ‘s/dieses/durchdas/g’ myfile.txt

s  hier **steht für** **substitute**, also **ersetzen**. /dieses/durchdas bedeutet dass, wir möchen das Wort ‘dieses’ mit das Wort ‘durchdas’ **ersetzen und** /g **steht für global**, also für alle in diese Textdatei und ich shliese das ganze mit **der Hochkomma**. Das **wäre der Syntaxt** wie eben dies**e [Substitution](https://www.collinsdictionary.com/dictionary/german-english/substitution)** **funktioniert**. 

sed ‘s/youtube/tom/g’ myfile.txt

Das ist jetzt nur ein Teil was SED alles kann aber es ist ein Beispiel Ich werde ihnen später **mit** ein**er** richtig**en [Datei](https://www.collinsdictionary.com/dictionary/german-english/datei)** (f) zweigen **wo** das SED eben **Sinn machen kann**. Nun lassen wir uns etwas arbeiten. Die letzte Beispiel hat nicht ganz funktioniert wie wir gehofft haben weil nur die kleine yuotube Wort ersetzt wurde. **Keine Panik** **das können wir anpassen**\! **Pfeiltaste nach oben** um den letzten Befehl zu **widerholen** und jetzt verwenden den folgenden Befehl.

sed ‘s/youtube/tom/g’ | sed ‘s/Youtube/Tom/g’ myfile.txt

**Ich glaube sie haben die Idee erhalten** aber sie haben auch gesehen wir muss**t**en mit de**m** pipe-[Symbol](https://www.collinsdictionary.com/dictionary/german-english/symbol) (m) arbeiten **damit** i**m** erste**n** Teil das **klein geschribenen** youtube ersetzen werden konnte und i**m** zweite**n** Teil das **groß geschriebenen** Youtube. Das können wir noch bessern.

Zuerst einmal de**n Bildschirminhalt etwas aufräumen mit Control+L**, die Linie habe ich entfernt **mit Control+U**. 

sed ‘s/\[Yy\]outube/tom/g’’ myfile.txt

Das ist **ein weiteres Beispiel** wie sie mit SED arbeiten können. Sie haben jetzt gesehen wie **mit dem Aufbau der Klammer**  \[Yy\] es gibt wirklig **enorm viel Möglichkeiten**. **Jetzt bar wo macht das Ganze Sinn? Wo macht es Sinn** mit SED zu arbeiten. Stellen sie einmal vor sie müssen eine **Konfigurationsdatei anpassen** beispielsweise die Apache **Konfigurationsdatei** und sie müssen de**n** **Wert** localhost ersetzen **in** d**er** gesamte**n** **Datei**. Ja ich gaube dass, **es macht keien Sinn** dass, sie die **Datei aufrufen** mit der vim-Editor und dann **überall nach** localhost suchen und dann **manuell eintippen** der neue Name **astelle von** localhost **das macht tatsäsclich keinen Sinn**\!

sich **als** root anmelden \> sich **als** root angemeldet sein  
eine Datei mit dem PAGER less sich **anshauen**  
**einen** Wort in [der Kommentar](https://www.collinsdictionary.com/dictionary/german-english/kommentar) **[aufsuchen](https://www.collinsdictionary.com/dictionary/german-english/aufsuchen)** \> **die Kommentare** beginnen mit de**m** Hastag   
etwas mit dem Hashtag **auskommentieren**  
eine**n** Wert (m) **setzen**

Ich möchte ihnen noch ein weiter**es** Beispiel zeigen. Zuerst einmal werde ich **als** root (sudo) **anmelden**. Jetzt bin ich **als** root **angemeldet**. Jetzt schauen wir uns einmal eine Detei an **und zwar** mit dem PAGER less wir navigieren in den Verzeichnis etc und wir **suchen** di Detei **auf** ~~nach~~ nsswitch.conf. In diese Detei gibt es viel **[Kommentare](https://www.collinsdictionary.com/dictionary/german-english/kommentar)**. \[[der Kommentar](https://www.collinsdictionary.com/dictionary/german-english/kommentar)\] Die Kommentare beginnen mit dem HASHTAG. Wir **navigieren** dann **nach unten** und **seitetenweise** mit de**r Leerschlagtaste \[[der Leerschlag](https://www.collinsdictionary.com/dictionary/german-english/leerschlag)\] \[[die Taste](https://www.collinsdictionary.com/dictionary/german-english/taste)\]**. Wir sehen es gibt einige **Werte die sind gesetzt** es gibt aber einige Werte die sind **auskommentiert** mit de**m HASHTAG.** 

sudo su \-   
less /etc/nsswitch.conf

Wir könnten das Ganze [**untersuchen**](https://www.collinsdictionary.com/dictionary/german-english/untersuchen) **(=[inspizieren](https://www.collinsdictionary.com/dictionary/german-english/inspizieren), [prüfen](https://www.collinsdictionary.com/dictionary/german-english/prufen)) mit foldendem Kommando**. Zuerst einmal verlassen wir den Pager mit dem Taste Q\[UIT\] und jetzt **verwende ich das Kommando** wo steht für wc WORD COUNT.

wc \-l /etc/nsswitch.conf  
sed \-i.$(date \+%F) ‘/^\#/d;/^$/d’ nsswitch.conf

Wir **ersetzen** hier alle **Kommentare** und **Leerzeichen** aber wir **erstellen gleichzeitig eine Backup von** diese Datei nsswitch.conf dass wenn wir etwas **rückgängig machen müssen** shet uns das [**jederzeit**](https://www.collinsdictionary.com/dictionary/german-english/jederzeit) zu Verfügung. Starten wir **beziehungsweise** **führen** wir den Befehl **aus** und jetzt haben wir das Ganze **ersetzt**. Jetzt **schauen** wir **uns** mit LESS diese Datei nsswitch.conf wieder **an.** Wir haben sie gesehen, jetzt **sieht sie** **viel schlanker aus als** **voher**.  

**Ich gebe ihnen absolut recht**, **macht es Sinn** Kommentare, **Beschreibungen, [Hilfestellungen](https://www.collinsdictionary.com/dictionary/german-english/hilfestellung)** [zu **entfernen**? **Nein, wahrscheinlich nicht,** **aber** es zight ihnen die Power](https://www.collinsdictionary.com/dictionary/german-english/hilfestellung) wie man SED **einsetzen** kann. Es ist wirklich **ein mächtiges Werkzeug** und es kann ihnen wirklich helfen es  **darum geht Konfigurationsdateien an**zu**passen** **damit** sie nicht [**manuell**](https://www.collinsdictionary.com/dictionary/german-english/manuell) **Wörter** ersetzen müssen.

wc \-l /etc/nsswitch.conf ls   
\-l nss\*

**Schauen** wir un**s** nochmal **an,** wie jetzt da**s [Resultat](https://www.collinsdictionary.com/dictionary/german-english/resultat)** **aussieht.** **Von** 64 Zeilen **sind** wir jetzt **runter** **auf** 15 Zeilen. Mit \-l nss\* zeige ich ihnen, dass **tatsächlich** eine Backupsdatei **angelegt wurde**, die mit dem anschließenden .datum **gezeigt** wird. Ich hoffe ich **konnte** inhen eine**n** kleine**n Eindruck** **geben** wie sie mit SED arbeiten können um eine **Konfigurationsdatei** beispielsweise **für ihre Bedürfnisse anpassen** zu können.  
---

### [Folge 8 \- Das Backup für eine VM (virtual Machine) einrichten](https://www.youtube.com/watch?v=KCTmAEsQK0A&t=1seBM)

**Zusammenfassung**

Wie man das Backup eine linux Machine **[einrichtet](https://www.collinsdictionary.com/dictionary/german-english/einrichten)** und **konfiguriert.**  
Wie man einen Backup ein**er** virtual Maschine **herstellen**.  
Wie man sich eine  Recovery Service Vault **herestellet**.

Lassen wir uns doch gleich beginnen. Zuerst einmal **navigie** ich **zu** Virtual Machines wo man eine [**Übersicht**](https://www.collinsdictionary.com/dictionary/german-english/ubersicht) **bekommt.** Ich möchte nun **ein Backup herstellen**. 

Navigiere ich dann ins Details dieser VM und **ein wenig unten** wo wir finden **die Sektion** Operations und **darin enthalten** die Option Backup wo man das Backup **konfigurieren** kann. Für das Backup brauchen wir **im Prinzip** **zwei Komponenten.**

1. Eine [**sogenannte**](https://www.collinsdictionary.com/dictionary/german-english/sogenannt) Recovery Service Vault  
2. Eine Backup Policy

Sie können **beiden~~(s?)~~** **direkt** hier in diese Blade **herstellen** oder sie können **einzel** herstellen und ich möchte ihnen zeigen wie das funktioniert.

**Navigiere** ich **zurück** **zu** Home und dann **wähle** ich hier **im Suchfeld** aus Backup **schlicht und einfach** und dann wird uns die Recovery Service Vault **vorgeschalgen.** Jetzt **herestellen** wir **gemeinsam** eine  Recovery Service Vault. Es gibt **bereits einen** aber ich möchte eine zusätzlichen **herstellen**. Ich **wähle** doch ADD **aus** und jetzt **startet das neue** Blade und wir können **mit** de**r Konfiguration** beginnen.

* **über** das gesamte Portale [**hinweg**](https://www.collinsdictionary.com/dictionary/german-english/hinweg)  
* de**m** Recovery Service Vault Tags **zuweisen**.   
* eine [**Validierung**](https://www.collinsdictionary.com/dictionary/german-english/validierung) **durchführen (**z.B. von Dokument**)**  
* ein**e Meldung** **erhalten**  
* Wichtige **/ zusäzliche Informationen erhalten**  
* **die [Replikation](https://www.dwds.de/wb/Replikation)** \= die Bildung einer **exakten Kopie von**.. **(Verdoppelung** des genetischen Material**) \> [replizieren](https://www.dwds.de/wb/replizieren) (** jdn **gesetzlich** replizieren )  
* **\=\! [die Replik](https://www.collinsdictionary.com/dictionary/german-english/replik) \= [Entgegnung, Erwiderung](https://www.dwds.de/wb/Replik)** \= Antwort **\>** in Erwiderung Ihres Schreibes vo**m**  
* Eine **Policy [erstellen](https://www.collinsdictionary.com/dictionary/german-english/erstellen)**   (= errichten, bauen \> Datei) **|**   
* eine **Aufbewarungsrichtlinie erstellen**  
  [**herstellen**](https://www.collinsdictionary.com/dictionary/german-english/herstellen) **(= [erzeugen](https://www.collinsdictionary.com/dictionary/german-english/erzeugen)** \> Wein, Butter, Produkt, Mistrauen, Spannung, Angst, **Kind)**  
* [**die Häufigkeit**](https://www.collinsdictionary.com/dictionary/german-english/haufigkeit) de**s** Bakup**s \> [die Häufigkeit](https://www.collinsdictionary.com/dictionary/german-english/haufigkeit) der** Policy  
* **die** **Zeitzone [anpassen](https://www.collinsdictionary.com/dictionary/german-english/anpassen)**  
* Wie lange sollen die **Datei [beibehalten](https://www.collinsdictionary.com/dictionary/german-english/beibehalten) werden**? (Bräuche, Regelung)  
* [**Standardmäßig**](https://www.dwds.de/wb/standardm%C3%A4%C3%9Fig) (=**serienmäßig**) werden diese Snapshots zwei Tage [**zurückgehalten**](https://www.collinsdictionary.com/dictionary/german-english/zuruckhalten)  
* Die Konfiguration unsere Wünschen [**anpassen**](https://www.collinsdictionary.com/dictionary/german-english/anpassen)  
* eine [Option](https://www.collinsdictionary.com/dictionary/german-english/option) (f) **aktivieren** und die **weitere Konfiguration durchführen**  
* Sie können diesen **Richtlinien [anpassen](https://www.collinsdictionary.com/dictionary/german-english/anpassen)** ganz **für** ihre [**Bedürfnisse**](https://www.collinsdictionary.com/dictionary/german-english/bedurfnis) ([**das Beürfniss**](https://www.collinsdictionary.com/dictionary/german-english/bedurfnis))  
* das Backup [**einrichten**](https://www.collinsdictionary.com/dictionary/german-english/einrichten)  
* **die Schaltfläche** **Enable Backup** [**klicken**](https://www.collinsdictionary.com/dictionary/german-english/klicken) **\> über** die Schaltfläche **Enable Backup** [**klicken**](https://www.collinsdictionary.com/dictionary/german-english/klicken)

Der Name de**s** Recovery Service Vault muss **eindeutig** sein **über** das gesamte Portale [**hinweg**](https://www.collinsdictionary.com/dictionary/german-english/hinweg)**.** Es geht weiter zu den Tags wo man dem Recovery Service Vault Tags **zuweisen kann**. Dann wählen wir Review und **es wird eine Validierung duchgeführt** und wir **erhalten eine Meldung**, dass es wird so und so konfiguriert. Das sihet jetzt in Ordnung **darum** wählen wir jetzt Create aus.

Diese **Bereitstellung** dauert nur ein paar Sekunden **nicht allzu lange** und sie sehen es ist **bereits abgeschlossen.** Navigiere ich jetzt zu Resource und wir sind jetzt hier in **Details von** unsere**m** Recovery Service Vault wo man **erhaltet** zuerst einmal **viele zusätzliche Informationen**.Wir können **direkt** ein Backup **erstellen** **indem** wir hier **in** dies**e Schaltfläche klicken** oder wir können hier mit ein**er** [**Replikation**](https://www.dwds.de/wb/Replikation) arbeiten das ist **ebenfalls möglich**.

Ich navigiere jetzt ein wenig nach unten und wir sehen hier **die Sektion** Manage und dann **unter anderem** Backup Policies hier ist ein standard Policy **vorhanded** die Default Policy **für** Azure VMs und dann auch ein Policy for Azure SQL Server in Azure VMs. Ich möchte jetzt **nicht** **mit** de**m** standard Policy arbeiten **sondern** ich möchte **eine eigene** Policy **herstellen darum** wähle ich Add **aus.**

Jetzt müssen wir den Policytype **bestimmen d.h.** **In unseren Fall** es ist eine virtuelle Machine **darum wähle** Azure VM **aus**. Nun startet das neue Blade und hier können wir jetzt unsere Policy **herstellen**. Dann [**die Häufigkeit**](https://www.collinsdictionary.com/dictionary/german-english/haufigkeit)**, täglich** oder **wochentlich** dann die **Startzeit** und **vielleicht keine Amtszeit**..

Ich möchte das Backup **am Abend** **herstellen** und ich muss hier auch **die** **Zeitzone [anpassen](https://www.collinsdictionary.com/dictionary/german-english/anpassen)**. Wir können hier auch **entscheiden** wie lange sollen die Intsant Recovery Snapshots **beibehalten** werden. [**Standardmäßig**](https://www.dwds.de/wb/standardm%C3%A4%C3%9Fig) (=**serienmäßig**) \[by default\] werden diese Snapshots zwei Tage [**zurückgehalten**](https://www.collinsdictionary.com/dictionary/german-english/zuruckhalten)**.** Sie können das **wiederum [anpassen](https://www.collinsdictionary.com/dictionary/german-english/anpassen). Übrigens** wenn sie mehr **Informationen möchten**, navigieren sie zu diesen kleinen \<i\> dann **erhalten** sie **zusätzlichen Informationen.**

Jetzt geht es weiter..

Wir haben hier den Retention Range wie lange soll das Backup **grundsätzlich** **aufbewahrt werden**. Dann könne wir **aber auch** eine **Aufbewarungsrichtlinie erstellen** für das w**ö**chentliche, m**o**natenliche und **sogar** für das j**ä**rliche Backup sie müssen ganz einfach hier diese [Option](https://www.collinsdictionary.com/dictionary/german-english/option) (f) **aktivieren** und jetzt können wir die **weitere Konfiguration durchführen**. Sie können diesen **Richtlinien [anpassen](https://www.collinsdictionary.com/dictionary/german-english/anpassen)** ganz **für** ihre [**Bedürfnisse**](https://www.collinsdictionary.com/dictionary/german-english/bedurfnis)**.** Wenn Sie **zufrieden** sind, sie können **dirkt** **auf** **die Schaltfläche** CREATE **klicken** dann wird diese **spezifische** Policy **erstellt**.

Ich **warte** nun **bis** dies**e Beeitstellung** **abgeschlossen** ist **dammit** wir [das Resultat](https://www.collinsdictionary.com/dictionary/german-english/resultat) **miteinander** anschauen können. Wir können jetzt **wie bereits erwähnt** das Backup für unsere LinuxVM **direkt auf** dies**e Schaltfläche** **einrichten**.

Jetzt navigiere ich zu mein neue**s** Recovery Service Vault und denn weiter ein bisschen nach unten zu Backup Policies wo unsere Policies **angezeigt wird**.Wir können nun **wie bereist erwähnt** das Backup **für** unsere LinuxVM **direkt über** diese Schaltfläche **einrichten** oder wie gehen zurück zu **die virtuelle Machine.** Ich navigiere zu **der** Operations [**Sektion**](https://www.collinsdictionary.com/dictionary/german-english/sektion) und jetzt können wir unsere neue**n** Recovery Service Vault und unser**e** neu**e** Backup Policy, die wir ganz vorbetreitet haben, **auswählen**.

**Der letzter Schritt** ist ganz einfach **die Schaltfläche** **Enable Backup** [**klicken**](https://www.collinsdictionary.com/dictionary/german-english/klicken) und jetzt wird das Backup für unsere Maschine **eingerichtet.** Jetzt kennen sie den Weg wie sie für ein Linux VM **oder allgemein** wie sie für eine VM ein Backup i**m** Azure Portal **einrichten** können.

---

### [Folge 7 \- Der Einsatz der Serial Console](https://www.youtube.com/watch?v=Yr7BoUgdeBM)

**Zusammenfassung**

Eine Linuxmaschine **verwalten wenn si keine SSH Zugriff haben**  
Wie man **die** Serial Console benutzen kann um eine SSH Verbindung zu einen Linuxmaschine aufzubauen und **Troubleshooting durchführuen**.  
**aus was für Gründe auch immer**  
Zuerst einmal **die [Istsituation](https://www.collinsdictionary.com/dictionary/german-english/istsituation)..**

Herzlich wilkommen. Heute geht es **darum** wie können sie ihre virtuelle Linuxmaschine **verwalten** **wenn si keine SSH Zugriff haben.** Es kann ja mal sein das vielleicht der SSH Dienst **aus was für Gründen auch immer** nicht mehr funktioniert. 

Wie können Sie dann ihre System **trotzdem** **noch** verwalten?

Ein Linuxsystem [**in Einsatz**](https://www.collinsdictionary.com/dictionary/german-english/einsatz) **haben**

Zuerst einmal **die [Istsituation](https://www.collinsdictionary.com/dictionary/german-english/istsituation).** Ich **habe** hier ein Linuxsystem [**in Einsatz**](https://www.collinsdictionary.com/dictionary/german-english/einsatz)**.** Das System ist gestartet, es sieht [soweit](https://www.collinsdictionary.com/dictionary/german-english/soweit)  alles in Ordnung aus. **Kopiere** ich nun die öffentliche IP-Addresse, ich **navigiere zu** Windows Terminal dann verwwende ich 

**ssh  user@\<öffentliche-IP-[Adresse](https://www.collinsdictionary.com/dictionary/german-english/adresse)\-der-System\>**

Ich drücke die Entertaste. Ich wurde denn gefragt, dass ich **die Kennwort antippen** muss. Das werde ich gleich machen und ich bin **mit** de**m** LInux**system** **verbunden** alles im bester Ordnung. **Kein Grund also um inrendwelche Panik zu schieben**. 

Was ist es wenn **eben genau** das nicht mehr funktioniert? Wenn Sie keine SSH Session aufbausen könnne? Wie können sie dann ihre Linux system **trotzdem** verwalten? Es gibt da verschieden Möglichkeiten aber ich möchte ihnen ein **wirklich spezifisch**es und **absolut** **tolles** Werkzeug zeigen.

Dieses Werkzeug finden wir direkt hier in der Übersicht von unsere Linuxmachine, **zwar ein wenich weiter unten.** Navigieren wir **ziemlich weit nach unten** und zwar zu Support und Troubleshooting und hier gibt ein Werkzeug **nennt** Serial Console und genau so ist es, **stellen** sie sich **vor,** dass sie **im Prinzip** mit einer seriellen Schnittstelle **in Anführungszeichen** eine Verbindung aufbauen zu ihren Linuxsystem.

* Wir können die Serial Console **nur** verwenden, **wenn** die Boot Diagnostic **aktiviert** ist.  
* **Diese Funktion [einschalten](https://www.collinsdictionary.com/dictionary/german-english/einschalten)** und **konfigurieren**  
* **über** die Schaltfläche Settings **klicken**  
* **in** **anführung Schlusszeichen / Anfhürungszeichen**

Ich **wähle** nun Serial Console **aus** und jetzt sehen wir **Foldendes,**  wir können diese Console nur verwenden wenn die Boot Diagnostic **aktiviert** ist. Also werden wir das gleich **miteinander konfigurieren.** Ich navigiere zu Boot Diagnostic und hier können wir **diese Funktion [einschalten](https://www.collinsdictionary.com/dictionary/german-english/einschalten).**

Wir machen das **über** die Schaltfläche Settings wir **ganz einfach** ON **auswählen**, dann müssen wir eine Storage Account **auswählen.** Ich verwenden da eine **bestehende** Storage Account und dann **ganz wichtig** die Schaltfläche SAFE **klicken**.

Jetzt werden die Boot Diagnostic **eingeschaltet** und wenn diese **zu Verfügung stehen** dann können wir mit de**m** Serial Console **arbeiten.** Ich warte **nun** bis dies**e Konfiguration gespeichert ist** das ist **bereits der Fall** und jetzt **navigieren** wir **wieder zurück zu** Serial Console und **schauen wir jetzt mal wie** das aussieht.

**Das sieht sehr aus wie einer SSH Session** und es wird eine Verbindung aufgebaut. **Das dauert jetzt ein paar Sekunden** und **anschließend** müssen wir **uns** a**m** System ganz normal **anmelden** wie sie das kennen. Ich **gebe** den Benutzername **an** und dann das Kennwort und jetzt bin ich mit diesem System verbunden. Das ist keien SSH Session, das ist, ich **sags** mal so **in** **anführung Schlusszeichen** serielle Verbindung und jetzt könne wir beispielsweise den **SSH Dienst**  wieder starten Falls diese eben nicht mehr gestartet ist.

* [die Notnagel](https://www.collinsdictionary.com/dictionary/german-english/notnagel) 

Sie können jetzt **das eigentlische Troubleshooting durchführuen**. Die serielle Console ist wirklich ihre [**Notnagel**](https://www.collinsdictionary.com/dictionary/german-english/notnagel) **wenn ich jetzt so sagen darf.** Jetzt möchte ich **sie noch an etwas [hinweisen](https://www.collinsdictionary.com/dictionary/german-english/hinweisen).** Sie haben gesehen, dass sie **musste** den Benutzername **angeben** und dann das Kennwort. 

* Wenn ihre Linuxsystem **ist jetzt so aufgebaut, dass** sie **mit** eine**n** SSA **Schlüsselpaar** (n) arbeiten dann müssen sie das zuert enden\!  
* Schritte [einlegen](https://www.collinsdictionary.com/dictionary/german-english/einlegen)   
* \[eine Vorgang oder Verlauf\] ? **unterbrechen**

In die  serielle Console kann man keine Schlüsselpaar engeben, das funktioniert nicht. Also, sie müssen den folgende **Zwischenschritt [einlegen](https://www.collinsdictionary.com/dictionary/german-english/einlegen) \[?\].**

* die Konfiguration **[ändern](https://www.collinsdictionary.com/dictionary/german-english/andern_2)**  
* **ein Kennwort einsetzen**  
* ein Update **ausführen**  
* Das Troubleshooting zu ihre**m** Linuxsystem **starten** und **führen**


Sie navigieren zu Reset Password und hier [**ändern**](https://www.collinsdictionary.com/dictionary/german-english/andern_2) sie ihre **Konfiguration.** Wenn Sie **eben**, **als bereits erwähnt,** mit einer SSH Schlüsselpaar arbeiten dann **wähle** Sie Reset Password **aus**, sie geben de**n** Benutzername**n** an, sie **setzen** ein Kennwort **ein**, **zweimal das Gleiche** selbstverständlich und **wählen** dann UPDATE **aus**. Wenn das Update **ausgeführt wurde**, wenn also wieder mit einem Password wieder gearbeitet wird dann können Sie wieder **zurückgehen** zu Serial Console und können dann ein**e Verbindung aufbauen zu** ihren Linuxsystem und zwar genau so wie ich es eben gezeigt habe.

Sie können nun ihren Troubleshooting **starten** zu ihre**m** Linuxsystem. Ich hoffe ich könnte ihnen zeigen, dass **die** Serial Console **ein wirklich tooles Instrument ist** falls sie keine Verbindug zu ihren Linuxsystem aufbauen kann, beispielsweise **über die öffentliche** oder **private IP-Addresse**.

 Sie können immer eine Verbindung durch **die** Serial Console nutzen und ihre Troubleshhoting **in alle Ruhe führen**.

---

### [Folge 6 \- Linux VM in Azure mit Azure Active Directory-Authentifizierung](https://www.youtube.com/watch?v=e1RK3inhilY)

#### [Install\_the\_Azure\_AD\_login\_VM\_extension](https://github.com/tomwechsler/LinuxOnAzure/blob/master/Install_the_Azure_AD_login_VM_extension.txt) 

[Sign in to a Linux virtual machine in Azure by using Microsoft Entra ID and OpenSSH](https://learn.microsoft.com/en-us/entra/identity/devices/howto-vm-sign-in-azure-ad-linux)   
[Anmelden bei einer Linux-VM in Azure mithilfe von Microsoft Entra ID und OpenSSH](https://learn.microsoft.com/de-de/entra/identity/devices/howto-vm-sign-in-azure-ad-linux) 

**Zusammenfassung**

**Das [Authentifizierung](https://www.collinsdictionary.com/dictionary/german-english/authentifizierung) etwas genauer unter die Lupe nehmen.**  
**Das Authentifizierung mit** der Azure Active Director [**konfigurieren**](https://www.collinsdictionary.com/dictionary/german-english/konfigurieren) (als [**Sicherheitsmaßnahme**](https://www.collinsdictionary.com/dictionary/german-english/sicherheitsmassnahme))  
Wie man das Azure Active Directory  verwenden kann **als [Authentifizierung](https://www.collinsdictionary.com/dictionary/german-english/authentifizierung)**  
Wie man auf ein Linux System ein lokal**es** **Konto / lokalen Konte** [**anlegen**](https://www.collinsdictionary.com/dictionary/german-english/anlegen) kann. 

[**die Anmeldung**](https://www.collinsdictionary.com/dictionary/german-english/anmeldung) \= [**die Registrierung**](https://www.collinsdictionary.com/dictionary/german-english/registrierung) | [die Bewerbung](https://www.collinsdictionary.com/dictionary/german-english/bewerbung),   
\> [die Applikation](https://www.collinsdictionary.com/dictionary/german-english/applikation) (=**die Anwendung** eine Methode)   
\[COMP\] ein**e Applikation** (auf ein System)  [**installieren**](https://www.collinsdictionary.com/dictionary/german-english/installieren) 

Heute geht es darum, dass wir **das Authentifizierung** **etwas genauer unter die Lupe nehmen** und **zwar** möchte ich mit Ihnen **Folgendes** [**konfigurieren**](https://www.collinsdictionary.com/dictionary/german-english/konfigurieren)**.** Ich möchte [**die Anmeldung**](https://www.collinsdictionary.com/dictionary/german-english/anmeldung) **bei** eine virtuelle Linux Machine in Azure **mit** der Azure Active Directory [**Authentifizierung**](https://www.collinsdictionary.com/dictionary/german-english/authentifizierung) **[konfigurieren](https://www.collinsdictionary.com/dictionary/german-english/konfigurieren).**

**Zuert** aber einmal **um was geht es. Schauen** wir uns **bei** den virtual Machine etwas genau **um.** Ich suche die IP Adresse, **damit** ich eine Verbindung mit diesem System **aufbauen** kann.Ich verwende **dazu also**  das Windows Terminal, dies**e Verbindung** werde ich nun **schließen** und ich verwenden..

**ssh  user@\<öffentliche-IP-[Adresse](https://www.collinsdictionary.com/dictionary/german-english/adresse)\-der-System\>**

Ich verwende hier **ein lokales Konto** welches auf dem Linux System **konfiguriert** ist. Ich drücke die Entertaste und ich muss **die Fingerprint [akzeptieren](https://www.collinsdictionary.com/dictionary/german-english/akzeptieren),** ich **gebe** das Kennwort zu diese**m Konto an**  und jetzt bin ich mich mit dem System verbunden. 

Wegen ich ein lokalen Konto benutzt habe um eine Verbindung mit dem System zu aufbauen, wir können zum Beispiel mit **sudo** arbeiten wie in die Folgende.

**sudo cat** /**etc/passwd**

**Darin enthalten** werden wir sehen welche Konte **vorhanden sind** unt **unter anderen** sehe ich das Konto das ich nun benutzt. Wir könnte jetzt weiter **Konte** [**anlegen**](https://www.collinsdictionary.com/dictionary/german-english/anlegen)**.** Wir könnten jetzt weitere**n [anlegen](https://www.collinsdictionary.com/dictionary/german-english/anlegen) damit** ander**e Benutzer** (pl) **ebenfalls** mit diesem Linux Machine arbeiten können. Aber ich glaube wir habe **bereits** die Idee erhalten, das wird sehr [**aufwendig**](https://www.collinsdictionary.com/dictionary/german-english/aufwendig) (=[**aufwändig**](https://www.collinsdictionary.com/dictionary/german-english/aufwandig)). **Es wäre doch nun super wenn** wir das Azure Active Directory  verwenden könnten **als [Authentifizierung](https://www.collinsdictionary.com/dictionary/german-english/authentifizierung).** Und genau das möchte ich mit ihnen [**konfigurieren**](https://www.collinsdictionary.com/dictionary/german-english/konfigurieren).

Wie kan man auf ein Linux System ein lokal**es** **Konto / lokalen Konte** [**anlegen**](https://www.collinsdictionary.com/dictionary/german-english/anlegen)?  
[**anlegen**](https://www.collinsdictionary.com/dictionary/german-english/anlegen) \> Datei / Users / ein Konto [**anlegen**](https://www.collinsdictionary.com/dictionary/german-english/anlegen)  
[der Benutzer, die Benutzer](https://www.dwds.de/wb/Benutzer)   
    
[**die Ressource**](https://www.collinsdictionary.com/dictionary/german-english/ressource) **\>** eine Ressource [**bereitstellen**](https://www.collinsdictionary.com/dictionary/german-english/bereitstellen) **|** einige **notwendige** Ressource**n**  
**die Bereitstellung von** Ressourcen  
[**Notwendigerweise**](https://www.collinsdictionary.com/dictionary/german-english/notwendigerweise) **\> [Notwendigerweise](https://www.collinsdictionary.com/dictionary/german-english/notwendigerweise)** müssen wir einige Ressourcen bereitstellen.

Wir **starten** zuerst einmal **in** d**er** Clound Shell. Wir müssen di **notwendigen [Ressourcen](https://www.collinsdictionary.com/dictionary/german-english/ressource)** und **dazu** verwende ich jetzt einmal **als Beispiel** die Clound Shell nicht wie im Poweshell sondern die Clound Shell und zwar habe ich ein **Bash Umgebung gestartet.** Als erster Schritt wir **erstellen** eine Ressourcen Gruuppe und das sieht **in etwa** so aus.

**az group create \--name myrg1 \--location  westeurope**

[**der Struktur**](https://www.collinsdictionary.com/dictionary/german-english/struktur) eine**s** Befehl**s [einfügen](https://www.collinsdictionary.com/dictionary/german-english/einfugen)**

Ich drücke die Entertaste und **die Ressourcengruppe** ist bereits erstellt. Nun **erstellen** wir einen neuen Linuxmachine. Ich werde ihnen gleich zeigen wie es aussieht. **Zuerst** de**n** **Bildschirmsinhalt** **aufräumen** mit **CTRL+L** und nun **füge** ich de**n Befehlstruktur** **ein** mit Paste.

Wir erstellen ein neuen Virtuellemachine mit

**az vm create \--reourceGroup RG \--name MyVM \--image UbuntuLTS \--admin-user USER \--generate-ssh-keys**

Wir **generieren** auch **ein SSH Schlüsselpaar** wir drücken die Entertaset und **die** **Bereitstellung** **wird durchgeführt**. Wenn dies**e Linux VM** bereitgestellt ist dann könnten wir **im Prinzip** **direkt** eine SSH Sitzung zu diesem System **aufbauen** zu diese**m** System aber, das möchte ich nicht\!

Ich möchte eher eine Extension **installieren** und zwar eine extention **damit** wir dann die Möglichkeit erhalten ums mit einem Active Directory Benutzer **an**zu**melden.** Wie das nun **konfiguriert** wird? Das werde ich ihnen gleich zeigen **sobald** diese Bereitstellung der Linux Maschine **abgeschlossen ist.**

de**n Bildschirminhalt [aufräumen](https://www.collinsdictionary.com/dictionary/german-english/aufraumen)** (1) \> ein **aufgeräumt Zimmer**  
**mit etwas [aufräumen](https://www.collinsdictionary.com/dictionary/german-english/aufraumen)** (2) \> [**beseitigen**](https://www.collinsdictionary.com/dictionary/german-english/beseitigen) **\= [eliminieren](https://www.collinsdictionary.com/dictionary/german-english/eliminieren)**    
**Schlussendlich (Endlich)** habe ich mich entschieden mit den ganzen Plan **aufzuräumen**  
**mit etwas [aufräumen](https://www.collinsdictionary.com/dictionary/german-english/aufraumen)** (3) \> [**dezimieren**](https://www.collinsdictionary.com/dictionary/german-english/dezimieren)   
[**die Seuche**](https://www.collinsdictionary.com/dictionary/german-english/seuche) hat **unter** der Bevölkerung gründlich **aufgeräumt** 

[**einräumen**](https://www.collinsdictionary.com/dictionary/german-english/einraumen) (1) \>  Wäsche, Bücher, Schrank, Regal \[stecken\] | Wohnung, Zimmer, Möbel  
Bücher **ins**  / in de**n Schrank** einräumen  
er war mir beim Einräumen meiner Wohnung **behilflich.**  
können Sie bitte die Wäsche in den Schublade für mich mal **einräumen**

eine**n** Befehl [**einfügen**](https://www.collinsdictionary.com/dictionary/german-english/einfugen) \> eine neue **Maschinenteile [einfügen](https://www.collinsdictionary.com/dictionary/german-english/einfugen)**  
Zuerst [**kopiere**](https://www.collinsdictionary.com/dictionary/german-english/kopieren) ich de**n Text** und dann füge de**n ausgeschinittetn Tetx** in**s Form** ein.

Die Bereitstellung ist **abgeschlossen** und wir können weiter arbeiten. Wir **installieren** nun die Extension. Zuerst einmal den Bildschirminhalt etwas **auf**räumen mit CTRL+L und ich **füge** nun de**n Behfel** **ein**. Der Befhel **lautet wie folgt**.

**az vm extension set \\**   
**\--publisher Microsoft.Azure.ActiveDirectory.LinuxSSH \\**  
**\--name AADLoginForLinux \\**  
**\--resource-group myRG \\**  
**\--vm-name MyVM**

eine **Extention [installieren](https://www.collinsdictionary.com/dictionary/german-english/installieren)**

Ich drücke die Entertaste **damit** diese Extention **installiert werden kann**. Wir werden es **selbstverständlich** gleich **überprüfen**, **ob** diese Extention **erfolgreich** installiert wurde und wir werden dann gleich mit dem nächsten Schritt  weiter arbeiten.Wir müssen **bei** der eben erstellte Ressourcengruppe noch **mit** Role Based Access Control **arbeiten**.

**Aber einer nach dem anderen, Schritt für Schritt.** Lassen wir zuerst einmal diese Bereitstellung abschließen **bevor** wir weiter arbeiten. Ich schließe diese Cloud Shell. Ich **navigiere zu** Ressourcen Gruppe und **anschließend zu** MyRG **darin enthalten** unsere virtuelle Maschine **mit den Namen** MyVM. 

eine **zusätzliche** [**Berechtigung**](https://www.collinsdictionary.com/dictionary/german-english/berechtigung) **brauchen** (=[**die Befugnis**](https://www.collinsdictionary.com/dictionary/german-english/befugnis))   
eine \- **erhalten / erteilen / brauchen**  
einen **Benutzer** [**berechtigen**](https://www.collinsdictionary.com/dictionary/german-english/berechtigen) **\>** jdn **zu** etwas **\-** | diese **Karte** berechtigt nicht **zu Eintritt**  
**Zutritt ohne \-** ist nicht [**gestatten**](https://www.collinsdictionary.com/dictionary/german-english/gestatten) **(= [einwilligen](https://www.collinsdictionary.com/dictionary/german-english/einwilligen))**

**entweder..oder**, ich halte es etwas Einfaches

Jetzt **prüfen** wir, **ob** die Extension installiert wurdet. **Navigieren** wir hier zu Extensions und wir sehen die Extention ist installiert. **Ohne** diese Extension können wir nicht **mit AD arbeiten**. Jetzt brauchen wir eine zusätzliche [**Berechtigung**](https://www.collinsdictionary.com/dictionary/german-english/berechtigung) und zwar ich möchte nun einen **Benutzer** [**berechtigen**](https://www.collinsdictionary.com/dictionary/german-english/berechtigen), dass er **eben** mit diesem Linux VM arbeiten kann. Ich kann **also** die RBAC Rolle **zuweisen entweder bei** der virtulle Machine **oder**, ich halte es etwas Einfaches, ich **verwenden dazu** gleich die **Ressourcengruppe.**

RBACK Rollen **einsetzen | verwenden | zuweisen**  
eine öffentliche IP-Addresse ein**er** viertuelle Machine **zuweisen**

Ich navigiere zu Access Control (IAM) und dann suchen wir eine bestimmte Rolle. Zuerst einmal **wähle** ich Add Role Assignment **aus dann** wir müssen die **entsprechende** Rolle **suchen.** Es gibt zwei **Rolle** die wir **einsetzen** können. **Entweder** können wir Virtual Machine Administrator **verwenden** oder Virtual Machine User Login 

* wenn Sie **innerhalb** der virtuelle Machine **aus** der **innerhalb** ihere Linux Machine mit **sudo** arbeiiten möchten dann brauchen sie die Rolle Virtual Machine User Login dann **erhalten** sie **das Recht,** dass sie mit **sudo Befehle** arbeiten können  
* wenn Sie als ganz normaler Benutzer arbeiten möchten denn wähle sie die Rolle Virtual Machine User Login

eine Option [**selektieren**](https://www.collinsdictionary.com/dictionary/german-english/selektieren)  

Dann brauchen wir nun **das** **entsprächende Konnto** mit dem wir arbeiten möchten. Ich **[selektiert](https://www.collinsdictionary.com/dictionary/german-english/selektieren)** und ich wähle SAVE. Jetzt wird diese Rolle **zugewiesen** das ist bereits **abgeschlossen** und diese ist die **Benachrichtigung** denn **navigiere** ich **zu** Role Assignment **damit** wir **das prüfen können.** Dort finde ich den Benutzer und die Rolle die ich ihm **zugewiesen** habe.

Jetzt brauchen wir die öffentliche IP-Addresse unsere VM **damit** wir **das Ganze überprüfen** können. **Selbsterständlich** ist es nicht ideal wenn man eine einzelne virtulle Machine eine öffentliche IP-Address **zuweißt** aber es geht ja hier um den (einen) Test, dass wir mit unserer Azure AD arbeiten können.

den Loginname | **das** Kennwort **angeben \>** die die öffentliche IP-Addresse **einfügen**  
den Fingerprint [**akzeptieren**](https://www.collinsdictionary.com/dictionary/german-english/akzeptieren)

Nun **navigieren** ich wieder **zu** Windows Terminal und  jetzt **verwende** ich **Folgendes**   
\[ssh **Abstand** Minus L um den Loginname **anzugeben** und wir **fügen** die öffentliche IP-Addresse **ein**\] dann drücke ich die Entertaste muss ich den Fingerprint [**akzeptieren**](https://www.collinsdictionary.com/dictionary/german-english/akzeptieren)**.**

**ssh \-l loginname@domain.subdomain \[öffentliche IP-Addresse\]**

**sich bei** eine**m** Linuxsystem [**anmelden**](https://www.collinsdictionary.com/dictionary/german-english/anmelden) (=[**ankündigen**](https://www.collinsdictionary.com/dictionary/german-english/ankundigen))

Wir haben jetzt die Möglichkeit **uns** **an**zu**melden** und es wurde erkannt, dass eben diese Extension **vorhanden** ist, dass wir da mit dem Azure AD arbeiten möchten und **darum** müssen wir jetzt nicht **das Kennwort** vo**m** Benutzer **angeben**. Jetzt erhalte ich den Device Login **duch**zu**füheren** das bedeutet also wor habe jetzt die Möglichkeit **uns an**zu**melden** und dass wurde erkannt dass eben diese Extension vorhanden ist dass wir mit dem Azure AD arbeiten möchten und **damit** müssen wir **nicht direkt** dass **Kennwort** vo**m** Benutzer auf das Linuxsystem **angeben**.

[http://microsoft.com/devicelogin](http://microsoft.com/devicelogin)

**das Azure AD** als **Authentifizierungs**dienst / **Authentifizierungs**provider **einsetzen**  
eine URL [mittels](https://www.collinsdictionary.com/dictionary/german-english/mittels) (+gen) eine**m** [Browser](https://www.collinsdictionary.com/dictionary/german-english/browser) (m) **aufrufen**  
etwas im Terminal **markieren und kopieren**

**Navigieren** wir zu eine**m Browser damit** wird genau diese **URL aufrufen** können und jetzt müssen wir den Code **angeben, der** wir finden im Terminal wo wir können das Ganze **markieren und kopieren** und es geht weiter und jetzt wird **die Authentifizierung durchgeführt**.

**durch** Azure AD | **mit** eine**m** Azure AD [**Konto**](https://www.collinsdictionary.com/dictionary/german-english/konto) (m)  **an** einem Linuxsystem **angemeldet werden**

Ich muss den Benutzer **angeben**, dass ich **eingesetzt habe** **loginname@domain.subdomain** und dann das Kennwort und jetzt wir arbeiten mit dem Azure AD. Es ist kein lokales Konto **sondern** das Azure AD.  
Nun drücke ich die Entertaste im Terminal und wir werden direkt **an** Linuxsystem **angemeldet.** Wir haben also **das Azure AD** als **Authentifizierungs**dienst **eingesetzt**. Es ist keine lokale Anmeldung **an** unsere Linuxsystem mehr.

Es ist eine tolle Sache, dass wir könne unseres Azure AD auch **bei** unseren Lynuxsystemen als **Authentifizierungs**provider **einsetzen**. Und wenn sie sich jetzt gefragt haben wo erhalte ich denn die enizelnen Schritte für die Bereitstellung die wir durch die Cloud Shell durchgeführt haben das will ich ihnen gleich zeigen.

---

### [Folge 5 \- Wie funktioniert die Linux Shell?](https://www.youtube.com/watch?v=NfXHwqik4vI)

**Zusammenfassung**

**Wie die Schell eigentlich funktioniert.**

Heute [**thematisieren**](https://www.collinsdictionary.com/dictionary/german-english/thematisieren) wir wie **funktioniert** eigentlich **die Shell.** Lassen Sie uns genau das in diese**m miteinander besprechen**. Zuerst enmal **navigiere** ich **zu** Windows Terminal weil, ich habe **eine aktive Verbindung mit zu** unsere**m** Red Hat Server System **aufgebaut**.

[nachfragen](https://www.collinsdictionary.com/dictionary/german-english/nachfragen) (= sich **nach jedm/etwas** [erkundigen](https://www.collinsdictionary.com/dictionary/german-english/erkundigen), anfragen \= [erfragen](https://www.collinsdictionary.com/dictionary/german-english/erfragen) )   

Wir **gehen**, wie bereits **erwähnt,** in deise Folge **nach** 

* wie funktioniert die Shell?  
* Was passiert wenn man bei einem Befehl die ENTER Taste drückt?

[**abarbeiten**](https://www.collinsdictionary.com/dictionary/german-english/abarbeiten) (= Befehlen, Planen [**ausführen**](https://www.collinsdictionary.com/dictionary/german-english/ausfuhren) )  
(Planen, Gesetzen, Vorhaben, Beschluss, Untersuchungen, Prüfung [**durchführen**](https://www.collinsdictionary.com/dictionary/german-english/durchfuhren))  
[**folglich**](https://www.collinsdictionary.com/dictionary/german-english/folglich) (=deshalb, demnach, deswegen, darum, somit)  
[**anzeigen**](https://www.collinsdictionary.com/dictionary/german-english/anzeigen) \=  **die Inhalt eines Verzeichnis anzeigen ls \-la**

**Die Schell [abarbeitet](https://www.collinsdictionary.com/dictionary/german-english/abarbeiten) immer Linie für Linie.** Wenn Sie ein Befehl eingebebn und dann die Entertaset drücken wird dies von der Schell [**übersetzt**](https://www.collinsdictionary.com/dictionary/german-english/ubersetzen). Wenn wir nun cd eingebe und nchts weiter passiert [**folglich**](https://www.collinsdictionary.com/dictionary/german-english/folglich) **nichts**. Um dies schnell zu erklären \<cd\> bedeutet CHANGE DIRECTORY und ich befinde mich **aktuell** in meine**m** Home **Verzeichnis** und ich verwende \* um alles **an**zu**zeigen.**

**ls \-la**  
**ls** steht für Listing und **\-l** steht für Long (Listing) und **\-a** steht für ALL.

Das ist **der Inhalt** von meine**m** Home Verzeichnis. Wenn ich jetzt wissen möchte in welche Verzeichnis ich mich befinde verwende ich ganz einfach **pwd** der steht für **Print Working Directory**.

**pwd**

Es wird mir eingezigt **tatsächlich** ich **befinde mich** in Verzeichenis /home/**userid**. Kommen wir zurück zu**m Befehl cd mit dem** können Sie ein CHANGE DIRECTORY **durchführen also** in ein andere**n Verzeichnen navigieren**. Wenn aber jetzt **cd eingeben** in ihre**m** Home Verzeichnis **hone Argument** dann passiert **nichts** ich bleibe in meinem Home Verzeichnis. Ich möchte Ihnen **einmal** **zeigen** wie es aussieht.

**cd/etc**

Befinde mich jetzt im Verzeichnis etc aber wenn jetzt wieder **cd** **eintippe** **ohne zusätzliche** Argument dann **gelangen** ich zurück zu meine Home Verzeichnis. Was passiert aber wenn ich **ein Befehl eingebe** der ncht gibt? **Es dauert ein kurzer Moment** und die Schell **versuche es [ausfindig](https://www.collinsdictionary.com/dictionary/german-english/ausfindig) zu machen was das ist,** findet aber nchts und **aus Ausgabe** **erhalte** ich *command not found*.

Was definiert aber eigentlich eine**n** Befehl? Alle Zeichnen bis zu**m** erste [**Leerschlag**](https://www.collinsdictionary.com/dictionary/german-english/leerschlag) **oder [Leerzeichen](https://www.collinsdictionary.com/dictionary/german-english/leerzeichen)** wird für die Schell **aus Befehl [übersetzt](https://www.collinsdictionary.com/dictionary/german-english/ubersetzen).** Wie findet denn die Schell die Befehle? **Dazu** verwendet die Schell **die Umgebungsvariablen**.

**echo $PATH**

**Im [Spezifischen](https://www.dwds.de/?q=Spezifischen&from=wb)**, **die Variable $PATH.** Hier **sucht** die Schell **nach den** sopezifische**n** Befehl**e.** Das ist eine Liste von **Verzeichnisse** welche die Schell **duchläuf um** diese Befehle zu finden. Wir können mit dem Befehl **type** [herausfinden](https://www.collinsdictionary.com/dictionary/german-english/herausfinden) wo diese Befehl [abgelegt ist](https://www.collinsdictionary.com/dictionary/german-english/ablegen).

**type cd**  
**type less**

**cd** ist ein [**sogenannt**](https://www.collinsdictionary.com/dictionary/german-english/sogenannthttps://www.collinsdictionary.com/dictionary/german-english/sogenannt)**e** Shell BUILTIN Befehl eber mit **type less** die Schell zeigt wo den Befehl **less** [**abgespeichert**](https://www.collinsdictionary.com/dictionary/german-english/abspeichern) ist. Wenn jetzt wir **less** zu der Schell eingeben denn sie in der Umgebungsvariable **$PATH** und findet dann [**schlussendlich**](https://www.collinsdictionary.com/dictionary/german-english/schlussendlich) den Befehl **less** in diesem Verzeichnis /usr/bin.

**set \-x**  
**cd** \~

Mit **set \-x setzen** wir ein **Debugebene ein.** Schauen wir uns mal was ist nun passier, es ist nun [**ersichtlich**](https://www.collinsdictionary.com/dictionary/german-english/ersichtlich), dass die Schell zuerst (\~) **das Tilde übersetzt** und dann **cd ausführt**. Das tilde wurde übesezt **in** /home/user und dann wurde den Befehl ausgeführt. 

**Lassen** ~~wir~~ **uns** das Ganze **nochmal** [**demonstrieren**](https://www.collinsdictionary.com/dictionary/german-english/demonstrieren)**.** Sie erinnern sich wier haben **echo $PATH** verwendet. Was passiert genau wenn man die Taste audrückt?

Es wurde **zuerst** die Variable **$PATH** übersetzt **anschließend** wurde dies**e Übersetzung** von der Bfehl **echo** **verarbeitet** um **die Ausgabe** **an**zu**zeigen.**

 **Lassen** ~~wir~~ **uns** mit einem weiteren Beispiel arbeiten: **cd $Home**. Was passiert genau wenn man die Taste audrückt? **$Home** wird **zuerst** übersetzt und dann wid was übersetzt wurde von **cd verarbeitet**.

Mit diese**n** drei Beispiel**e** ist es [**sichtlich**](https://www.collinsdictionary.com/dictionary/german-english/sichtlich) **(es liegt auf der Hand),** dass **zuerst** die Variablen übersetzt werden und dann **anschießend** den eigentlichen Befehl ausgefürt wird. 

**Und jetzt wissen Sie wie die Schell funktioniert\!**

---

### [Folge 4 \- SSH Schluesselpaar erstellen und Anmeldung testen](https://www.youtube.com/watch?v=bNH8YiZFxzk)

**Zusammenfassung**

1. Wie man ein SSH Schlüsselpaar mit dem Befehl **ssh-keygen** generieren/herstellen kann   
2. Den Weg kennen wie man bei**m**  Azure Portal eine öffentliche Schlüssel **hin**zu**fügen** kann  
3. Wie man ein SSH öffentliche Shclüssel mit dem Befehl **ssh-copy-id** auf ein anderes Linux System kopieren kann  
4. Wie man damit ein sicherer Verbindung zu einen Linux System aufbauen kann

**eine Schlüsselpaar generieren**  
Es etwa**s** sicher**er** **machen/gestalten**  
**Eine Verbindung (zu etwas) aufbauen**

Heute geht es darum dass, wir **eine Schlüsselpaar für ein SSH Verbindung generieren. Damit** wir unsere Kommunikation zu unser**er Linux VM** etwa**s** sicher**er gestalten** können. Wir erinnern uns an Folgend**es,** wir haben das Windows Terminal verwendet um eine Verbindung auf**zu**bauen **zu** unsere Red Hat System.

\[**ssh** USERNAME@XXX.YYY.ZZZ.UUU\] 	\[**ssh** USERNAME@\<öffentliche IP Adresse\>  
Mit dem Befehl \[**ssh** USERNAME@\<öffentliche IP Adresse\> ich **drücke** **die** ENTER **Taste** und jetzt **werde** ich **aufgefordert** [**das Kennwort**](https://www.collinsdictionary.com/dictionary/german-english/kennwort) dann zu geben. Das werde ich gleich machen und jetzt sind wir **mit** dem Red Hat System **verbunden**.

Ich arbeite also in diesem Beispiel **mit** eine**m** **Benutzernamen** und Passwort aber das möchte es nun ändern. Ich möchte nun mit eine**m Zertifikat** arbeiten **bzw.** eben mit ein SSH Schlüsselpaar **damit** wir dies**e Verbindung sicherer** **gestalten** können. Was müssen wir ändern?

**das Passwort [zurücksetzen](https://www.collinsdictionary.com/dictionary/german-english/zurucksetzen)** (nach hinten gehen \[Auto\], auf frührenn Platz, **zurückgesetzt** **Preis**)

Ich will Ihnen das gleich zeigen. Ich **navigiere zu** unsere**m** Red Hat System dann **in der Übesrsicht navigiere ich nach unten** dann haben wir die Möglichkeit **ganz weit unten bei** Support und Trouble shooting das Passwort **zurück**zu**setzen.** 

Ein \[SSH Public Key\] **verwenden**  
Aber ich möchte nicht das Passwort zurücksetzen nein ich möchte ein \[SSH Public Key\] verwenden.  
Dass wir dann **nicht mehr** einer Verbindung aufbauen **mit ein Passwort** sondern **mit** einem Sclüsselpaar.

Eine Schlüsselpaar **generieren/erstellen**  
**\[ssh-keygen\]**  das ist SSH [**Bindestrich**](https://www.collinsdictionary.com/dictionary/german-english/bindestrich) KEYGEN  
zu Verfügung stehen

Jetzt brauchen wir ein Schlüsselpaar **und zwar** brauchen wir eine**n privaten Schlüssel** und eine**n öffentlichen Schlüssel.** Wie **generieren** wir nun diese **Schlüsselpaar?** Ganz einfach ich **navigiere zurück zu** Windows Terminal und ich verwenden **das Kommando \[ssh-keygen\]** mit diese**m Werkzeug** können wir ein Sclüsselpaar **generieren**.

**\[ssh-keygen\]** steht Ihnen wenn Sie mit Linux arbeiten **direkt** auch zu Verfügung sie müssen **da** nichts nach installieren. Ich habe auch schon gezeigt dass ich auf meinem System mit dem Linux Subsystem arbeite **darauf** kann ich **nicht direct \[ssh-keygen\] aufrufen.** Wenn Sie es jetzt nicht mehr wissen **was ich genau meine** dann zeige ich Ihnen das schon mal.

**Mit** Rechts**click** **auf** die **Startfläche** **wähle** ich **Ausführen** \[RUN\] navigieren zum CONTROL PANEL **anschließend** zu PROGRAMME UND FEATURES und dann **wähle** ich WINDOWS FEATURE **aktivieren** oder **de**aktivieren. Es wird **eine Liste generiert** ich **navigieren nach unten** und Sie sehen **ich habe das** WINDOWS SUBSYSTEM für LINUX **aktiviert.** Das müssen Sie **ebenfalls** machen **damit** Sie diesen Befehl dann **anschließend** **zu Verfügung haben**.

Lassen uns nun **das Schlüsselpaar generieren** **ssh-keygen.exe** und drücke die ENTER Taste und jetzt wurde ein Schlüsselpaar **erstellt** und zwar ein PUBLIC und ein PRIVATE KEY. Jezt **erhalten wir die Nachricht** wo **der** private **Sclhüssel** **gespeichert** wird.

Jetzt müssen wir eine PASSPHRASE **angeben.** Die PASSPHRASE schützt den private Schlüssel, die PASSPHRAS **ist nichts anderes als** eine Art Passwor**t** sie können sie auch **leer lassen** sie müssen dann die ganze **zweimal bestätigen mit** de**r** ENTER **Taste** und dann wäre keine PASSPHRASE **gesetzt**.Ich empfehlen aber dass Sie den private Schlüssel schützen mit einer PASSPHRASE deshalb würde ich nun die PASSPHRASE **eintippen.**

Jezt sehen Sie wurde das Schlüsselpaar **erstellt** und wir **erhalten die Benachrichtigung** mit dem Pfad zu dem **öffentlichen** Schlüssel und genau diese Pfad brauchen wir jezt. Wir müssen nun diesen **öffentlichen** **Schlüssel** in Azure Portal verwenden und damit habe ich de**n** Pfad in die **Zwischenablage** **kopiert**. 

\[**notepad** PATH-TO-PUBLIC-KEY\]  
eine**n** private / de**n** Schlüssel [**kompromittieren**](https://www.collinsdictionary.com/dictionary/german-english/kompromittieren)    
**mit** de**m** öffentlichen Schlüssel **arbeiten (**\=**benutzen)**

Ich muss diese Inhalte in die Zwischenablage kopieren. Den öffentliche Schlüssel, können Sie verteilen deb oft wie sie wollen aber de**n private** Schlüssel **niemals im fremde Hände geben.** Wenn der private Schlüssel **kompromittiert** ist, dann können Sie **mit** de**m** öffentlichen **Schlüssel** nicht mehr **arbeiten. Außerdem** den private Schlüssen muss immer **in ihrem Besitz bleiben**.

**auf** eine **Schaltfläche** **clicken**  
Eine [**Konfiguration**](https://www.collinsdictionary.com/dictionary/german-english/konfiguration) **speichern**

Jetzt können wir die [**Anpassung**](https://www.collinsdictionary.com/dictionary/german-english/anpassung) **durchführen.** Wir **verwenden** hier die zweit**e Option**. Wir möchten hier **mit** ein SSH Key **arbeiten** ich **gebe** de**n** Benutzername **an** und dann **füge** ich den öffentliche Schlüssel **ein** \[SHH Public Key\] nun ich habe auf das **Schaltfläche** UPDATE **geklickt.** Es wird aber das Update noch nicht  durchgeführt, Nein\! **Es wurde** **zuerst** der \[Public Key\] **überprüft** und wir sehen doese **grüne Checkmark**. Das **zeigt an,** dass mit diese Schlüssel gearbeitet werden kann.

Jetzt click ich nochmals auf die Schaltfläche Update und jetzt wird dies**e [Konfiguration](https://www.collinsdictionary.com/dictionary/german-english/konfiguration)** **gespeichert** das heißt wir können uns in einem nächsten Schritt wieder an unse**m** Linux **System anmelden** aber wir **verwenden** nicht mehr ein **Passwort** sondern **eben** diese**s Schlüsselpaar**.

Die **Pfeiltaste drücken** um die **letzte Befehlen** zu **wiederholen.**  
[**angeben**](https://www.collinsdictionary.com/dictionary/german-english/angeben) (=nennen,**eingeben**, \=bestimmen Tempo, Kurs, \=behaupten, aussagen, anzaigen Preis, Teperatur)  
[Der Schlüssel](https://www.collinsdictionary.com/dictionary/german-english/schlussel) / das Passwort

Das wurden wir jetzt **testen,** wir gehen zurück zu Windows Terminal und **drücke** **die Pfeiltaste nach oben** um die letzte Behfele **zu widerholen** und jetzt rufen wir die **ssh** auf mit user@\<**öffentliche**\-IP-Adresse\> und jetzt sehen  sie die Unterschied. Wir müssen nicht mehr das Passwort **eingeben sondern** die Passphrase. Wir müssen die Passphrase **von unserem** privaten Schlüssel [**angeben**](https://www.collinsdictionary.com/dictionary/german-english/angeben)**.**

**mehr** **Sicherheit** **integrieren**  
**auf Brute Force Angriffe anfällig sein**  
**für** eine**m** **Verbindung** zwischen Systeme **ein SSH Schlüsselpaar** **einsetzen**  
**eine Verbindung schließen**  
das Inhalt (Bildschirminhalt) **löschen**  
**ein Schlüsselpaar \[n\] generieren / herstellen**  
**Jdm wie** etwas **funktioniert zeigen**   
**die Information erhalten (wie/wo…)**  
**eine [Datei](https://www.collinsdictionary.com/dictionary/german-english/datei) / [Daten](https://www.collinsdictionary.com/dictionary/german-english/daten) speichern | [ablegen](https://www.collinsdictionary.com/dictionary/german-english/ablegen)**    
Eine**n öffentlichen Schlüssel auf** ein System **kopieren**   
**eine/die IP [Adresse](https://www.collinsdictionary.com/dictionary/german-english/adresse)** eingeben / angeben /[**eintippen**](https://www.collinsdictionary.com/dictionary/german-english/eintippen) / [**abtippen**](https://www.collinsdictionary.com/dictionary/german-english/abtippen) / [**einsetzen**](https://www.collinsdictionary.com/dictionary/german-english/einsetzen) / [~~antippen~~](https://www.collinsdictionary.com/dictionary/german-english/antippen)  
**die Bestätigung** erhalten, dass es wurde **ein Schlüssel [hin](https://www.collinsdictionary.com/dictionary/german-english/hinzufugen)**[zu**gefügt**](https://www.collinsdictionary.com/dictionary/german-english/hinzufugen)  
**die Benachrichtigung** erhalten

[**testen**](https://www.collinsdictionary.com/dictionary/german-english/testen) ([**prüfen**](https://www.collinsdictionary.com/dictionary/german-english/prufen) | **nach**prüfen, [**erpröben**](https://www.collinsdictionary.com/dictionary/german-english/erproben), [**untersuchen**](https://www.collinsdictionary.com/dictionary/german-english/untersuchen) **\= [inspizieren](https://www.collinsdictionary.com/dictionary/german-english/inspizieren)** , probieren, auprobeieren)  
jdn **in** etwas testen / prüfen, wer hat **bei dir** geprüft?, **schriftlich geprüft** werden  
probieren / ausprobieren \= **auf die Probe stellen,  \= [inspizieren](https://www.collinsdictionary.com/dictionary/german-english/inspizieren)** | [**untersuchen**](https://www.collinsdictionary.com/dictionary/german-english/untersuchen)  
**Lebensmittel, Wein zur [Inspektion](https://www.collinsdictionary.com/dictionary/german-english/inspektion) bringen \= [inspizieren](https://www.collinsdictionary.com/dictionary/german-english/inspizieren)**

[**antippen**](https://www.collinsdictionary.com/dictionary/german-english/antippen)   
jeden **auf** sein**e [Schulter](https://www.collinsdictionary.com/dictionary/german-english/schulter)** **antippen** | das Pedal / die Bremse / das Bildschirm (leicht) **antippen**  
**bei** jdm **antippem, ob**.. \[untersuchen, ermitteln, nachgehen, recherchieren, ausforschen, durchleuchten\]   
De**n** [**Vorgang**](https://www.collinsdictionary.com/dictionary/german-english/vorgang) **unterbrechen**. ( [der Vorgang](https://www.collinsdictionary.com/dictionary/german-english/vorgang) \= [der Verfahren](https://www.collinsdictionary.com/dictionary/german-english/verfahren) ) \[Process\]

Jetzt **sind** wir **direkt**  mit unserem Red Hat System **verbunden.** Ein SSH Schlüsselpaar erlaubt uns etwas **mehr** **Sicherheit** zu **integrieren, weil** **wenn** wir **mit** eine**m** Benutername**n** und eine**m** Passwot arbeiten, ist es oft so, sind diese **anfällig auf Brute Force Angriffe.** Mit eine SSH Shclüsselpaar haben wir **da etwas entgegen gewirkt**. Ich sage jetzt nicht das es super sicher ist aber wir habe etwas Sicherheit integriert.  
   
Gut, haben wir miteinander **abgemacht, dass** wir diese System als Jumpbox brauchen **um** ein Verrbindung auf**zu**bauen **mit** unsere**m** Debian System und ich könnte diese Verbindung aufbauen **mit** user@\<**private**\-IP-Adresse\> wenn ich jetzt die ENTER Taste drücke dann kennen wir das wir müssen das **Kennwort angeben** gebe das Kennwort an und bin nun mit dem Debian System verbunden aber ich möchte jetzt auch **für** diese Verbindung **ein SSH Schlüsselpaar** **einsetzen**.

Wie **gehen wir** denn **davor?**

Zuerst einmal **schließe** ich **die Verbindung** dann **lösche** das Bildschirminhalt. Wir müssen auch **ein Schlüsselpaar generieren** aber das ist **völlig unabhängig von** dem Azure Portal. Ds heißt, wir **herstellen** ein Schlüsselpaar direkt hier auf unsere Red Hat System auch **wiederum** mit SSH.

**ssh-keygen \<wir** kopieren hier das öffentlichen Schlüssen auf unser Debian System**\>**

**\[**der Befhel S S H Bindenstrich KEYGEN .. und drücken wir die ENTER Taste**\]**

   
Und dann könne wir wieder mit diesem Schlüsselpaar arbeiten. Ich zeige Ihnen gleich wie das funktioniert. Jetzt **erhalten** wir die **Information** **wo** **der** private Schlüssel [**abgegelt wird**](https://www.collinsdictionary.com/dictionary/german-english/ablegen). Drücke ich die ENTER Taste und jetzt muss ich die Passphrase **wieder bestimmen**.Und jetzt haben wir **das** Schlüssel**paar** **generiert.**

Und jetzt verwenden wir den folgenden Befehl **damit** wir de**n** **öffentlichen Schlüssel** nun **auf** unsere Debian System **kopieren** können. Wie **gehen wir** denn **davor?**

**ssh-copy-id  user@\<private-IP-[Adresse](https://www.collinsdictionary.com/dictionary/german-english/adresse)\-der-Debian-System\>**

Jetzt wird den öffentlichen Schlüssel kopiert, **es dauert ein paar Sekunden.** Sollt ihr merken, dass ihr die falsche IP Adresse eingegeben hat, dann könnt ihr CTRL+C benutzen **um diese [Vorgang](https://www.collinsdictionary.com/dictionary/german-english/vorgang) zu unterbrechen**. Pfeiltaste nach oben und dann die richtige IP Adresse **[einsetzen](https://www.collinsdictionary.com/dictionary/german-english/einsetzen)**

Nun wird das öffentlichen Schlüssel kopiert und muss ich das Kennwort angeben vo**m Benutzer user**. Das werde ich nun **eintippen** und jetzt wurde das **erfolgrech abgeschlossen** und sehen wir auch **die Betätigung** es wurde ein Schlüssel **hin**zu**gefügt** und wir **erhalten** **die Benachrichtigung,** dass wir SSH **testen** können.

Lassen sie uns doch das  gleich **ausprobieren. Zuerst einmal** de**n Bildschirminhalt löschen** und dann verwenden ich

**ssh  user@\<private-IP-[Adresse](https://www.collinsdictionary.com/dictionary/german-english/adresse)\-der-Debian-System\>**

Ich mucc jetzt nicht mehr eintippen, keine Passphrase eintippen, weil wir bei**m Erstellen von** Schlüsselpaar de**n privaten Schüssel** nicht mit einer Passphrase **geschüzt** haben und wir werden **also** **direkt mit** de**m** Debiansystem **verbunden.** Wir haben diese Verbingung etwas sicherwer gemacht, weil wir nun von unsere**m** Red Hat System **aus** **ebenfalls mit** eine**m** Schüssel**paar** **arbeiten** wenn wir eien Verbindung aufbauen wollen **zu** unsere**m** Debian System.  
                                                        
---

### [Folge 3 \- Mit einfachen Linux Shell Befehlen Informatione sammeln](https://www.youtube.com/watch?v=j0FnE8IPK8M)

Ein weiter**er** Befehl ist \[df\] es **steht für** \[Disk Free\]. Wir sehen die Informationen aber sie sind **schwer zu lesen.** Was sind diese Zahlen? Diese AZahlen sind in ein **1 Kilo Blockformat  Lassen dies uns doch etwas anpassen** \[df \-h\] wo \-h **steht für** Human Readable **damit** wir das besser lesen können und jetzt verwende ich auch \-T d.h. \[df \-hT\] **damit** das Dateisystem sehen.

**Bevor** ich jetzt de**n** **Befehl** verwende **drücke** ich \[CTRL+L\] und jetzt wird **der Bildschirminhalt gelöscht** aber **der Befehl bleibt bestehen**. \[\\sda1\] ist **die Partition** und sie hat **eine Große von** 30 GB und 772 MD **sind verwendet** und **verfügbar** isnt **aktuelle** 28 GB wenn das nicht besser **lessbar** ist.

Wenn Sie jetzt an diesen Befehl mehr Informationen möchten verwenden Sie die \[man\] z.B. \[man lspci\] und Sie **erhalten** detalierte **Informationen** **zu** diesem Befehl. 

Nun möchte ich wissen welche **Module** wurden [**eingebunden**](https://www.collinsdictionary.com/dictionary/german-english/einbinden) (=[einbeziehen](https://www.collinsdictionary.com/dictionary/german-english/einbeziehen)) in unsere Debian System.  
\[lsmode\] **liefert die Antwort** aber diese Aufgabe wird sehr detaliert sein jetzt können wir eine**n Trick anwenden.**  Wiir \[lsmode | \] wo **| das senkrechte** **Strich** heißt das PIPE Symbol und wir lenken **das Result** um in einen Page mit dem Name LESS. Wir können so **seitenweise durchnavigieren.**

Wir können jetzt **weiter navigieren** entweder **mit** der ENTER Taste dann geht es **zeilenweise weiter** oder wir können **die Leerschlagtaste ([der Leerschlag](https://www.collinsdictionary.com/dictionary/german-english/leerschlag) auf die Tastatur)** verwenden.  
Nun möchte ich wissen welche MOUNTs wurden [**ausgeführt**](https://www.collinsdictionary.com/dictionary/german-english/ausfuhren) **() ( \!= [aufführen](https://www.collinsdictionary.com/dictionary/german-english/auffuhren) ).**

**maunten (von das englische Wort mount und das Verb to mount) \=\> das Verzeichnis wurde geauntet** 

Der Befehl **MOUNT** liefert die Information, wir sehen hier die MOUNTs **die** **ausgeführt wurden**. **Ein Beispiel**, \[/dev/sda1\] [diese Partition](https://www.collinsdictionary.com/dictionary/german-english/partition) **wurde gemauntet** **in das [sogenannt(e](https://www.collinsdictionary.com/dictionary/german-english/sogenannt)**) **Rootverzeichnis, das Slash / [indiziert](https://www.collinsdictionary.com/dictionary/german-english/indizieren)** das Root[verzeichnis](https://www.collinsdictionary.com/dictionary/german-english/verzeichnis) und **das Dateisystem** welch**es** verwendet wird ist **EXT4** dann gibt es noch **weitere Verzeichnisse** z.B. \[/sys\] oder **beziehungsweise** \[sysfs\] **wurde gemauntet.**

Ich werde **gleich später** dazu noch etwas sagen.

Wir **verwenden** \[uname \-r\] dann **erhalten** wir den Kernel und die Version. Wenn wir jetzt alles sehen möchten **verwenden** wir \[uname **\-a**\] jetzt wissen wir **es handelt sich hier um** Linux, **keine große Überaschung**, aber es könnte auch ein **Unix** System sein dann der Hausname wird hier [**angezeigt (=angeben, mitteilen)**](https://www.collinsdictionary.com/dictionary/german-english/anzeigen) und dann \[x86\_64\] \[ \_ **underline**\]. Sie können dies**e Informationen** **aufrufen** mit \[lsb\_release \-a\] . 

[**angezeigt (=angeben)**](https://www.collinsdictionary.com/dictionary/german-english/anzeigen) \[Temperatur, Zeit, Wetterlage, Detail, Messwert, Spielstand\]  
[**angezeigt (=bekannt geben)**](https://www.collinsdictionary.com/dictionary/german-english/anzeigen) \[Heirat, Verlobung, **eine [Reklame](https://www.collinsdictionary.com/dictionary/german-english/reklame) machen für** etwas, werben, die Werbung\]

[abfragen](https://www.collinsdictionary.com/dictionary/german-english/abfragen)  eine **relationale Datenbank** abfragen | eine**n** **Rechnersystem** abfragen  
[abfragen](https://www.collinsdictionary.com/dictionary/german-english/abfragen) \*  Nach der **Lektion** die Studenten wurden regelmäßig **auf** die Inhalte **abgefragt**  
[Die Abfrage](https://www.collinsdictionary.com/dictionary/german-english/abfrage)  
Wenn wir eine nur weniger verschiedene **SQL Abfrage eingeben**, bekommen wir ein ganz anderen **Abfrageergebnisse** auf den Bildschirm

Ich habe **vorhin (gerade erst, soeben)** das Verzeichnis \[/proc\] **erwhänt.** Ich rufe da**s Verzeichnis** auf **mit** \[ls /proc\] und hier sehen wir verschiedenen Informationen. Das Verzeichnis /proc **ist kein Verzeichnis im eigentlixhen Sinn** sondern **bildet** **Parameter** de**s** Kernel**s ab** und kann [**dementsprechen**](https://www.collinsdictionary.com/dictionary/german-english/dementsprechend) **(=[demnach](https://www.collinsdictionary.com/dictionary/german-english/demnach))** auch **zur Abfrage** de**s** Kernel**s.**

Eine wichtige Information de**s** \[/proc\] Verzeichnis ist da**s** **sogenanntes virtuell**e Verzeichniss \[/sys\]. Diese Verzeichnis ist **ebenfalls** ein speziell**es** Verzeichniss. **Das virtuelle Dateisystem** /sys **exportiert** endlich **Systeminformationen** **über** Treibermodule \[DRIVERs\] des Kernels (hinein) für den Benutzer sichbare Verzeichnes nämlich \[/sys\].

[das Laufwerk](https://www.collinsdictionary.com/dictionary/german-english/laufwerk)  | [die Festplatte](https://www.collinsdictionary.com/dictionary/german-english/festplatte) | **Gerätedateien** \[DEVICE FILES\] | eien Festplatte [**partitionieren**](https://www.dwds.de/wb/partitionieren) **|**   
eine [Partition](https://www.collinsdictionary.com/dictionary/german-english/partition) (auf eine Festplatte ) erstellen  
etwas **unterhalb von** etwas stellen/darstellen  
Logische und pysische Geräte unter eine Verzeichnis [abbilden](https://www.collinsdictionary.com/dictionary/german-english/abbilden) (darstellen, schildern, zeichnen)  
[**der Treiber, die Treiber**](https://www.collinsdictionary.com/dictionary/german-english/treiber) \[DRIVER(s)\]

Dann haben wir noch das \[/dev\] Verzeichnis, [**sowohl**](https://www.collinsdictionary.com/dictionary/german-english/sowohl) **physische [als auch](https://www.collinsdictionary.com/dictionary/german-english/sowohl)** **logische Laufwerke** werden unter Linux **aus** **Gerätedateien** \[DEVICE FILES\] **unterhalb von** /dev **dargestellt (=repräsentiert).**  
Also, wir haben physische Geräte beispielsweise ein**e Festplatte** und wir sehen hier eine estre Festplatte sda und diese Festplatte wurde **partitioniert** **mit** sd1, sda14 und sda15.

Wir können auch also sagen alle Geräte, physische und auch logische Geräte werden unter /dev [abgebildet](https://www.collinsdictionary.com/dictionary/german-english/abbilden). \[cd/proc\],  \[cd\] **steht für** \[CHANGE DIRECTORY\], **damit** das **in** **der** \[/proc\] Verzeichnis **navigieren** **können** das wird auch jetzt auch **angezeigt**. Wenn Sie **übrigens** weiteren Informationen möchten **zu** diesem Verzeichnis, verwenden \[man procfs\] und sie **erhalten** mehr **Informationen über** dieses sogenannte **pseudo** **Filesystems**.

Nun geht es aber weiter, ich möchte einmal Informationen aufrüfen **zu** de**n geladenen Hardware** oder auch [**Treiber**](https://www.collinsdictionary.com/dictionary/german-english/treiber) \[DRIVER\]. **Dazu** verwenden wir \[cat devices\] und jetzt erhalten wir eine Liste die wird un**s angezeigt**. Wir sehen die verschiedenen Devices z.B. \[/dev/tty\], \[dev/console\] **dann** **geht’s weiter drunter** haben wir die Blockdevices, etc. 

[**anwenden**](https://www.collinsdictionary.com/dictionary/german-english/anwenden) (=[gebrauchen](https://www.collinsdictionary.com/dictionary/german-english/gebrauchen), benutzen) | (Theorie, Prinzipien, Regel, Ehfahrung, Einfluss)  
[**verwenden**](https://docs.google.com/document/d/11D-wPadVH4paCAheRfwl1i-mZqd3Gkz54Ivg12OeWw0/edit#) (Methode, Mittels, Mühe/Fleiß **auf** etwas \-, **Zeit** **auf** etwas \-)

**Übrigens** \[cat\] **steht für** CONCATENATE, das bedeutet eigentlich das wir zwei Dateien **gleichzeitig anzeigen** können oder wir können \[cat\] also **anwenden** um eien Datei **einfach** **direkt** an Terminal **aus**zu**geben.**

[der Kernel](https://www.collinsdictionary.com/dictionary/english-german/kernel)   
**Datei**/Dokumente [untersuchen](https://www.collinsdictionary.com/dictionary/german-english/untersuchen) (=[inspizieren](https://www.collinsdictionary.com/dictionary/german-english/inspizieren))  
Information(en) **zu** etwas **erhalten**  
Information(en) **[übergeben](https://www.collinsdictionary.com/dictionary/german-english/ubergeben) (=**[überreichen](https://www.collinsdictionary.com/dictionary/german-english/uberreichen)**) (=[überweisen](https://www.collinsdictionary.com/dictionary/german-english/uberweisen) )** \[Geld, Patient, Gehalt\]

\[cat cmdline\]  
Jetzt **untersuchen** wir **die Datei** \[cat cmdline\] und jetzt **erhalten** wir die **Information** **zu** unserem \[Boot Image\]. Dise Information wurde **während** de**s** Start**s** de**s** Kernel**s übergeben** damit der Kernel weiß, was gestarted werden muss.

[das Resultat](https://www.collinsdictionary.com/dictionary/german-english/resultat) | [das Ergebnis](https://www.collinsdictionary.com/dictionary/german-english/ergebnis) (**zu** keine \- **früheren | kommen, ohne \-**) [ergebnislos](https://www.collinsdictionary.com/dictionary/german-english/ergebnislos) \=  [resultatlos](https://www.collinsdictionary.com/dictionary/german-english/resultatlos)   
[anschauen](https://www.collinsdictionary.com/dictionary/german-english/anschauen) (sich etwas (dat) anschauen / [betrachten](https://www.collinsdictionary.com/dictionary/german-english/betrachten))  | [betrachten](https://www.collinsdictionary.com/dictionary/german-english/betrachten) **bei nährem** Betrachten | jdn/etwas **als** etwas brachten, ich betrachte ihn **als** Freund

\[cat modules\] \[ | less \] \[Q\]  
**Schauen** wir uns \[cat modules\] **an.** Es zeigt alle **geladenen Module** an und das ist ein**e** **große Liste**, damit wir das besser sehen können, verwenden wir das PIPE Symbol und lenken **das Resultat** um in LESS und jetzt können wir **seitenweise navigieren**. [Das Wort](https://www.collinsdictionary.com/dictionary/german-english/wort) (END) **in Klammer** zeigt an dass, wir **am Ende der Augbage** sind. **Übrigens** ich habe dies**e Augabe verlassen** mit der Taste Q.

[**hierbei**](https://www.collinsdictionary.com/dictionary/german-english/hierbei) (=[währenddem, währenddessen](https://www.collinsdictionary.com/dictionary/german-english/wahrenddem)) \[**bei diese Gelegenheit**\]  
sich um etwas handeln, Es sich um etwas haldelt

\[Q\] **steht für** QUICK. Jetzt können Sie **selbstverständlich** noch wietere **Informationen aufrufen** z.B. wenn Sie sich in \[/dev\] Verzeichnis **umschauen** möchten, verwenden Sie \[ls /dev/ | less\] oder dann vielleicht  \[ls /dev/cdrom\] und dann wird **uns angezeigt** dass, es sich [**hierbei**](https://www.collinsdictionary.com/dictionary/german-english/hierbei) um einen **symbolischen Link** handelt. 

**symbolisches Link**  
[**das Format**](https://www.collinsdictionary.com/dictionary/german-english/format) **| anhand von | farblische Interpretation | [aufweisen](https://www.collinsdictionary.com/dictionary/german-english/aufweisen)**   
dieses Wort **weist es auf** dass, der Schriftsteller meinte es wirklich ganz anders als wir zuerts uns vorgestellt haben.

\[ls \-la /dev/cdrom\]  
\-la **steht für** LONG-LISTING **Format**. Ich sehe dass es **anhand von** este mal diese Farbe aber was wichtiger ist hier haben wir ein File. Diese **farblische Interpretation** zeigt oder **weist** daraufdass, es ein **symbolisches Link** ist.

[**thematisieren**](http://thematisieren) (**über** etwas [**besprechen**](https://www.collinsdictionary.com/dictionary/german-english/besprechen))  
(=zum Thema, **Gegenstand einer Diskussion machen**; (eine Angelegenheit) **zur Sprache bringen**)  
[**miteinander**](https://www.collinsdictionary.com/dictionary/german-english/miteinander) (= [**gemeinsam**](https://www.collinsdictionary.com/dictionary/german-english/gemeinsam)**, [zusammen](https://www.collinsdictionary.com/dictionary/german-english/zusammen)**)

Was ein **symbolisches Link** ist ~~dass,~~ **das** werden wir später [**miteinander**](https://www.collinsdictionary.com/dictionary/german-english/miteinander)  [**thematisieren**](http://thematisieren)**.**

das **Homeverzeichnis | zu** de**m** **Homeverzeichnis (zurück) navigieren**  
\[ ls /dev/sd\* \]   
\[cd\] ohne Argument  
Sie können selbverständlich auch einmal alle DEVICES **aufrufen** die SD beginnen und dann wervden alle DEVICES **angezeigt** mit SD beginnen. Wenn Sie **zurück navigieren** wollen **zu** Ihre**m** **Homeverzeichnis** verwenden Sie \[cd\] ohne Argument. 

**sich über (von)** etwas **informieren**  
**Befehle** **einsetzen | Befehle** **antippen**  
[**nachsehen (=nachschauen)**](https://www.collinsdictionary.com/dictionary/german-english/nachsehen) 

Nun kennen sie einige **Befehle** die sie **einsetzen** können um sich **ganz einfach** locker und gemütlich **über** ihr Linux System **informieren** zu können. Wenn Sie denken muss ich nun alle diese Befehle **abtippen** oder **nachschauen..**

[**anschließend**](https://www.collinsdictionary.com/dictionary/german-english/anschliessend) **([danach](https://www.collinsdictionary.com/dictionary/german-english/danach), [hinterher](https://www.collinsdictionary.com/dictionary/german-english/hinterher))**  
**das Suchfeld | nach** etwas **im Suchfeld suchen**  
Nein, ich habe diese Befehle in einem Text. **Navigieren** Sie **zu** [github.com](https://github.com/) [**anschließend**](https://www.collinsdictionary.com/dictionary/german-english/anschliessend) suchen Sie hier **im Suchfeld nach** Tom Wechsler dann navigieren Sie zu Users und hier werde Tom Wechsler **angezeigt.**

ein neu**es** Repo(sitory) [**eröffnen**](https://www.collinsdictionary.com/dictionary/german-english/eroffnen) **(=beginnen**, Ausstellung, **Konkursverfahren)**  
[**Darin enthalten**](https://www.collinsdictionary.com/dictionary/german-english/enthalten) **| [die Beschreibung](https://www.collinsdictionary.com/dictionary/german-english/beschreibung)**  
Ich werde ein neu**es** Repository **eröffnen**, das Repository **wird heißen** [LinuxOnAzure](https://github.com/tomwechsler/LinuxOnAzure). [**Darin enthalten**](https://www.collinsdictionary.com/dictionary/german-english/enthalten) wird eine Datei sein mit den Befehlen und dann auch **ein paar Beschreibungen** die ich in diese Video verwendet habe.

---

### [Folge 2 \- Mit SSH eine Remotesitzung erstellen](https://www.youtube.com/watch?v=Ou4yEaaygnQ)

### [Folge 1 \- Aufbau einer Testumgebung](https://www.youtube.com/watch?v=77khOi9yAyI)

**Computer** kann **Anweisungen** **blitzschnell ausführen.**

**die Systemsteuerung**  
Die Systemsteuerung ist **die (grafische) Oberfläche** auf Windows wo man vielen **Settings zugreifen** und **umstellen** kann.

Brauchen wir bei der Linux Systeme die wir aufbauen immer öffentliche IP Adresse? Nein, brauchen wir nicht, aber lassen wir es uns **Schritt für Schritt angehen**. Ich möchte Ihnen einmal zeigen wie zuerst eine **Verbindung** **mit SSH aufbauen** kannt. Mit Linux SSH **Unterstützung** ist doch **integriert** aber wenn sie **beispielsweise** mit ein **Windows System arbeiten,** dann können Sie **u.a.** Mit Putty arbeiten oder Sie können di Linux Unterstützung **installieren**.

**Ich zeige ihnen wie es funktioniert**. **Rechtsklick auf die** Start**oberfläche** **navigieren** zu **Ausführen (RUN) geben ein** “Control Panel”..

Lassen wir uns mal **navigieren zu** Program und Features **um** die Windows Features **zu aktivieren** und **deaktivieren** und dann werde **eine Liste generiert**. Navigieren wir (ganz) nach unten um das Windows **Subsystem** für Linux **einzuschalten,** der **enthalten** unter anderen (u.a.) **SSH Unterstützung.**   
Sie brauchen hier eine neue W10 **Version**, damit dies zu Verfügun steht. 

Wenn sie jetzt ein älteres Windows System **im Einsatz haben**, **wenden** sie beispielsweise Putty, das könne sie **kostenlos herunterladen**. 

[**die Zwischenablage**](https://www.collinsdictionary.com/dictionary/german-english/zwischenablage) (the clipboard)  
**Beginnen wir** mit ein **Verbindungsaufbau zu** unserem Debian System. **Dazu** **kopieren** ich mir die öffentliche IP-Adresse **in die Zwischenablage.** Ich [öffnen](https://www.collinsdictionary.com/dictionary/german-english/offnen) nun das Windows Terminal, **das** ist ein **Werkzeug, welches** relativ neu ist. Sie finden dieses Werkzeug in Microsoft Store. 

Jezt geht los. **Verwende** ssh dann, tom oder Ihr**er Benutzername**  **@ (/et/),**  dann die öffentliche IP-Adresse und nun wo Sie **den Fingerprint annehmen.** Ich bin mit der Debian System **ebenfalls** verbunden über die öffentliche IP-Address und dann ich **schließe** diese SSH wieder **mit** exit.  

Ich möchte Ihnen zeigen ich brauche keine öffentliche IP-Adresse um mit the Debian System eine Verbindung aufzubauen also ich werde zuerst diese öffentliche IP-Adresse **entfernen. Es hat der Vorteil**   
das einmal **wenige kosten generiert** werden und das diese System dann **öffentlich** **nicht erreichbar** ist, das heißt **es ist nicht direkt eine Gefahr ausgesetzt**. Nach ich auf das Link klicke **wird** **es umgesetzt (=implementiert, ausgeführt)** und ich werde auch gleich diese IP-Adresse **auslöschen (löschen)** wie bereits **erwähnt.**

Ich warte nun bis diese **Konfiguration abgeschlossen** **ist**.(abschließen) und das wird das Portal zeigen mit einer **erfolgreichen Benachrichtigung**.

Die [Änderung](https://www.collinsdictionary.com/dictionary/german-english/anderung) (Kleidungsstück, Gebäude **an+dat/gen,in jdm**) 

Das System wird automatisch die Änderungen speichern wenn der Benutzer es ausschaltet ohne auf eine Bestätigung zu warten.

**ein neue Register öffnen**  
Navigiere Sie zurück zu dem Terminal um **ein neue Register zu öffnen** dann müssen Sie **die Fingerprint** wieder **annehmen** und **die Kennwort** **eintippen**. Jetzt **schließe** ich diese **Session mit** EXIT  
und dann ebenfalls das Register wieder mit exit. Lassen uns nun noch mal zur **Übersicht zurückgehen**.

Der Debian System hat kein**e IP Adresse** nicht mehr und das ist, **von Standpunkt der Sicherheit,** sehr gut aber wir können **trotzdem** eine Verbindung aufbauen.

[Azure Tip: Linux on Azure \- Folge 3 \- Mit einfachen Linux Shell Befehlen Informationen sammeln](https://www.youtube.com/watch?v=j0FnE8IPK8M) 

[**bewähren**](https://www.collinsdictionary.com/dictionary/german-english/bewahren_2) (**sich** **\-**, Gerät, Mthode, Plan, Investition, Fleiß, Auto, **sich gut/schlecht \-**, **sich lohnen**)   
**\!=**  
[**bewehren**](https://www.collinsdictionary.com/dictionary/german-english/bewehren) ()  
**Beton** bewehren [(=ihm durch Eisen**einlagen** Zugfestigkeit verleihen)](https://www.dwds.de/wb/bewehren)**\- [das Bauwesen](https://www.collinsdictionary.com/dictionary/german-english/bauwesen) | bewehrter Beton**  
**Mit Schutz gegen Angriffe versehen** (=ausstatten, jdn **mit** etwas \-, **mit** etwas \- **sein**)

**Heute geht es darum** dass wir ganz einfach mit Linux ~~bewähren~~ **bewehren.** Wir **erinnern uns** wir haben ein **Testumgebung** aufgebaut und es gibt **darin** zwei System**e**. Ich habe mit ihnen abgemacht..und genau das ist auch **aktuell** immer die Situation.

[abmachen](https://www.collinsdictionary.com/dictionary/german-english/abmachen) (=entfernen, Schnur, Kette, [**herunternehmen**](https://www.collinsdictionary.com/dictionary/german-english/herunternehmen))  
Ich habe die beide Linux Systeme **abgemacht / heruntergenommen**

[der Ordner](https://www.collinsdictionary.com/dictionary/german-english/ordner) |  [das Verzeichnis](https://www.collinsdictionary.com/dictionary/german-english/verzeichnis) ( das **Home**verzeichnis )  
Jetzt können wir mit ganz **einfache Befehle uns informieren. “Ls”,** es ist ein **Befehl um der Inhalt aus der aktueller Ordner aufzulisten**. Es ist ein Listbefehl aber hier es wird nichts **angezeigt** , weil in meine **Homeverzeichnis** git es nur **Datei,** die **versteckt sind.** Wenn wir die **vestekten Derein** anzeigen möchten verwenden wir ein minus a (ls \-a) wo a **steht für** alles und wenn ich auch  mit ms \-**l**a **kombinieren, da** \-l steht für [lange Auflistung](https://www.collinsdictionary.com/dictionary/german-english/auflistung).

[die Ausgabe](https://www.collinsdictionary.com/dictionary/german-english/ausgabe) (=[der Ausdruck](https://www.collinsdictionary.com/dictionary/german-english/ausdruck) von Computer) (die Ausgabe **auf das Bildschirm**)   
Jetzt siet **die** **Ausgabe** (das Output) so aus**,** Ich wollte ihnen aber **lscpi** **zeigen.** Wenn sie jetzt zu diesem Befehl **lspci** mehr Informationen möchten, verwenden sie die **main lspci** und sie **erhalten detalierte Informationen zu** diese Befehl laspci.

[Die Schnittstelle](https://www.collinsdictionary.com/dictionary/german-english/schnittstelle) (USB oder PCI Schnittstellen, **grafische/serielle** \-) | der Befehl  
Ein weiter**es** **Befehl** ist **lsusb.** Es zeigt uns USB **Schnittstellen** wenn sie **vorhanden** sind aber **in diesem Fall** zeigt  es uns \[lsusb: command not found\] **das heißt** ich **habe zu wenig Rechte** **um** diesen **Befehl** **aus**zu**führen**.

[thematisieren](http://collinsdictionary.com/dictionary/german-english/thematisieren) | [eine Angelegenheit **zur Sprache Bringen**](https://www.dwds.de/wb/thematisieren)     
Also verwende ich \[sudo\] und dann **Abstand** \[lsusb\] und **drücke** **die Entertaste** und gebe das **Kennwort für** meiner Benutzer. Was \[sudo\] bedeutet, dass werden wir **zu einem späteren Zeitpunkt [thematisieren](https://www.dwds.de/wb/thematisieren).**

[**indem**](https://www.collinsdictionary.com/dictionary/german-english/indem)  (=dadurch, dass) **|** (= **während der ganzen Zeit**) indem er sich hinsetzen, sagte er..  
**die Tabulatortaste**   
[**sämtlich**](https://www.collinsdictionary.com/dictionary/german-english/samtlich) **(vollständig, alle)** |  **[einsetzen](https://www.dwds.de/wb/einsetzen)** (eine**n** **Befehl**, etwas **auf Spiel setzen**/**gebrauchen**)    
Es gibt keine \[lsusb\] auf ein Debiansystem, **das können wir überprüfen** **indem** (dass) wir ls **eintippen** und zwei mal **die Tabulatortaste** drücken. Es werden jetzt **sämtliche** Befehle **aufgelistet** die mit \[ls\] beginnen und klar \[lsusb\] **fehlt.** Sie sehen **also** das Befehl \[lsusb\] **steht** auf ein Debiansystem **nicht zu Verfügung.** Wir können de**n Befehl einsetzen unten** RedHat aber **nicht** **unten Debiansysteme.**

---

