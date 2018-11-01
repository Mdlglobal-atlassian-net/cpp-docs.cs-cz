---
title: 'Průvodce přenosem: MFC Scribble'
ms.date: 11/04/2016
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
ms.openlocfilehash: b41689b1e0207029f4494cfd91c261705789a733
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539760"
---
# <a name="porting-guide-mfc-scribble"></a>Průvodce přenosem: MFC Scribble

Toto téma je první několik témat, které vám představí postup upgradu pro projekty Visual C++, které byly vytvořeny ve starších verzích sady Visual Studio do sady Visual Studio 2017. Tato témata zavést procesu upgradu podle příkladu, počínaje velmi jednoduchý projekt a přechod na ty o něco složitější. V tomto tématu se budeme pracovat prostřednictvím procesu upgradu ke konkrétnímu projektu knihovny MFC Scribble. Je vhodné jako základní informace o procesu upgradu pro projekty C++.

Jednotlivými verzemi sady Visual Studio zavádí možné nekompatibility, které může zkomplikovat přesunutí kódu ze starší verze sady Visual Studio na novější. Někdy jsou požadované změny v kódu, takže je nutné znovu zkompilovat a aktualizujte svůj kód a někdy jsou požadované změny v souborech projektu. Když otevřete projekt, který byl vytvořen pomocí předchozí verze sady Visual Studio, Visual Studio automaticky vás zeptá, zda aktualizovat projekt nebo řešení na nejnovější verzi. Tyto nástroje obvykle upgradovat jenom soubory projektu; Neprovádějte žádné změny zdrojového kódu.

## <a name="mfc-scribble"></a>MFC Scribble

MFC Scribble je dobře známé ukázky, která byla zahrnuta v různých verzích Visual C++. Je jednoduchou aplikaci výkresu, který ukazuje některé základní funkce knihovny MFC. Existují různé verze je k dispozici, včetně spravovaný a nativní kód. V tomto příkladu jsme nalezena stará verze Scribble v nativním kódu ze sady Visual Studio 2005 a otevřít v sadě Visual Studio 2017.

Před pokusem o upgrade, ujistěte se, že máte úlohu Windows Desktop nainstalovat. Spusťte instalační program sady Visual Studio (vs_installer.exe). Jedním ze způsobů otevřete instalační program je zvolit **souboru** > **nový projekt** a přejděte do dolní části seznamu nainstalovaných šablon, dokud se nezobrazí **otevřít instalační program Visual Studio**. Po otevření instalačního programu se zobrazí všechny dostupné úlohy. Pokud políčko u **Windows Desktop** úlohy není vybraná, vyberte ho a klikněte **změnit** tlačítko v dolní části okna.

Dále proveďte zálohu celé řešení a veškerý jeho obsah.

Nakonec jsme museli rozhodovat na konkrétní metody upgradu. Pro složitější řešení a projekty, které nebyly upgradované po dlouhou dobu měli byste zvážit upgrade jedné verze sady Visual Studio v čase. Tímto způsobem můžete zúžit problém zavedená verze sady Visual Studio. Pro Jednoduchý projekt je vhodné otevřením v nejnovější verzi sady Visual Studio a umožňuje Průvodce převést projekt. Pokud to nefunguje, zkuste upgrade jedné verze najednou, pokud máte přístup k odpovídající verze sady Visual Studio.

Všimněte si, že můžete také spustit devenv do příkazového řádku pomocí `/Upgrade` možnost, namísto použití Průvodce pro upgrade projektů. Zobrazit [/upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe). Který může být užitečná při automatizaci procesu upgradu pro velký počet projektů.

### <a name="step-1-converting-the-project-file"></a>Krok 1. Převádí se projektový soubor

Když otevřete starý soubor projektu v sadě Visual Studio 2017, Visual Studio nabízí převést soubor projektu na nejnovější verzi, která můžeme přijmout. Objevily se následující dialogové okno:

![Zkontrolovat změny projektu a řešení](../porting/media/scribbleprojectupgrade.PNG "ScribbleProjectUpgrade")

To, že nám, že cíl Itanium není k dispozici a nebudou převedeny došlo k chybě.

```Output
Platform 'Itanium' is missing from this project. All the configurations and their file configuration settings specific to this platform will be ignored. If you want this platform converted, please make sure you have the corresponding platform installed under '%vctargetpath%\platforms\Itanium'.Continue to convert this project without this platform?
```

V době, kdy byla vytvořena předchozí Scribble projekt byla Itanium důležité cílovou platformu. Platforma Windows už nepodporuje Itanium, takže jsme se rozhodli pokračovat bez podpora na platformu Itanium se.

Visual Studio pak zobrazí sestavu migrace výpis všechny problémy s původní soubor projektu.

![Zpráva o inovaci](../porting/media/scribblemigrationreport.PNG "ScribbleMigrationReport")

V tomto případě problémy se všechna upozornění a sady Visual Studio provedli odpovídající změny v souboru projektu. Rozdíl jde projektu je, že nástroj pro sestavení se změnil z vcbuild nástroji MSBuild. Tato změna byla poprvé zavedena v sadě Visual Studio 2010. Další změny patří některé změny uspořádání pořadí prvků v samotném souboru projektu. Žádné problémy nutná další pozornost pro tento jednoduchý projekt.

### <a name="step-2-getting-it-to-build"></a>Krok 2. Načítání sestavení

Před sestavením, zkontrolujeme sada nástrojů platformy, abychom věděli, jaké verze kompilátoru používá systém projektu. V dialogovém okně Vlastnosti projektu v rámci **vlastnosti konfigurace**v **Obecné** kategorie, podívejte se **sada nástrojů platformy** vlastnost. Obsahuje verzi sady Visual Studio a čísla verze nástrojů platformy, které v tomto případě je v141 pro Visual Studio 2017 verze nástrojů. Pokud převedete projekt, který byl původně kompilován s Visual C++ 2010, 2012, 2013 nebo 2015, sada nástrojů se neaktualizuje automaticky do sady nástrojů Visual Studio 2017.

Přechod usnadní do kódování Unicode, otevřete vlastnosti projektu, v části **vlastnosti konfigurace**, zvolte **Obecné** části a vyhledejte **znaková sada** vlastnost. Změnit z **použít vícebajtovou znakovou sadu** k **použít znakovou sadu Unicode**. Účinkem této změny je to teď _UNICODE a UNICODE makra jsou definována a _MBCS není, což můžete ověřit v dialogovém okně Vlastnosti v části **C/C++** kategorií **příkazového řádku** vlastnost.

```Output
/GS /analyze- /W4 /Zc:wchar_t /Zi /Gm- /Od /Fd".\Debug\vc141.pdb" /Zc:inline /fp:precise /D "_AFXDLL" /D "WIN32" /D "_DEBUG" /D "_WINDOWS" /D "_UNICODE" /D "UNICODE" /errorReport:prompt /WX /Zc:forScope /Gd /Oy- /MDd /Fa".\Debug\" /EHsc /nologo /Fo".\Debug\" /Fp".\Debug\Scribble.pch" /diagnostics:classic
```

I když Scribble projekt nebyl nastaven pro kompilaci pomocí znaků Unicode, je již byla zapsána s Tchar – místo char, takže ve skutečnosti není třeba nic změnit. Projekt vytvoří úspěšně pomocí znakové sady Unicode.

Nyní sestavte řešení. V okně Výstup kompilátoru víme, že _WINNT32_WINNT není definován:

```Output
_WIN32_WINNT not defined. Defaulting to _WIN32_WINNT_MAXVER (see WinSDKVer.h)
```

Toto je upozornění, ne o chybu a je velmi běžná v případě upgrade projektu Visual C++. Toto je makro, které definuje co nejnižší verze Windows, na kterém bude naši aplikaci spustili. Pokud jsme upozornění ignorovat, můžeme přijmout výchozí hodnotu _WIN32_WINNT_MAXVER, což znamená, že aktuální verzi Windows. Tabulka obsahující možné hodnoty, najdete v článku [pomocí hlavičky Windows](/windows/desktop/WinProg/using-the-windows-headers). Například můžeme nastavit jeho spuštění na libovolnou verzi systému Vista a vyšší.

```cpp
#define _WIN32_WINNT _WIN32_WINNT_VISTA
```

Pokud tento kód použije části rozhraní Windows API, které nejsou k dispozici na na verzi Windows, kterou zadáte pomocí tohoto makra, měli byste vidět, který jako chybu kompilátoru. V případě Scribble kódu se nezobrazí žádná chyba.

### <a name="step-3-testing-and-debugging"></a>Krok 3. Testování a ladění

Neexistuje žádné sady testů, který jsme právě spuštění aplikace a testovat jeho funkcí ručně přes uživatelské rozhraní. Nezjistily se žádné problémy.

### <a name="step-4-improve-the-code"></a>Krok 4. K lepšímu kódu

Teď, když jste migrovali do sady Visual Studio 2017, můžete chtít provést nějaké změny, abyste mohli využívat nové funkce jazyka C++. Aktuální verze kompilátoru jazyka C++ je mnohem více splňující podmínky na standardní a předchozí verze C++, takže pokud budete mít paměti, aby nějaký kód změn kódu bezpečnější a větší přenositelnost na jiné kompilátory a operační systémy, měli byste zvážit některé vylepšení.

## <a name="next-steps"></a>Další kroky

Scribble byla aplikace pracovní plochy Windows malý a jednoduchý a se těžko převést. Velký počet malých, jednoduché aplikací stejně snadno převést na novou verzi.  U složitějších aplikací, s mnoha více řádků kódu, starší starší kód, který nemusí být až moderních standardů, více projektů a knihovny, vlastní kroky sestavení nebo pro komplexní skriptované automatizované buildy, bude trvat déle k upgradu. Pokračujte [další příklad](../porting/porting-guide-com-spy.md), ATL/COM aplikaci COM Spy.

## <a name="see-also"></a>Viz také

[Přenos a upgrade: Příklady a případové studie](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Následující příklad: COM Spy](../porting/porting-guide-com-spy.md)