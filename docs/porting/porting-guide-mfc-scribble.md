---
title: 'Průvodce přenosem: MFC Scribble'
ms.date: 11/19/2018
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
ms.openlocfilehash: e808f67b1479653add27a54ddf91f6578c046734
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511543"
---
# <a name="porting-guide-mfc-scribble"></a>Průvodce přenosem: MFC Scribble

Toto téma je první z několika témat, která vás seznámí s postupem upgradu pro projekty sady Visual C++ Studio, které byly vytvořeny ve starších verzích sady Visual Studio, do sady visual Studio 2017. Tato témata zavádějí proces upgradu, který začíná velmi jednoduchý projekt a přesouvá se na mírně komplexnější. V tomto tématu budeme pracovat v procesu upgradu pro konkrétní projekt, prostředí MFC Klikyháky. Je vhodný jako základní Úvod k procesu upgradu pro C++ projekty.

Každá verze sady Visual Studio zavádí možné nekompatibility, které mohou zkomplikovat přesunutí kódu ze starší verze sady Visual Studio na novější. V některých případech jsou požadované změny v kódu, takže je nutné znovu kompilovat a aktualizovat kód a někdy jsou požadované změny v souborech projektu. Když otevřete projekt, který byl vytvořen pomocí předchozí verze sady Visual Studio, Visual Studio automaticky zobrazí dotaz, zda chcete aktualizovat projekt nebo řešení na nejnovější verzi. Tyto nástroje obvykle upgradují pouze soubory projektu; nemění váš zdrojový kód.

## <a name="mfc-scribble"></a>MFC Scribble

Prostředí MFC Klikyháky je dobře známá ukázka, která byla obsažena v mnoha různých verzích vizuálu C++. Jedná se o jednoduchou aplikaci pro kreslení, která ilustruje některé základní funkce knihovny MFC. K dispozici jsou různé verze, včetně spravovaných i nativních verzí kódu. V tomto příkladu jsme našli starou verzi Klikyháky v nativním kódu ze sady Visual Studio 2005 a otevřeli ji v aplikaci Visual Studio 2017.

Než se pokusíte o upgrade, ujistěte se, že máte nainstalovanou pracovní úlohu Windows. Otevřete instalační program sady Visual Studio (vs_installer. exe). Jedním ze způsobů, jak otevřít instalační program, je zvolit **soubor** > **Nový projekt** a přejít na konec seznamu nainstalovaných šablon, dokud neuvidíte **otevřít instalační program pro Visual Studio**. Po otevření instalačního programu se zobrazí všechny dostupné úlohy. Pokud políčko pro pracovní **plochu Windows** není vybrané, vyberte ho a klikněte na tlačítko **Upravit** v dolní části okna.

V dalším kroku zálohujte celé řešení a veškerý jeho obsah.

Nakonec jsme se museli rozhodnout o konkrétní metodě upgradu. V případě složitějších řešení a projektů, které nebyly upgradovány po dlouhou dobu, byste měli zvážit upgrade jedné verze sady Visual Studio v jednom okamžiku. Tímto způsobem můžete zúžit možnosti, které verze sady Visual Studio zavedla k problému. V případě jednoduchého projektu je vhodné ho otevřít v nejnovější verzi sady Visual Studio a povolit průvodci převod projektu. Pokud to nefunguje, můžete zkusit upgradovat jednu verzi najednou, pokud máte přístup k příslušným verzím sady Visual Studio.

Všimněte si, že můžete také spustit devenv z příkazového řádku pomocí `/Upgrade` možnosti namísto použití průvodce k upgradu projektů. Viz [/Upgrade (devenv. exe)](/visualstudio/ide/reference/upgrade-devenv-exe). To může být užitečné při automatizaci procesu upgradu pro velký počet projektů.

### <a name="step-1-converting-the-project-file"></a>Krok 1. Převod souboru projektu

Když otevřete starý soubor projektu v aplikaci Visual Studio 2017, Visual Studio nabídne převod souboru projektu na nejnovější verzi, kterou jsme přijali. Zobrazilo se následující dialogové okno:

![Zkontrolovat změny projektu a řešení](../porting/media/scribbleprojectupgrade.PNG "Zkontrolovat změny projektu a řešení")

Při upozorňování na nás došlo k chybě, že cíl Itanium není dostupný a nebude převeden.

```Output
Platform 'Itanium' is missing from this project. All the configurations and their file configuration settings specific to this platform will be ignored. If you want this platform converted, please make sure you have the corresponding platform installed under '%vctargetpath%\platforms\Itanium'.Continue to convert this project without this platform?
```

V době, kdy byl vytvořen předchozí projekt Klikyháky, byl procesor Itanium důležitou cílovou platformou. Platforma Windows už nepodporuje Itanium, takže jsme se rozhodli pokračovat bez podpory platformy Itanium.

Visual Studio potom zobrazí sestavu migrace obsahující všechny problémy se starým souborem projektu.

![Sestava upgradu](../porting/media/scribblemigrationreport.PNG "Sestava upgradu")

V tomto případě byly problémy všechna upozornění a aplikace Visual Studio provedla příslušné změny v souboru projektu. Velký rozdíl, který je v souladu s projektem, je v tom, že se nástroj sestavení změnil z vcbuild na MSBuild. Tato změna byla poprvé představena v aplikaci Visual Studio 2010. Další změny zahrnují jiné uspořádání sekvence prvků v samotném souboru projektu. Žádný z problémů není u tohoto jednoduchého projektu potřeba další pozornost.

### <a name="step-2-getting-it-to-build"></a>Krok 2. Získání sestavení

Před sestavením zkontrolujeme sadu nástrojů platformy, abychom věděli, jaká verze kompilátoru systém projektu používá. V dialogovém okně Vlastnosti projektu v části **Vlastnosti konfigurace**v kategorii **Obecné** si prohlédněte vlastnost **Sada nástrojů platformy** . Obsahuje verzi sady Visual Studio a číslo verze nástroje platformy, které je v tomto případě v141 pro verzi sady Visual Studio 2017 nástroje. Při převodu projektu, který byl původně zkompilován pomocí sady Visual Studio 2010, 2012, 2013 nebo 2015, sada nástrojů není automaticky aktualizována na sadu nástrojů Visual Studio 2017.

Chcete-li přepnout na kódování Unicode, otevřete vlastnosti projektu, v části **Vlastnosti konfigurace**vyberte oddíl **Obecné** a vyhledejte vlastnost **znaková sada** . Toto změňte z **použití vícebajtové znakové sady** pro **použití znakové sady Unicode**. Vlivem této změny je, že jsou teď definovaná makra _UNICODE a Unicode a možnost _MBCS není, což můžete ověřit v dialogovém okně Vlastnosti v kategorii **CC++ /** kategorie ve vlastnosti příkazového **řádku** .

```Output
/GS /analyze- /W4 /Zc:wchar_t /Zi /Gm- /Od /Fd".\Debug\vc141.pdb" /Zc:inline /fp:precise /D "_AFXDLL" /D "WIN32" /D "_DEBUG" /D "_WINDOWS" /D "_UNICODE" /D "UNICODE" /errorReport:prompt /WX /Zc:forScope /Gd /Oy- /MDd /Fa".\Debug\" /EHsc /nologo /Fo".\Debug\" /Fp".\Debug\Scribble.pch" /diagnostics:classic
```

I když se v aplikaci Klikyháky nevytvořila kompilace pomocí znaků Unicode, již byla napsána s TCHAR namísto char, takže není nic skutečně nutné změnit. Projekt se úspěšně vytvoří pomocí znakové sady Unicode.

Nyní Sestavte řešení. V okně výstupu kompilátor oznamuje, že není definován _WINNT32_WINNT:

```Output
_WIN32_WINNT not defined. Defaulting to _WIN32_WINNT_MAXVER (see WinSDKVer.h)
```

Toto je upozornění, nejedná se o chybu a je velmi běžné při upgradu projektu sady Visual C++ Studio. Toto je makro, které definuje nejnižší verzi Windows, na které bude aplikace běžet. Pokud se upozornění ignoruje, přijměte výchozí hodnotu _WIN32_WINNT_MAXVER, což znamená aktuální verzi Windows. Tabulku možných hodnot najdete v tématu [použití hlaviček Windows](/windows/win32/WinProg/using-the-windows-headers). Můžete třeba nastavit, aby se spouštěla na libovolné verzi ze systému Vista a vyšší.

```cpp
#define _WIN32_WINNT _WIN32_WINNT_VISTA
```

Pokud kód používá části rozhraní API systému Windows, které nejsou k dispozici ve verzi systému Windows, kterou zadáte pomocí tohoto makra, měli byste vidět, že jako chyba kompilátoru. V případě kódu Klikyháky není k dispozici žádná chyba.

### <a name="step-3-testing-and-debugging"></a>Krok 3. Testování a ladění

Není k dispozici žádná sada testů, takže jsme aplikaci spustili sami, otestovali jsme její funkce ručně prostřednictvím uživatelského rozhraní. Nebyly pozorovány žádné problémy.

### <a name="step-4-improve-the-code"></a>Krok 4. Vylepšení kódu

Teď, když jste migrovali do sady Visual Studio 2017, můžete chtít udělat nějaké změny, abyste mohli využívat nové C++ funkce. Aktuální verze C++ kompilátoru je mnohem více vyhovující C++ standardům, pak předchozí verze, takže pokud máte v úmyslu provést některé změny kódu, aby byl váš kód bezpečnější a lépe přenosný do jiných kompilátorů a operačních systémů, měli byste Vezměte v úvahu některá vylepšení.

## <a name="next-steps"></a>Další kroky

Klikyháky je malá a jednoduchá desktopová aplikace pro Windows a nedokázala se převést. Mnohé malé, jednoduché aplikace se převádějí stejně snadno na novou verzi.  U složitějších aplikací s mnoha více řádky kódu, starším starším kódem, který nemusí být až do moderních technických standardů, více projektů a knihoven, vlastních kroků sestavení nebo složitých automatizovaných sestavení, bude trvat déle. Pokračujte [dalším příkladem](../porting/porting-guide-com-spy.md)aplikace ATL/com s názvem com Spy.

## <a name="see-also"></a>Viz také:

[Přenos a upgrade: Příklady a případové studie](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Další příklad: COM Spy](../porting/porting-guide-com-spy.md)
