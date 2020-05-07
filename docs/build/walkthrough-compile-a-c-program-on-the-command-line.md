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

Visual C++ obsahuje kompilátor jazyka C, který můžete použít k vytvoření všeho od základních konzolových programů až po plné desktopové aplikace pro Windows, mobilní aplikace a další.

Tento návod ukazuje, jak vytvořit základní program jazyka C ve stylu "Hello, World" pomocí textového editoru a pak ho zkompilovat na příkazovém řádku. Pokud místo toho chcete pracovat v jazyce C++ na příkazovém řádku, přečtěte si [Návod: kompilování nativního programu c++ na příkazovém řádku](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Pokud byste chtěli prostředí Visual Studio IDE vyzkoušet namísto použití příkazového řádku, přečtěte si [Návod: práce s projekty a řešeními (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) nebo [použití integrovaného vývojového prostředí (IDE) sady Visual Studio pro C++ Desktop Development](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Požadavky

Chcete-li dokončit tento návod, je nutné nainstalovat aplikaci Visual Studio a volitelné součásti Visual C++ nebo nástroje sestavení pro Visual Studio.

Visual Studio je výkonné integrované vývojové prostředí, které podporuje plně vybavený editor, správce prostředků, ladicí programy a kompilátory pro mnoho jazyků a platforem. Informace o těchto funkcích a o tom, jak stáhnout a nainstalovat Visual Studio, včetně bezplatné edice Visual Studio Community Edition, najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

Sada nástrojů Build Tools for Visual Studio nainstaluje pouze sadu nástrojů příkazového řádku, kompilátory, nástroje a knihovny, které potřebujete k vytváření programů v jazyce C a C++. Je ideální pro Build Labs nebo cvičení v učebně a poměrně rychle se instaluje. Chcete-li nainstalovat pouze sadu nástrojů příkazového řádku, Stáhněte si nástroje sestavení pro sadu Visual Studio na stránce [soubory ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) a spusťte instalační program. V instalačním programu sady Visual Studio vyberte úlohu **nástroje C++ pro sestavení** a zvolte možnost **nainstalovat**.

Před vytvořením programu C nebo C++ na příkazovém řádku je nutné ověřit, zda jsou nástroje nainstalovány a zda k nim máte přístup z příkazového řádku. Visual C++ má složité požadavky na prostředí příkazového řádku pro vyhledání nástrojů, hlaviček a knihoven, které používá. **Nemůžete použít Visual C++ v prostém okně příkazového řádku** bez přípravy. Potřebujete okno *příkazového řádku pro vývojáře* , což je běžné okno příkazového řádku, které má nastavenou všechny požadované proměnné prostředí. Naštěstí Visual C++ nainstaluje klávesové zkratky pro spuštění příkazového řádku pro vývojáře, které mají prostředí nastavené pro sestavení příkazového řádku. Názvy klávesových zkratek pro vývojáře a místa, kde se nacházejí, jsou v téměř každé verzi Visual C++ a v různých verzích systému Windows se však liší. První úkol návodu je najít správného zástupce, který se má použít.

> [!NOTE]
> Zástupce příkazového řádku pro vývojáře automaticky nastaví správné cesty pro kompilátor a nástroje a pro všechny požadované hlavičky a knihovny. Některé z těchto hodnot jsou pro každou konfiguraci sestavení odlišné. Tyto hodnoty prostředí je nutné nastavit sami, pokud nepoužíváte některou z klávesových zkratek. Další informace naleznete v tématu [Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md). Vzhledem k tomu, že prostředí sestavení je složité, důrazně doporučujeme použít zástupce příkazového řádku pro vývojáře namísto sestavování vlastního.

Tyto pokyny se liší v závislosti na verzi sady Visual Studio, kterou používáte. Chcete-li zobrazit dokumentaci k preferované verzi sady Visual Studio, použijte ovládací prvek selektor **verzí** . Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Otevření příkazového řádku pro vývojáře v aplikaci Visual Studio 2019

Pokud jste nainstalovali Visual Studio 2019 ve Windows 10, otevřete nabídku Start a pak přejděte dolů a otevřete složku **Visual studio 2019** (ne aplikace visual Studio 2019). **Pro VS 2019 vyberte Developer Command Prompt** a otevřete okno příkazového řádku.

Pokud používáte jinou verzi systému Windows, podívejte se do nabídky Start nebo na úvodní stránce složky nástroje Visual Studio, která obsahuje zástupce příkazového řádku pro vývojáře. Můžete také použít funkci Windows Search k vyhledání "příkazového řádku pro vývojáře" a vybrat, který odpovídá nainstalované verzi sady Visual Studio. Pomocí zástupce otevřete okno příkazového řádku.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Otevření příkazového řádku pro vývojáře v aplikaci Visual Studio 2017

Pokud jste nainstalovali Visual Studio 2017 ve Windows 10, otevřete nabídku Start a pak přejděte dolů a otevřete složku **Visual studio 2017** (ne aplikace visual Studio 2017). **Pro VS 2017 vyberte Developer Command Prompt** a otevřete okno příkazového řádku.

Pokud používáte jinou verzi systému Windows, podívejte se do nabídky Start nebo na úvodní stránce složky nástroje Visual Studio, která obsahuje zástupce příkazového řádku pro vývojáře. Můžete také použít funkci Windows Search k vyhledání "příkazového řádku pro vývojáře" a vybrat, který odpovídá nainstalované verzi sady Visual Studio. Pomocí zástupce otevřete okno příkazového řádku.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Otevření příkazového řádku pro vývojáře v aplikaci Visual Studio 2015

Pokud jste nainstalovali nástroje Microsoft Visual C++ Build Tools 2015 ve Windows 10, otevřete nabídku **Start** a přejděte dolů a otevřete složku **nástroje Visual C++ sestavení** . Vyberte **Visual C++ 2015 x86 Native Tools Command Prompt** otevřete okno příkazového řádku.

Pokud používáte jinou verzi systému Windows, podívejte se do nabídky Start nebo na úvodní stránce složky nástroje Visual Studio, která obsahuje zástupce příkazového řádku pro vývojáře. Můžete také použít funkci Windows Search k vyhledání "příkazového řádku pro vývojáře" a vybrat, který odpovídá nainstalované verzi sady Visual Studio. Pomocí zástupce otevřete okno příkazového řádku.

::: moniker-end

Dále ověřte, zda je správně nastaven příkaz Visual C++ Developer Command Prompt. V okně příkazového řádku zadejte `cl` a ověřte, že výstup vypadá nějak takto:

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

V závislosti na verzi Visual C++ a nainstalovaných aktualizací můžou existovat rozdíly v aktuálním adresáři nebo číslech verzí. Pokud je výše uvedený výstup podobný tomu, co vidíte, jste připraveni k sestavení programů C nebo C++ na příkazovém řádku.

> [!NOTE]
> Pokud se zobrazí chyba, například "' CL ' není rozpoznán jako interní nebo externí příkaz, programový nebo dávkový soubor," Error C1034 nebo Error LINKERŮ LNK1104 při spuštění příkazu **CL** , pak buď nepoužíváte příkazový řádek pro vývojáře, nebo je něco v instalaci Visual C++ chybné. Než budete pokračovat, musíte tento problém vyřešit.

Pokud nemůžete najít zástupce příkazového řádku pro vývojáře, nebo pokud se vám zobrazí chybová zpráva, `cl`když zadáte, může dojít k potížím s instalací Visual C++. Pokud používáte Visual Studio 2017 nebo novější, zkuste přeinstalovat **vývoj desktopových aplikací pomocí úlohy C++** v instalačním programu sady Visual Studio. Podrobnosti najdete v tématu [Instalace podpory C++ v aplikaci Visual Studio](vscpp-step-0-installation.md). Nebo přeinstalujte nástroje sestavení ze stránky [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) . Dokud to neuděláte, nepokračujte do další části. Další informace o instalaci a řešení potíží se sady Visual Studio najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> V závislosti na verzi systému Windows v počítači a konfiguraci zabezpečení systému bude pravděpodobně nutné kliknutím pravým tlačítkem myši otevřít místní nabídku pro zástupce příkazového řádku pro vývojáře a potom zvolit možnost **Spustit jako správce** a úspěšně sestavit a spustit program, který vytvoříte pomocí tohoto návodu.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Vytvoření zdrojového souboru jazyka C a jeho kompilace v příkazovém řádku

1. V okně příkazového řádku pro vývojáře zadejte `cd c:\` pro změnu aktuálního pracovního adresáře na kořen jednotky C:. Potom zadejte `md c:\simple` , že chcete vytvořit adresář a pak ho zadat `cd c:\simple` pro změnu do tohoto adresáře. Tento adresář bude obsahovat zdrojový soubor a zkompilovaný program.

1. Do `notepad simple.c` příkazového řádku pro vývojáře zadejte. V dialogovém okně upozornění poznámkového bloku, které se zobrazí, vyberte **Ano** , pokud chcete vytvořit nový jednoduchý soubor. c v pracovním adresáři.

1. V programu Poznámkový blok zadejte následující řádky kódu:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. Na panelu nabídek poznámkového bloku klikněte na**Uložit** a uložte do svého pracovního adresáře jednoduchý **soubor** > . c.

1. Přepněte zpět do okna příkazového řádku pro vývojáře. Zadáním `dir` příkazu na příkazovém řádku zobrazíte seznam obsahu adresáře c:\simple. Zdrojový soubor by měl být v seznamu adresářů uveden jako jednoduchý. c, který vypadá nějak takto:

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

   Data a další podrobnosti se v počítači liší. Pokud nevidíte soubor zdrojového kódu, Simple. c, ujistěte se, že jste změnili adresář c:\simple, který jste vytvořili, a v poznámkovém bloku nezapomeňte uložit zdrojový soubor do tohoto adresáře. Také se ujistěte, že jste uložili zdrojový kód s příponou názvu souboru. c, nikoli s příponou. txt.

1. Chcete-li zkompilovat program, `cl simple.c` zadejte do příkazového řádku pro vývojáře.

   V řádcích výstupních informací, které kompilátor zobrazuje, můžete zobrazit název spustitelného programu Simple. exe:

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
   > Pokud se zobrazí chyba, například "" CL "není rozpoznán jako interní nebo externí příkaz, spustitelný program nebo dávkový soubor," Error C1034 nebo Error LINKERŮ LNK1104 ", váš příkazový řádek pro vývojáře není správně nastavený. Informace o tom, jak tento problém vyřešit, získáte zpět do části **otevření příkazového řádku pro vývojáře** .

   > [!NOTE]
   > Pokud získáte jiný kompilátor nebo chybu linkeru nebo upozornění, zkontrolujte zdrojový kód a opravte všechny chyby a pak ho uložte a spusťte kompilátor znovu. Informace o konkrétních chybách najdete v poli hledání v horní části stránky, kde najdete číslo chyby.

1. Chcete-li spustit program, `simple` zadejte do příkazového řádku.

   Program zobrazí tento text a potom ukončí:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Gratulujeme, zkompilujete a spustíte program v jazyce C pomocí příkazového řádku.

## <a name="next-steps"></a>Další kroky

Příklad "Hello, World" je jednoduché, protože program v jazyce C může získat. Programy v reálném světě mají hlavičkové soubory a další zdrojové soubory, propojí se do knihoven a potřebují pracovat.

Můžete použít kroky v tomto návodu k sestavení vlastního kódu jazyka C namísto zadávání zobrazeného ukázkového kódu. Můžete také vytvořit mnoho ukázkových programů v kódu jazyka C, které najdete jinde. Chcete-li zkompilovat program, který obsahuje další soubory zdrojového kódu, zadejte je do příkazového řádku, například:

`cl file1.c file2.c file3.c`

Kompilátor vytvoří výstup programu s názvem Soubor1. exe. Chcete-li změnit název na Program1. exe, přidejte možnost linkeru [/out](reference/out-output-file-name.md) :

`cl file1.c file2.c file3.c /link /out:program1.exe`

A k automatickému zachycení chyb programování doporučujeme kompilovat pomocí možnosti [/w3](reference/compiler-option-warning-level.md) nebo [/W4](reference/compiler-option-warning-level.md) úrovně upozornění:

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Kompilátor, CL. exe má mnoho dalších možností, které můžete použít pro sestavení, optimalizaci, ladění a analýzu kódu. Pro rychlý seznam zadejte `cl /?` do příkazového řádku pro vývojáře. Můžete také kompilovat a propojit samostatně a použít Možnosti linkeru ve složitějších scénářích sestavení. Další informace o možnostech kompilátoru a linkeru a o použití naleznete v tématu [Reference pro sestavení C/C++](reference/c-cpp-building-reference.md).

K nakonfigurování a sestavování složitějších projektů na příkazovém řádku můžete použít NMAKE a makefiles nebo soubory MSBuild a Project. Další informace o použití těchto nástrojů naleznete v tématu [reference NMAKE](reference/nmake-reference.md) a [MSBuild](msbuild-visual-cpp.md).

Jazyky C a C++ jsou podobné, ale ne stejné. Kompilátor jazyka Microsoft C/C++ (MSVC) používá jednoduché pravidlo k určení jazyka, který se má použít při kompilování kódu. Ve výchozím nastavení zpracovává kompilátor MSVC všechny soubory, které končí. c jako zdrojový kód jazyka C a všechny soubory, které končí. cpp jako zdrojový kód jazyka C++. Chcete-li vynutit, aby kompilátor považoval všechny soubory jako nezávisle na příponě názvu souboru v jazyce C, použijte možnost kompilátoru [/TC](reference/tc-tp-tc-tp-specify-source-file-type.md) .

MSVC je kompatibilní se standardem ISO C99, ale není výhradně kompatibilní. Ve většině případů bude přenos v kódu jazyka C zkompilován a spuštěn podle očekávání. Visual C++ nepodporuje většinu změn v ISO C11. Některé funkce knihovny a názvy funkcí POSIX jsou zastaraly pomocí MSVC. Funkce jsou podporovány, ale preferované názvy se změnily. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md) a [Upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Viz také

[Návod: Vytvoření programu ve standardním C++ (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[Referenční dokumentace jazyka C](../c-language/c-language-reference.md)<br/>
[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)<br/>
[Kompatibilita](../c-runtime-library/compatibility.md)
