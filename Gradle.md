Ist ein Build-Tool
### Warum werden Build-Tools benötigt 
Bei manueller Compilation von COde müssen alle biblittheken angegeben werden, die im Code verwendet werden. Das ist sehr aufwändig und fehleranfällig. Build-Tools machen das compilieren einfacher, fehler freier und weniger aufwändig. 
Sie können auch den Prozess des verpackens der Anwendung in deployable Versionen übernehmen. 
### Gradle
Kann die Aufgaben des compilieren, testen und verpackens der Anwendung übernehmen. 
Man muss Gradle mitteilen, was für eine Art von Anwendung man baut, welche Abhängigkeiten diese Anwendung hat (Libraries, etc.) und spezielle compile und test Optionen. 
Gradle verwendet einen Code-first ansatz, was das erstellen einfacher macht, als bspw Maven. 
- settings.gradle: Richtet High-Level Konfigurationen für das Prjekt ein, wie bspw. den Projektnamen. 
- build.gradle: Build-Script Konfiguraiton. Sie beschreibt die Anwendung, so dass gradle sie bauen kann. 
- gradlew / gradlew.bat:  Gradle wrapper skritpe. Lassen einen ein Anwendung bauen, ohne dafür gradle herunterladen zu müssen.
### Prjects, build scripts, tasks & plugins
Ein Projekt ist ein Konzept auf höchsteer Stufe. Es ist in Container für alles, was gradle üüber unsere Anwendung weiß.
Jedees Projekt kann ein build script haben. Hier werden gradle informationen über die Anwendung mitgeteilt. 
Tasks sind individuelle build-actions, die von der Kommandozeile aus aufgerufen werden können. 
Wenn plugins in einem build script angwewendet werden fügen sie automatisch tasks zum projekt hinzu.
### Groovy
Ist eine Sprache, die auf der JVM läuft. 
Groovcy ist eine Sript-sprache, also kann man code außerhalb einer Klasse verwenden.
Sie ist dynamisch getypt, als  kann das def keyword verwendet werden, anstatt einen tyoen anzugeben.
### Building 
Für Java Anwendungen wir das Java Plugin über die plugins closure eingebunden. Das erlaubt das bauen von Java Projekten.
Damit gradle weiß, welche Klasse die Main Klasse ist kann dies angegeben werden. Dadruch kann die entstehende jar auch ausgeführt werden. 
### Dependencies
Abhängigkeiten, die nicht standardmäßig mit Java ausgeliefert werden müssen über gradle deklariert und eingebunden werden, um sie zu verwenden. 
Die geschieht in der dependencies closure.
### Repositories
Gradle lädt deklarierte Abhängigkeiten automatisch aus dem Internet herunter. Um zu wissen, wo die gewünschten libraries liegen müssen die repositories ebenfalls angegeben werden. Dies geschieht in der repositories closure. 
MavenCentral() ist der standard. Es können aber ebenso custom repositories angegeben werden.  
### Multiproject Build
Um aus einem einfache gradle Projekt ein mutliprojekt zu machen muss man lediglich in der settings.gradle des Hauptprojekts ```include 'name des subprojekts'``` eingeben und darufhin ```gradle projects``` ausführen.
allprojects closure in der parent build.gradle wendet einstellungen auf alle subprojekte im Gesamtprojekt an. Um spezeille Tasks ausführen zu lassen kann man in jedem Subprojekt eine build.gradle erstellen, die die gewünschten Tasks ausführt. 
### Lifecycle
1. Initialization
2. Configuration
3. Execution
In der initialisierungsphase wird die settings.gradle ausgeführt, um herauszufinden, welche Projekte ausgeführt werden müssen. 
Anschließend, in der Configuration phase, wird zunächst die prent gradle ausgeführt und schließlich die subporojects in der Reihenfolge, in der sie deklariert sind.
