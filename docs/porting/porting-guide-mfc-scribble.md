---
title: 'Průvodce přenosem: MFC Scribble | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe0ae0580be4ab062e3ff7ee0cedfb42e201272d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="porting-guide-mfc-scribble"></a>Průvodce přenosem: MFC Scribble
Toto téma je první několik témat, které vám představí postup upgradu pro projekty Visual C++, které byly vytvořeny starší verze sady Visual Studio pro Visual Studio 2017. Tato část představuje příklad, počínaje velmi jednoduché projektu a přesunutí chcete trochu složitější proces upgradu. V tomto tématu jsme fungovat prostřednictvím procesu upgradu pro konkrétní projekt, Klikyháky MFC. Je vhodné jako základní informace o procesu upgradu pro projekty C++.  
  
 Každá verze nástroje Visual Studio zavádí možné nekompatibility, které může zkomplikovat přesunutí kódu ze starší verze sady Visual Studio na novější. Někdy jsou požadované změny v kódu, proto musíte znovu zkompiluje a aktualizujte kód a někdy jsou požadované změny do souborů projektu. Když otevřete projekt, který byl vytvořen s předchozí verzí sady Visual Studio, Visual Studio automaticky zeptá, jestli se má aktualizovat na nejnovější verzi projekt nebo řešení. Tyto nástroje obvykle upgradovat pouze soubory projektu; Neměňte vašeho zdrojového kódu.  
  
## <a name="mfc-scribble"></a>MFC Scribble  
 MFC Klikyháky je dobře známé vzorku, který byl zahrnut v různých verzích Visual C++. Je jednoduchou kreslení aplikaci, která ukazuje některé základní funkce MFC. Existují různé verze je k dispozici, včetně i spravované a nativní kód verze. V tomto příkladu jsme nalezených starší verzi Scribble v nativním kódu v sadě Visual Studio 2005 a otevřít v aplikaci Visual Studio 2017.  
  
 Před pokusem o upgrade, ujistěte se, že máte nainstalovaný Windows Desktop zatížení. Spusťte instalační program sady Visual Studio (vs_installer.exe). Jedním ze způsobů spusťte instalační program je chcete vybrat soubor | Nový projekt a přejděte do dolní části seznamu nainstalovaných šablon, dokud nebude najdete v části "Otevřete instalační program Visual Studio". Po otevření instalační program se zobrazí všechny dostupné úlohy. Pokud není políčko pro pracovní vytížení Windows Desktop, vyberte ho a klikněte na tlačítko Upravit v dolní části okna. 


 Dále vytvořte zálohu celé řešení a veškerý jeho obsah. 
 
 Nakonec jsme potřebné při rozhodování o konkrétní metody upgradu. Pro složitější řešení a projekty, které nebyly upgradovány po dlouhou dobu měli byste zvážit upgrade jedné verze sady Visual Studio v čase. Tímto způsobem můžete zúžit kterou verzi sady Visual Studio zdrojem potíží. Pro jednoduché projekt je vhodné pokusu o otevření v nejnovější verzi sady Visual Studio a povolení v Průvodci převést projekt. Pokud to nefunguje, zkuste upgrade jedné verze současně, pokud máte přístup k příslušné verze sady Visual Studio.  
  
 Všimněte si, že můžete také spustit devenv na příkazovém řádku, pomocí `/Upgrade` možnost, místo použití Průvodce aktualizovat projekty. V tématu [spínače/upgradu (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe). Který může být užitečná při automatizaci procesu upgradu pro velký počet projekty.  
  
### <a name="step-1-converting-the-project-file"></a>Krok 1. Převádění souboru projektu  
 Když otevřete starý soubor projektu ve Visual Studio 2017, Visual Studio nabízí převést soubor projektu na nejnovější verzi, která jsme přijata. Zobrazilo se dialogové okno následující:  
  
 ![Posuďte projektu a řešení změny](../porting/media/scribbleprojectupgrade.PNG "ScribbleProjectUpgrade")  
  
 Nám upozornění, že cíl Itanium není k dispozici a nebudou převedeny došlo k chybě.  
  
```Output  
Platform 'Itanium' is missing from this project. All the configurations and their file configuration settings specific to this platform will be ignored. If you want this platform converted, please make sure you have the corresponding platform installed under '%vctargetpath%\platforms\Itanium'.Continue to convert this project without this platform?  
```  
  
 V době, kdy byla vytvořena předchozí Scribble projektu se Itanium důležité cílové platformy. Platforma Windows nepodporuje Itanium, proto jsme zvolili pro pokračování bez podpora platformy Itanium.  
  
 Visual Studio se následně zobrazí migrace sestavu se seznamem všechny problémy s původní soubor projektu.  
  
 ![Upgrade sestavy](../porting/media/scribblemigrationreport.PNG "ScribbleMigrationReport")  
  
 V takovém případě problémy byly všech upozornění a Visual Studio potřebné změny provedené v souboru projektu. Velký rozdíl jde projektu je, že nástroj pro sestavení změněn z vcbuild k msbuild. Tato změna byla poprvé použita v sadě Visual Studio 2010. Další změny zahrnují některé změny uspořádání pořadí prvků v samotném souboru projektu. Žádné problémy vyžaduje další pozornost pro tento projekt jednoduché.  
  
### <a name="step-2-getting-it-to-build"></a>Krok 2. Načítání sestavení  
 Před vytvořením, jsme zkontrolujte sada nástrojů platformy, abychom věděli, jaké verze kompilátoru používá systém projektu. V dialogovém okně Vlastnosti projektu v části **vlastnosti konfigurace**v **Obecné** kategorie, podívejte se na **sada nástrojů platformy** vlastnost. Obsahuje verzi sady Visual Studio a číslo verze platformy nástroj, který v tomto případě je v141 pro Visual Studio 2017 verzi nástroje. Při převodu projekt, který byl původně kompilovat s Visual C++ 2010 2012, 2013 nebo 2015, sady nástrojů není automaticky aktualizován do sady nástrojů Visual Studio 2017.   
  
  Chcete-li přepínač na kódování Unicode, otevřete vlastnosti projektu v části **vlastnosti konfigurace**, vyberte **Obecné** části a vyhledejte **znaková sada** vlastnost. Změňte z **vícebajtové znakové sady** k **použít sadu znak Unicode**. Účinek této změny je to teď _UNICODE a jsou definovány makra kódování UNICODE a _MBCS není, které můžete ověřit v dialogovém okně Vlastnosti v části **C/C++** kategorie v **příkazového řádku** vlastnost.  
  
```Output  
/GS /analyze- /W4 /Zc:wchar_t /Zi /Gm- /Od /Fd".\Debug\vc141.pdb" /Zc:inline /fp:precise /D "_AFXDLL" /D "WIN32" /D "_DEBUG" /D "_WINDOWS" /D "_UNICODE" /D "UNICODE" /errorReport:prompt /WX /Zc:forScope /Gd /Oy- /MDd /Fa".\Debug\" /EHsc /nologo /Fo".\Debug\" /Fp".\Debug\Scribble.pch" /diagnostics:classic 
```  
  
 I když Scribble projekt nebyl nastaven na kompilovat s znaky znakové sady Unicode, byl již napsán s Tchar – místo char, takže nic ve skutečnosti je potřeba změnit. Sestavení projektu úspěšně pomocí znakové sady Unicode.  
  
 Nyní sestavte řešení. V okně výstupu kompilátoru víme, že tento _WINNT32_WINNT není definován:  
  
```Output  
_WIN32_WINNT not defined. Defaulting to _WIN32_WINNT_MAXVER (see WinSDKVer.h)  
```  
  
 Toto je upozornění, není k chybě a je velmi běžné při upgradu projektu Visual C++. Toto je makro, která definuje co nejnižší verze systému Windows, které aplikace poběží na. Pokud jsme upozornění ignorovat, můžeme přijmout výchozí hodnota, _WIN32_WINNT_MAXVER, což znamená, aktuální verze systému Windows. Pro tabulku možných hodnot, viz [použití Windows hlaviček](https://msdn.microsoft.com/en-us/library/aa383745.aspx). Například můžeme můžete nastavit jeho spuštění na libovolnou verzi z Vista a vyšší.  
  
```  
#define _WIN32_WINNT _WIN32_WINNT_VISTA  
```  
  
 Pokud kód používá částí rozhraní API systému Windows, které nejsou k dispozici na verzi systému Windows, které zadáte pomocí této makro, byste měli vidět, jako chyba kompilátoru. V případě kód Scribble se nezobrazí žádná chyba.  
  
### <a name="step-3-testing-and-debugging"></a>Krok 3. Testování a ladění  
 Neexistuje žádné testovací sady, který jsme právě spuštění aplikace a otestovat jeho funkce ručně přes uživatelské rozhraní. Byly dodrženy žádné problémy.  
  
### <a name="step-4-improve-the-code"></a>Krok 4. Zlepšení kód  
 Teď, když jste migrovali na Visual Studio 2017, můžete chtít provést některé změny využívat výhod nových funkcí jazyka C++. Aktuální verze kompilátoru C++ je mnohem víc vyhovující na C++ standardní pak předchozí verze, takže pokud budete mít paměti, aby nějaký kód změní aby váš kód bezpečnější a víc přenosného k jiné kompilátory a operační systémy, měli byste zvážit některé vylepšení.  
  
## <a name="next-steps"></a>Další kroky  
 Scribble bylo malé a jednoduché desktopová aplikace systému Windows a nebyl těžko převést. Mnoho aplikací malé, jednoduché stejným způsobem převést na novou verzi.  U složitějších aplikací, s mnoha další řádky kódu, starší starší kód, který nemusí být až moderních standardů, více projektů a knihovny, vlastní kroky sestavení nebo pro komplexní skriptované automatizovaných sestaveních, bude trvat déle k upgradu. Před pokračováním [další příklad](../porting/porting-guide-com-spy.md), ATL nebo COM aplikaci s názvem COM Spy.  
  
## <a name="see-also"></a>Viz také  
 [Portování a upgrade: Příklady a případové studie](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [Další příklad: COM Spy](../porting/porting-guide-com-spy.md)
