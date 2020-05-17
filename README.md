# DevOpsTest

	A feladat elvégzését a statikus analízist végző SonarQube (Community Edition) telepítésével kezdtem. A telepítést a dokumentáció alapján végeztem, aminek eredményeként a localhost:9000 címen elérhetővé vált a SonarQube szerver. Ezután telepítettem a SonarScanner for MSBuild nevű programot, ami a forráskód analízisét végzi. A sikeres analízishez a SonarScanner és az MSBuild elérési útvonalának elérhetőnek kell lennie a PATH változóban (utóbbi megtalálható a Visual Studio telepítési könyvtárában, de külön is telepíthető). A beállítások után a következő 3 parancsot adtam ki a projekt gyökérkönyvtárában:

1.	SonarScanner.MSBuild.exe begin /k:"IET-HF" /d:sonar.host.url="http://localhost:9000" /d:sonar.login="<token>"
2.	MsBuild.exe /t:Rebuild
3.	SonarScanner.MSBuild.exe end /d:sonar.login="<token>"

A lefutásuk után (~20 perc) a SonarQube felhasználói felületéhez visszatérve és az eredmények feltöltésének végeztével (~3 perc) elérhetővé vált a statikus analízis eredménye:
 

	Az eredmények alapján javítottam sebezhetőségeket és bugokat is. Elsősorban critical vagy major megjelölésű hibákkal/figyelmeztetésekkel foglalkoztam. Ezen kívül a javított hibákat tartalmazó és a hozzájuk szorosabban kapcsolódó osztályok manuális átvizsgálását is elvégeztem (ez alól kivételt képeznek az extrém méretű osztályok (2-3000 sor)). A manuális vizsgálat eredményeként több osztályban is végeztem kisebb-nagyobb refaktorálást. A javítások végeztével a SonarQube összefoglaló oldala:
 

	A SonarQube rendkívül hasznos eszköznek bizonyult kódhibák felderítésére és javítására olyan méretű kódbázisban is, amelynek teljes átnézésére manuálisan esély sem lenne. 
