# 1DT308-1DT902
TeamProject

Grupp 16 - Smart street lights
Medlemmar: Kim Nygren, Naseem Qurban Ali, Jan Abdulkader och Jafar Soltani
Program: Mjukvaruteknik och datateknik
Kurs: Introducerande project (1DT308 och 1DT902)

Introduktion
Projektet handlar om att bygga en prototyp av smart street lights så att rörelse av objekt kan detekteras med PIR sensor. Objekt i det här sammanhanget är bil, cyklist eller gående osv. Beroende på objekts rörelse kommer ljusstyrkan på belysningen kommer att minskas eller ökas.

Bakgrund och idé
Gatubelysning är en jättestor fråga som Kalmar kommun har. Det är både en trygghet- och säkerhetsfråga. Idag kostar det mycket och det kräver en hel del manuellt arbete för att det här ska fungera. Särskilt när belysningen går sönder kan det ta lång tid innan felen åtgärdas eftersom man måste vara på plats och skriva ner detta. Det sker således många steg innan lamporna kunde fixas.
Idén av denna projekt är att göra gatubelysningen smartare, det innebär att belysningen kan tändas automatiskt eller ha olika ljusstyrkor beroende på om det finns närvaro eller inte. Bilister kan alltså lätt upptäcka om det finns fotgängare på vägen eller inte. På så sätt kan energi och manuellt arbete reduceras men man kan fortfarande känna sig trygg på gatorna. I det här projektet vill vi även kontrollera och rapportera belysningens status på ett smidigt sätt och ifall om belysningen går sönder kan kommunen ha bättre förutsättning att checka av situationen.

Metod
Två olika sensor används, den ena är PIR sensor för att detektera rörelse och den andra är photoresistor (LDR) för att känna av om det är dagtid eller kvällstid. Dessa sensor ska kopplas till varandra och sedan till LED. Lopy och Lora antenn används för att kunna skicka data mellan enheter och servern och på det sättet kan lamporna kommuniceras med varandra.

requirements.md
hardware.md
test.md
setup.md
timelog.md


Resultat och diskussion
Video : Grupp 16 Smart Street Lights.
Resultat blir som vi förväntar oss. När alla komponenter kopplas ihop så kör vi vår main.py kod för att se om allt funkar som den ska. Photoresistor funkar för automatisk släckning/tändning för dagtid och kvällstid. Pir sensor styr lampornas ljusstyrka, normalt är lampornas ljussturkan 25% när det inte finns rörelse omkring. Lampornas ljusstyrka blir sedan 100% när pir sensor upptäcker rörelse.
För prototypen använder vi 2 lopy och 6 stycken lampor. Första lopy kopplas till 3 lampor och den andra lopy kopplas sedan till resterande lampor.  När PIR-sensor känner av rörelse så tänds de 3 första lampor och sedan skickas ett meddelande via lora till den andra lopy för att de resterande lampor också ska vara på. När det inte finns rörelse så återgår alla lampor till 25% ljustyrka.
Pir senor känner av rörelse och skickar sedan vidare signal men eftersom sensorn är värmekänslig så kan den fortsätta skicka värde exempelvis även om det finns inte rörelse. Om vi ska ha pir sensor på riktiga beslysningen så kanske måste placera det i en box så att den inte blir påverkad av andra faktorer som vind och fåglar osv.

Vi får ett värde av den trasiga lampan men det funkar än så länge för en lampa som kopplas till en lopy. Vi gör en extra analog pins mellan resistorn och lampan och denna pins är bara för att kolla om lampan är trasig eller inte. När lampan inte är trasig då får vi olika värden (26, 25, 24 osv) enligt bilden nedan. Denna information skickas inte till servern eftersom vi bara är intresserade av information om den trasiga lampan.

Vi testar en trasig lampan genom att lampan tas bort. Anolog pins för lampan ger oss ett värde och det här värdet är samma hela tiden, det vill säga 0. Vi kan sedan skicka värdet till servern TTN  (se bilder nedan)


När den ena lampan känner av rörelse så skickar sedan ett meddelande till andra lampan så att den också ska tändas. Förutom att värdet av den trasiga lampan skickas till servern TTN så har meddelandet till andra lopy skickats med till servern. Det meddelandet gör att det blir mycket onödig data till servern som vi inte vill ha.
I verkligheten kanske det här sättet att skicka information om en trasig lampa är inte omptimalt, då ska man koppla lampan till lopy och gör sedan en extra anolog pins för den. Det kräver möjligen högre spänning för gatubeslysning än vad lopy klarar av vilket gör att lopy kan gå sönder om belysningen kopplas till lopy. Istället för att göra extra anolog pins så kanske man har en temperatursenor under belysningen för att se om att den är tänd eller inte.