---
title: 'Návod: Kompilace programu C v příkazovém řádku'
ms.custom: conceptual
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: d807fa75b32b515c2222fec9ea9d070266303e33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335266"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Návod: Kompilace programu C v příkazovém řádku

Visual C++ obsahuje kompilátor Jazyka C, který můžete použít k vytvoření všeho od základních konzolových programů až po úplné aplikace pro Windows Desktop, mobilní aplikace a další.

Tento návod ukazuje, jak vytvořit základní, "Hello, World" styl C program pomocí textového editoru a pak jej zkompilovat na příkazovém řádku. Pokud chcete raději pracovat v jazyce C++ na příkazovém řádku, [přečtěte si návod: Kompilace nativního programu Jazyka C++ na příkazovém řádku](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Pokud chcete zkusit IDE sady Visual Studio namísto použití příkazového řádku, [přečtěte si návod: Práce s projekty a řešení (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) nebo [použití ide Visual Studio pro vývoj plochy jazyka C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Požadavky

Chcete-li dokončit tento návod, musíte mít nainstalovaný buď Visual Studio a volitelné součásti Visual C++ nebo nástroje sestavení pro Visual Studio.

Visual Studio je výkonné integrované vývojové prostředí, které podporuje plnohodnotný editor, správce prostředků, ladicí program a kompilátory pro mnoho jazyků a platforem. Informace o těchto funkcích a o tom, jak stáhnout a nainstalovat visual studio, včetně bezplatné edice Visual Studio Community, naleznete v [tématu Instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

Build Tools for Visual Studio verze Sady Visual Studio nainstaluje pouze sadu nástrojů příkazového řádku, kompilátory, nástroje a knihovny, které potřebujete k vytvoření c a c++ programy. Je ideální pro sestavení laboratoře nebo cvičení ve třídě a instaluje poměrně rychle. Chcete-li nainstalovat jenom sadu nástrojů příkazového řádku, stáhněte nástroje sestavení pro sadu Visual Studio ze stránky [stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) a spusťte instalační program. V instalačním programu Sady Visual Studio vyberte zatížení **nástrojů sestavení jazyka C++** a zvolte **Instalovat**.

Před vytvořením programu Jazyka C nebo C++ na příkazovém řádku je nutné ověřit, zda jsou nástroje nainstalovány a zda k nim můžete přistupovat z příkazového řádku. Visual C++ má složité požadavky pro prostředí příkazového řádku najít nástroje, záhlaví a knihovny, které používá. **Visual C++ nelze použít v okně příkazového řádku prosté** bez přípravy. Potřebujete okno *příkazového řádku vývojáře,* což je pravidelné okno příkazového řádku, které má nastaveny všechny požadované proměnné prostředí. Visual C++ naštěstí nainstaluje zástupce, abyste mohli spustit příkazové příkazové řádky pro vývojáře, které mají prostředí nastavené pro sestavení příkazového řádku. Názvy zástupců příkazového řádku pro vývojáře a místa, kde se nacházejí, se bohužel liší téměř ve všech verzích visual c++ a v různých verzích systému Windows. Prvním úkolem návodu je najít správnou zkratku k použití.

> [!NOTE]
> Zástupce příkazového řádku vývojáře automaticky nastaví správné cesty pro kompilátor a nástroje a pro všechny požadované hlavičky a knihovny. Některé z těchto hodnot se liší pro každou konfiguraci sestavení. Pokud nepoužijete jednu ze zkratek, je nutné tyto hodnoty prostředí nastavit sami. Další informace naleznete [v tématu Nastavení proměnných cesty a prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md). Vzhledem k tomu, že prostředí sestavení je složité, důrazně doporučujeme použít zástupce příkazového řádku vývojáře namísto vytváření vlastních.

Tyto pokyny se liší v závislosti na verzi sady Visual Studio, kterou používáte. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Otevření vývojářského příkazového řádku ve Visual Studiu 2019

Pokud jste nainstalovali Visual Studio 2019 ve Windows 10, otevřete nabídku Start a pak posuňte dolů a otevřete složku **Visual Studio 2019** (ne aplikaci Visual Studio 2019). Zvolte **Příkazový řádek pro vývojáře pro VS 2019,** abyste otevřeli okno příkazového řádku.

Pokud používáte jinou verzi Windows, vyhledejte v nabídce Start nebo na stránce Start složku nástrojů sady Visual Studio, která obsahuje zástupce příkazového řádku pro vývojáře. Pomocí funkce vyhledávání systému Windows můžete také vyhledat "příkazový řádek pro vývojáře" a vybrat ten, který odpovídá nainstalované verzi sady Visual Studio. Pomocí zástupce otevřete okno příkazového řádku.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Otevření vývojářského příkazového řádku ve Visual Studiu 2017

Pokud jste nainstalovali Visual Studio 2017 ve Windows 10, otevřete nabídku Start a pak posuňte dolů a otevřete složku **Visual Studio 2017** (ne aplikaci Visual Studio 2017). Zvolte **Příkazový řádek pro vývojáře pro VS 2017,** abyste otevřeli okno příkazového řádku.

Pokud používáte jinou verzi Windows, vyhledejte v nabídce Start nebo na stránce Start složku nástrojů sady Visual Studio, která obsahuje zástupce příkazového řádku pro vývojáře. Pomocí funkce vyhledávání systému Windows můžete také vyhledat "příkazový řádek pro vývojáře" a vybrat ten, který odpovídá nainstalované verzi sady Visual Studio. Pomocí zástupce otevřete okno příkazového řádku.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Otevření vývojářského příkazového řádku ve Visual Studiu 2015

Pokud jste nainstalovali Microsoft Visual C++ Build Tools 2015 ve Windows 10, otevřete nabídku **Start** a pak posuňte dolů a otevřete složku **Nástroje pro sestavení Visual C++.** Zvolte **Visual C++ 2015 x86 Nativní nástroje Příkazový řádek** otevřít okno příkazového řádku.

Pokud používáte jinou verzi Windows, vyhledejte v nabídce Start nebo na stránce Start složku nástrojů sady Visual Studio, která obsahuje zástupce příkazového řádku pro vývojáře. Pomocí funkce vyhledávání systému Windows můžete také vyhledat "příkazový řádek pro vývojáře" a vybrat ten, který odpovídá nainstalované verzi sady Visual Studio. Pomocí zástupce otevřete okno příkazového řádku.

::: moniker-end

Dále ověřte, zda je správně nastaven příkazový řádek vývojáře visual c++. V okně příkazového `cl` řádku zadejte a ověřte, zda výstup vypadá přibližně takto:

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

V aktuálním adresáři nebo číslech verzí mohou být rozdíly v závislosti na verzi jazyka Visual C++ a všech nainstalovaných aktualizacích. Pokud je výše uvedený výstup podobný tomu, co vidíte, pak jste připraveni k vytvoření programů C nebo C++ na příkazovém řádku.

> [!NOTE]
> Pokud se při spuštění příkazu **cl** zobrazí chyba jako "cl' není rozpoznán jako interní nebo externí příkaz, funkční program nebo dávkový soubor", chyba C1034 nebo chyba LNK1104, pak buď nepoužíváte příkazový řádek vývojáře, nebo je něco v nepořádku s instalací aplikace Visual C++. Tento problém je nutné vyřešit, než budete moci pokračovat.

Pokud nemůžete najít zástupce příkazového řádku pro vývojáře nebo pokud `cl`se při zadávání zobrazí chybová zpráva , může mít instalace visual c++ potíže. Pokud používáte Visual Studio 2017 nebo novější, zkuste přeinstalovat vývoj plochy s úlohami **C++** v instalačním programu Visual Studia. Podrobnosti naleznete v [tématu Instalace podpory jazyka C++ v sadě Visual Studio](vscpp-step-0-installation.md). Nebo přeinstalujte nástroje sestavení ze stránky [stažení sady Visual Studio.](https://visualstudio.microsoft.com/downloads/) Nechoďte na další část, dokud to nebude fungovat. Další informace o instalaci a řešení potíží s Visual Studio naleznete v [tématu Instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> V závislosti na verzi systému Windows v počítači a konfiguraci zabezpečení systému může být nutné klepnutím pravým tlačítkem myši otevřít místní nabídku zástupce příkazového řádku vývojáře a potom zvolit **Spustit jako správce,** chcete-li úspěšně sestavit a spustit program, který vytvoříte, pomocí tohoto návodu.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Vytvoření zdrojového souboru C a jeho kompilace na příkazovém řádku

1. V okně příkazového řádku `cd c:\` vývojáře zadejte, chcete-li změnit aktuální pracovní adresář do kořenového adresáře jednotky C:. Dále zadejte, `md c:\simple` chcete-li vytvořit `cd c:\simple` adresář, a pak jej změňte. Tento adresář bude obsahovat zdrojový soubor a zkompilovaný program.

1. Zadejte `notepad simple.c` na příkazovém řádku vývojáře. V dialogovém okně upozornění poznámkového bloku, které se objeví, zvolte **Ano** a vytvořte nový soubor simple.c ve vašem pracovním adresáři.

1. Do poznámkového bloku zadejte následující řádky kódu:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. Na řádku nabídek Poznámkový blok zvolte**Uložit** **soubor,** > chcete-li uložit simple.c do pracovního adresáře.

1. Přepněte zpět do okna příkazového řádku vývojáře. Zadáním `dir` příkazového řádku zobrazíte seznam obsahu adresáře c:\simple. Měli byste vidět zdrojový soubor simple.c v seznamu adresářů, který vypadá podobně:

    ```Output
    C:\simple>dir
     Volume in drive C has no label.
     Volume Serial Number is CC62-6545

     Directory of C:\simple

    10/02/2017  03:46 PM    <DIR>          .
    10/02/2017  03:46 PM    <DIR>          ..
    10/02/2017  03:36 PM               143 simple.c
                   1 File(s)            143 bytes
                   2 Dir(s)  514,900,566,016 bytes free

    ```

   Data a další podrobnosti se v počítači budou lišit. Pokud soubor zdrojového kódu, simple.c, nevidíte, zda jste změnili adresář c:\simple, který jste vytvořili, a v poznámkovém bloku zkontrolujte, zda jste zdrojový soubor v tomto adresáři uložili. Také se ujistěte, že jste uložili zdrojový kód s příponou .c název souboru, nikoli příponu .txt.

1. Chcete-li zkompilovat program, zadejte `cl simple.c` na příkazovém řádku pro vývojáře.

   Název spustitelného programu simple.exe můžete zobrazit v řádcích výstupních informací, které kompilátor zobrazuje:

    ```Output
    c:\simple>cl simple.c
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
    Copyright (C) Microsoft Corporation.  All rights reserved.

    simple.c
    Microsoft (R) Incremental Linker Version 14.10.25017.0
    Copyright (C) Microsoft Corporation.  All rights reserved.

    /out:simple.exe
    simple.obj
    ```

   > [!NOTE]
   > Pokud se zobrazí chyba, například "cl' není rozpoznán jako interní nebo externí příkaz, funkční program nebo dávkový soubor", chyba C1034 nebo chyba LNK1104, příkazový řádek vývojáře není správně nastaven. Informace o tom, jak tento problém vyřešit, naleznete v části **Otevřít vývojářský příkazový řádek.**

   > [!NOTE]
   > Pokud se zobrazí jiná chyba nebo upozornění kompilátoru nebo propojovacího programu, zkontrolujte zdrojový kód, abyste opravili všechny chyby, uložte jej a znovu spusťte kompilátor. Informace o konkrétních chybách získáte pomocí vyhledávacího pole v horní části této stránky a vyhledejte číslo chyby.

1. Chcete-li spustit `simple` program, zadejte na příkazovém řádku.

   Program zobrazí tento text a poté ukončí:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Blahopřejeme, zkompilovali jste a spusťte program Jazyka C pomocí příkazového řádku.

## <a name="next-steps"></a>Další kroky

Tento příklad "Hello, World" je asi tak jednoduché, jak program C může dostat. Programy reálného světa mají soubory hlaviček a další zdrojové soubory, odkaz v knihovnách a dělat užitečnou práci.

Pomocí kroků v tomto návodu můžete vytvořit vlastní kód C namísto zadání zobrazeného ukázkového kódu. Můžete také vytvořit mnoho ukázkových programů kódu C, které najdete jinde. Chcete-li zkompilovat program, který má další soubory zdrojového kódu, zadejte je všechny na příkazovém řádku, například:

`cl file1.c file2.c file3.c`

Kompilátor vyvezuu program s názvem file1.exe. Chcete-li změnit název na program1.exe, přidejte možnost propojovacího programu [/out:](reference/out-output-file-name.md)

`cl file1.c file2.c file3.c /link /out:program1.exe`

A chcete-li zachytit více chyb programování automaticky, doporučujeme zkompilovat pomocí možnosti [/W3](reference/compiler-option-warning-level.md) nebo [/W4](reference/compiler-option-warning-level.md) úrovně upozornění:

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Kompilátor cl.exe má mnoho dalších možností, které můžete použít k sestavení, optimalizaci, ladění a analýze kódu. Rychlý seznam najdete `cl /?` na příkazovém řádku vývojáře. Můžete také zkompilovat a propojit samostatně a použít možnosti propojovacího systému ve složitějších scénářích sestavení. Další informace o možnostech kompilátoru a propojovacího programu a použití naleznete v [tématu C/C++ Building Reference](reference/c-cpp-building-reference.md).

Můžete použít NMAKE a makefiles nebo MSBuild a soubory projektu ke konfiguraci a sestavení složitější projekty na příkazovém řádku. Další informace o použití těchto nástrojů naleznete v [tématech NMAKE Reference](reference/nmake-reference.md) a [MSBuild](msbuild-visual-cpp.md).

Jazyky C a C++ jsou podobné, ale nejsou stejné. Kompilátor Microsoft C/C++ (MSVC) používá jednoduché pravidlo k určení jazyka, který se má použít při kompilaci kódu. Ve výchozím nastavení kompilátor MSVC zachází se všemi soubory, které končí ve zdrojovém kódu C, jako se všemi soubory, které končí v .cpp jako se zdrojovým kódem jazyka C++. Chcete-li vynutit kompilátor považovat všechny soubory jako C nezávislé přípony názvu souboru, použijte možnost kompilátoru [/Tc.](reference/tc-tp-tc-tp-specify-source-file-type.md)

MSVC je kompatibilní s normou ISO C99, ale není striktně kompatibilní. Ve většině případů bude přenosný kód C zkompilovat a spustit podle očekávání. Visual C++ nepodporuje většinu změn v ISO C11. Některé funkce knihovny a názvy funkcí POSIX jsou zastaralé msvc. Funkce jsou podporovány, ale upřednostňované názvy byly změněny. Další informace naleznete [v tématu funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md) a [upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Viz také

[Návod: Vytvoření programu ve standardním C++ (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C Referenční příručka jazyka](../c-language/c-language-reference.md)<br/>
[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)<br/>
[Kompatibilita](../c-runtime-library/compatibility.md)
