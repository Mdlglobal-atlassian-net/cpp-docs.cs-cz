---
title: 'Návod: Kompilace programu C na příkazovém řádku'
ms.custom: conceptual
ms.date: 09/24/2018
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: 756e0fa820806142f05ba45a52735692298f80d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656869"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Návod: Kompilace programu C na příkazovém řádku

Visual C++ obsahuje kompilátor jazyka C, který můžete použít k vytvoření čehokoliv od základních konzoly programy celých aplikací Windows Desktop, mobilní aplikace a další.

Tento návod ukazuje, jak vytvořit základní, "Hello, World"-stylu programu jazyka C pomocí textového editoru a jeho následnou kompilaci v příkazovém řádku. Pokud by raději pracujete v jazyce C++ v příkazovém řádku, naleznete v tématu [návod: kompilace nativního programu C++ v příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Pokud chcete zkusit IDE sady Visual Studio namísto z příkazového řádku, naleznete v tématu [návod: práce s projekty a řešeními (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) nebo [pomocí integrovaného vývojového prostředí sady Visual Studio pro vývoj v jazyce C++ Desktop](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu, musíte instalaci sady Visual Studio a volitelné součásti Visual C++ nebo nástroje Build Tools pro Visual Studio.

Visual Studio je výkonné integrované vývojové prostředí, které podporuje editoru se plně funkční, správce prostředků, ladicí programy a kompilátory pro mnoho jazyky a platformy. Informace o těchto funkcích a jak si stáhnout a nainstalovat sadu Visual Studio, včetně bezplatné edice Visual Studio Community najdete v části [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

Nástroje Build Tools pro Visual Studio verze sady Visual Studio nainstaluje pouze příkazového řádku sady nástrojů, kompilátory, nástroje a knihovny, které potřebujete k vytváření programů jazyka C a C++. Je ideální pro testovací prostředí pro sestavování nebo classroom vykonává a nainstaluje poměrně rychle. Chcete-li nainstalovat pouze příkazového řádku sady nástrojů, stáhněte si [Build Tools pro Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=875721) a spusťte instalační program.

Před sestavením programu jazyka C nebo C++ v příkazovém řádku, je nutné ověřit, že jsou nainstalované nástroje a že je můžete přistupovat k nim z příkazového řádku. Visual C++ má složité požadavky na prostředí příkazového řádku nástroje, hlavičky a knihovny, které používá. **Visual C++ nelze použít v okně prostý příkazového řádku** bez některé přípravy. Je nutné *příkazový řádek pro vývojáře* okna, což je okno regulární příkazového řádku, který má všechny požadované prostředí proměnné nastavené. Naštěstí Visual C++ nainstaluje zástupce můžete spustit příkazový řádek pro vývojáře, které mají prostředí pro sestavení příkazového řádku. Bohužel se liší v téměř všechny verze aplikace Visual C++ a různými verzemi Windows názvy zkratky příkazového řádku pro vývojáře a kde jsou umístěny. Vaše první úkol návodu je najít správné místní použití.

> [!NOTE]
> Zástupce příkazového řádku pro vývojáře automaticky nastaví správnou cesty kompilátoru a nástrojů a pro jakékoli požadované hlavičky a knihovny. Některé z těchto hodnot se liší pro každou konfiguraci sestavení. Je nutné nastavit tyto hodnoty prostředí sami Pokud nechcete použít jeden z klávesové zkratky. Další informace najdete v tématu [nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Protože je komplexní prostředí pro sestavení, důrazně doporučujeme že použít zástupce příkazového řádku pro vývojáře namísto sestavování vlastních.

## <a name="open-a-developer-command-prompt"></a>Otevřete příkazový řádek pro vývojáře

1. Pokud jste nainstalovali Visual Studio 2017 ve Windows 10, otevřete nabídku Start a posuňte se dolů a otevřete **Visual Studio 2017** složce (ne aplikace Visual Studio 2017). Zvolte **Developer Command Prompt for VS 2017** otevřete okno příkazového řádku.

   Pokud jste nainstalovali Microsoft Visual C++ Build Tools 2015 ve Windows 10, otevřete **Start** nabídky a potom přejděte dolů a otevřete **Visual C++ Build Tools** složky. Zvolte **příkazového řádku nativních nástrojů Visual C++ 2015 x86** otevřete okno příkazového řádku.

   Pokud používáte jinou verzi sady Visual Studio nebo jsou spuštěny na jinou verzi Windows, vyhledejte v nabídce Start nebo úvodní stránka pro složku nástroje Visual Studio, který obsahuje zástupce příkazového řádku pro vývojáře. Funkce vyhledávání Windows můžete použít také k vyhledání "developer command prompt" a vyberte ten, který odpovídá vaší nainstalované verzi sady Visual Studio. Chcete-li otevřít okno příkazového řádku použijte klávesovou zkratku.

1. Dále ověřte, že je správně nastavené příkazový řádek pro vývojáře Visual C++. V okně příkazového řádku zadejte `cl` a ověřte, že výstup by měl vypadat přibližně takto:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Může docházet k rozdílům v aktuálním adresáři nebo číslo verze, a to v závislosti na verzi aplikace Visual C++ a nainstalovány žádné aktualizace. Pokud výše uvedené výstup je podobný, co vidíte, pak budete připraveni k sestavení programů jazyka C nebo C++ v příkazovém řádku.

   > [!NOTE]
   > Pokud dojde k chybě, jako je "'cl' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru" Chyba C1034 nebo chyba LNK1104 při spuštění **cl** příkaz, pak buď nejsou pomocí příkazového řádku pro vývojáře, nebo něco se nepovedlo s instalací aplikace Visual C++. Než budete pokračovat, je nutné opravit tento problém.

   Pokud nemůžete najít vývojář zástupce příkazového řádku, nebo pokud se zobrazí chybová zpráva při zadání `cl`, pak instalaci aplikace Visual C++ může mít potíže. Pokud používáte Visual Studio 2017, zkuste přeinstalovat **vývoj desktopových aplikací pomocí C++** úlohy v instalačním programu sady Visual Studio. Podrobnosti najdete v tématu [podpora instalace jazyka C++ v sadě Visual Studio](../build/vscpp-step-0-installation.md). Nebo, přeinstalujte [Build Tools pro Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=875721). Není přejděte k další části dokud to funguje. Další informace o instalaci a řešení potíží s Visual Studio najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > V závislosti na verzi systému Windows v počítači a konfiguraci zabezpečení systému, bude pravděpodobně nutné klikněte pravým tlačítkem na otevřete místní nabídku pro zástupce příkazového řádku pro vývojáře a klikněte na tlačítko **spustit jako správce** do úspěšně sestavíte a spustíte program, který vytvoříte podle tohoto postupu.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Vytvořte zdrojový soubor jazyka C a jeho kompilace na příkazovém řádku

1. V okně příkazového řádku pro vývojáře zadejte `cd c:\` změnit aktuální pracovní adresář na kořenové jednotce C:. Pak zadejte `md c:\simple` vytvoření adresáře, a pak zadejte `cd c:\simple` pro přechod do této složky. Tento adresář bude obsahovat zdrojový soubor a zkompilovaný program.

1. Zadejte `notepad simple.c` příkazového řádku pro vývojáře. V programu Poznámkový blok dialogového okna výstrah, která se otevře, zvolte **Ano** k vytvoření nového souboru simple.c ve svém pracovním adresáři.

1. V programu Poznámkový blok zadejte následující řádky kódu:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. Na panelu nabídek poznámkového bloku vyberte **souboru** > **Uložit** uložit simple.c ve svém pracovním adresáři.

1. Přepněte zpět do okna příkazového řádku pro vývojáře. Zadejte `dir` příkazového řádku k výpisu obsahu adresáře c:\simple. Měli byste vidět simple.c zdrojového souboru v seznamu adresářů, který vypadá zhruba v tomto tvaru:

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

   Kalendářní data a další podrobnosti se bude lišit v počítači. Pokud nevidíte souboru zdrojového kódu, simple.c, ujistěte se, že jste změnili c:\simple adresáře, který jste vytvořili a v programu Poznámkový blok, ujistěte se, že jste uložili zdrojový soubor v tomto adresáři. Také se ujistěte, že jste uložili zdrojový kód s .c příponu souboru, ne .txt příponu.

1. Chcete-li kompilovat aplikaci, zadejte `cl simple.c` příkazového řádku pro vývojáře.

   Zobrazí se název spustitelného programu simple.exe v řádcích výstupních informací, které kompilátor zobrazí:

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
   > Pokud dojde k chybě, jako je "'cl' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru" Chyba C1034 nebo chyba LNK1104, příkazový řádek pro vývojáře není správně nastavený. Informace o tom, jak tento problém vyřešit, přejděte zpět **otevřete příkazový řádek pro vývojáře** oddílu.

   > [!NOTE]
   > Pokud se zobrazí různých kompilátoru nebo linkeru chybu nebo upozornění, zkontrolujte zdrojový kód opravte všechny chyby, pak jej uložit a znovu spusťte kompilátor. Informace o konkrétní chyby použijte vyhledávací pole v horní části této stránky a vyhledejte číslo chyby.

1. Chcete-li spustit program, zadejte `simple` příkazového řádku.

   Program zobrazí tento text a následně skončí:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Blahopřejeme, jste zkompilovat a spustit program jazyka C pomocí příkazového řádku.

## <a name="next-steps"></a>Další kroky

V tomto příkladu "Hello, World" je přibližně stejně jednoduché jako C programu můžete získat. Programy reálného světa mít hlavičkové soubory a další zdrojové soubory, na odkaz v knihovnách a dělat užitečnou práci.

Kroky v tomto názorném postupu můžete použít k vytvoření vlastního kódu jazyka C namísto zadávání vzorový kód ukazuje. Můžete také vytvořit mnoho C kód ukázkové aplikace, které jinde nenajdete. Pro kompilaci program, který obsahuje další zdrojové soubory, zadejte je na příkazovém řádku, jako je:

`cl file1.c file2.c file3.c`

Kompilátor výstupy program s názvem file1.exe. Chcete-li změnit název na program1.exe, přidejte [/out](../build/reference/out-output-file-name.md) – možnost linkeru:

`cl file1.c file2.c file3.c /link /out:program1.exe`

K zachycení více programovacích chyb automaticky, doporučujeme při kompilaci pomocí [w3](../build/reference/compiler-option-warning-level.md) nebo [/W4](../build/reference/compiler-option-warning-level.md) upozornění úrovně možnost:

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Kompilátor, cl.exe má mnoho dalších možností, můžete použít k sestavení, optimalizovat, ladit a analyzovat svůj kód. Stručný seznam, zadejte `cl /?` příkazového řádku pro vývojáře. Můžete také zkompilovat a propojit samostatně a použít možnosti linkeru v podobě komplexních scénářů sestavení. Další informace o kompilátoru a možnosti propojovacího programu a jeho použití najdete v tématu [Reference sestavení C/C++](../build/reference/c-cpp-building-reference.md).

NMAKE a soubory pravidel nebo MSBuild a soubory projektu můžete použít ke konfiguraci a sestavit projekty složitější na příkazovém řádku. Další informace o použití těchto nástrojů naleznete v tématu [NMake – odkaz](../build/nmake-reference.md) a [MSBuild](../build/msbuild-visual-cpp.md).

Jazyky C a C++ jsou podobné, ale nejsou stejné. Kompilátor Visual C++ používá jednoduché pravidlo k určení jazyk, který se má použít při kompilaci kódu. Ve výchozím nastavení kompilátor Visual C++ zpracovává všechny soubory, které končí .c jako zdrojový kód jazyka C a všechny soubory, které končí .cpp jako zdrojový kód jazyka C++. Chcete-li vynutit na kompilátoru, aby považoval všechny soubory jako C nezávislé přípony názvu souboru, použijte [/Tc](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) – možnost kompilátoru.

Kompilátor Visual C++ C je kompatibilní se standardem ISO C99, ale není striktně kompatibilní. Ve většině případů bude přenositelný kód C zkompilovat a spustit podle očekávání. Visual C++ nepodporuje většinu změn v ISO C11. Některé funkce knihovny a POSIX – názvy funkcí jsou zastaralé v kompilátoru jazyka Visual C++. Jsou podporované, ale upřednostňované názvy změnily. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md) a [upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Viz také:

[Návod: Vytvoření programu ve standardním C++ (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[Referenční dokumentace jazyka C](../c-language/c-language-reference.md)<br/>
[Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)<br/>
[Kompatibilita](../c-runtime-library/compatibility.md)
