---
title: 'Návod: Kompilace nativního programu C++ v příkazovém řádku'
description: Použijte kompilátor Microsoft C++ z příkazového řádku.
ms.custom: conceptual
ms.date: 04/23/2019
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: daab00768f8140869a8db39c73f4fec3ab6304c7
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051514"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Návod: Kompilace nativního programu C++ v příkazovém řádku

Visual Studio obsahuje kompilátor příkazového řádku C++ , který můžete použít k vytvoření všeho od základních konzolových aplikací až po Univerzální platforma Windows aplikací, aplikací klasické pracovní plochy, ovladačů zařízení a komponent .NET.

V tomto návodu vytvoříte základní program ve stylu C++ "Hello, World" pomocí textového editoru a potom ho zkompilujete na příkazovém řádku. Pokud byste chtěli prostředí Visual Studio IDE vyzkoušet namísto použití příkazového řádku, přečtěte si [Návod: práce s projekty a řešeními (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) nebo [pomocí integrovaného vývojového prostředí C++ sady Visual Studio pro desktopový vývoj](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

V tomto návodu můžete použít vlastní vizuální C++ program namísto zadávání zobrazeného ovládacího prvku nebo můžete použít ukázku vizuálního C++ kódu z jiného článku.

## <a name="prerequisites"></a>Požadavky

Chcete-li dokončit tento návod, je nutné nainstalovat aplikaci Visual Studio a volitelný **vývoj pro stolní C++ počítače s** úlohou nebo nástroje pro sestavení příkazového řádku pro Visual Studio.

Visual Studio je výkonné integrované vývojové prostředí (IDE), které podporuje plně vybavené editory, správce prostředků, ladicí programy a kompilátory pro mnoho jazyků a platforem. Informace o tom, jak stáhnout a nainstalovat Visual Studio, včetně bezplatné edice Visual Studio Community Edition a zahrnutí podpory pro C/C++ vývoj, najdete v tématu [instalace C++ podpory v aplikaci Visual Studio](vscpp-step-0-installation.md).

Nástroje sestavení pro Visual Studio instalují jenom kompilátory, nástroje a knihovny příkazového řádku, které potřebujete k sestavení C a C++ programů. Je ideální pro Build Labs nebo cvičení v učebně a poměrně rychle se instaluje. Pokud chcete nainstalovat jenom nástroje příkazového řádku, hledejte na stránce [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) nástroje pro sestavení pro Visual Studio.

Před vytvořením C nebo C++ programu na příkazovém řádku je nutné ověřit, zda jsou nástroje nainstalovány a zda k nim máte přístup z příkazového řádku. Vizuál C++ má složité požadavky na prostředí příkazového řádku, aby bylo možné najít nástroje, hlavičky a knihovny, které používá. **Vizuál C++ nemůžete použít v prostém okně příkazového řádku** bez přípravy. Naštěstí Visual C++ nainstaluje klávesové zkratky pro spuštění příkazového řádku pro vývojáře, který má prostředí nastavené pro sestavení příkazového řádku. Názvy klávesových zkratek pro vývojáře a místa, kde se nacházejí, jsou v téměř každé verzi vizuálu C++ a v různých verzích systému Windows odlišné. První úkol Průvodce hledá, který z nich je nejvhodnější použít.

> [!NOTE]
> Zástupce příkazového řádku pro vývojáře automaticky nastaví správné cesty pro kompilátor a nástroje a pro všechny požadované hlavičky a knihovny. Pokud používáte běžné okno **příkazového řádku** , musíte tyto hodnoty prostředí nastavit sami. Další informace naleznete v tématu [Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md). Místo vytváření vlastního prostředí doporučujeme použít zástupce příkazového řádku pro vývojáře.

### <a name="open-a-developer-command-prompt"></a>Otevření příkazového řádku pro vývojáře

1. Pokud jste nainstalovali Visual Studio 2017 nebo novější ve Windows 10, otevřete nabídku Start a vyberte **všechny aplikace**. Posuňte se dolů a otevřete složku sady **Visual Studio** (ne aplikace Visual Studio). Vyberte možnost **Developer Command Prompt pro vs** . otevře se okno příkazového řádku.

   Pokud jste nainstalovali Microsoft Visual C++ Build Tools 2015 ve Windows 10, otevřete nabídku **Start** a vyberte **všechny aplikace**. Posuňte se dolů a otevřete složku **Nástroje pro vizuální C++ sestavení** . Zvolením možnosti  **C++ Visual 2015 x86 Native Tools Command Prompt** otevřete okno příkazového řádku.

   Můžete také použít funkci Windows Search k vyhledání "příkazového řádku pro vývojáře" a vybrat, který odpovídá nainstalované verzi sady Visual Studio. Pomocí zástupce otevřete okno příkazového řádku.

1. Dále ověřte, zda je správně C++ nastaven příkazový řádek nástroje Visual Developer. V okně příkazového řádku zadejte `cl` a ověřte, že výstup vypadá nějak takto:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   V závislosti na verzi vizuálu C++ a nainstalovaných aktualizací můžou existovat rozdíly v aktuálním adresáři nebo číslech verzí. Pokud je výše uvedený výstup podobný tomu, co vidíte, budete připraveni sestavit C nebo C++ programy v příkazovém řádku.

   > [!NOTE]
   > Pokud se zobrazí chyba, například "' CL ' není rozpoznán jako interní nebo externí příkaz, programový nebo dávkový soubor," Error C1034 nebo Error LINKERŮ LNK1104 při spuštění příkazu **CL** , pak buď nepoužíváte příkazový řádek pro vývojáře, nebo je něco v instalaci vizuálu C++nesprávné. Než budete pokračovat, musíte tento problém vyřešit.

   Pokud nemůžete najít zástupce příkazového řádku pro vývojáře, nebo pokud se vám zobrazí chybová zpráva při zadání `cl`, může mít C++ vaše instalace vizuálu problém. Zkuste přeinstalovat vizuální C++ komponentu v aplikaci Visual Studio nebo přeinstalovat nástroje pro Microsoft Visual C++ Build. Dokud to neuděláte, nepokračujte do další části. Další informace o instalaci a řešení potíží s C++Visual, najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > V závislosti na verzi systému Windows v počítači a konfiguraci zabezpečení systému bude pravděpodobně nutné kliknutím pravým tlačítkem myši otevřít místní nabídku pro zástupce příkazového řádku pro vývojáře a potom zvolit možnost **Spustit jako správce** a úspěšně sestavit a spustit program, který vytvoříte pomocí tohoto návodu.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Vytvoření vizuálního C++ zdrojového souboru a jeho kompilace na příkazovém řádku

1. V okně příkazového řádku pro vývojáře zadejte `md c:\hello` pro vytvoření adresáře a potom zadejte `cd c:\hello`, který chcete změnit na tento adresář. Tento adresář je místo, kde se vytváří zdrojový soubor a zkompilovaný program v nástroji.

1. V okně příkazového řádku zadejte `notepad hello.cpp`.

   Vyberte možnost **Ano** , pokud se zobrazí výzva k vytvoření souboru v programu Poznámkový blok. Tento krok otevře prázdné okno poznámkového bloku, které jste připraveni zadat kód do souboru s názvem Hello. cpp.

1. V programu Poznámkový blok zadejte následující řádky kódu:

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Tento kód je jednoduchý program, který na obrazovce zapíše jeden řádek textu a pak se ukončí. Chcete-li minimalizovat chyby, zkopírujte tento kód a vložte ho do poznámkového bloku.

1. Uložte svoji práci. V programu Poznámkový blok vyberte v nabídce **soubor** možnost **Uložit**.

   Gratulujeme, vytvořili jste C++ zdrojový soubor Hello. cpp, který je připravený ke kompilaci.

1. Přepněte zpět do okna příkazového řádku pro vývojáře. Do příkazového řádku zadejte `dir` pro výpis obsahu adresáře c:\Hello. V seznamu adresářů by se měl zobrazit zdrojový soubor Hello. cpp, který vypadá nějak takto:

   ```Output
   c:\hello>dir
    Volume in drive C has no label.
    Volume Serial Number is CC62-6545

    Directory of c:\hello

   05/24/2016  05:36 PM    <DIR>          .
   05/24/2016  05:36 PM    <DIR>          ..
   05/24/2016  05:37 PM               115 hello.cpp
                  1 File(s)            115 bytes
                  2 Dir(s)  571,343,446,016 bytes free

   ```

   Data a další podrobnosti se v počítači liší. Pokud nevidíte soubor zdrojového kódu, Hello. cpp, ujistěte se, že jste změnili adresář c:\Hello, který jste vytvořili, a v poznámkovém bloku nezapomeňte uložit zdrojový soubor do tohoto adresáře. Také se ujistěte, že jste uložili zdrojový kód s příponou názvu souboru. cpp, nikoli s příponou. txt.

1. Do příkazového řádku pro vývojáře zadejte `cl /EHsc hello.cpp` pro zkompilování programu.

   Kompilátor cl. exe vygeneruje soubor. obj, který obsahuje zkompilovaný kód, a potom spustí linker k vytvoření spustitelného programu s názvem Hello. exe. Tento název se zobrazí v řádcích výstupních informací, které kompilátor zobrazuje. Výstup kompilátoru by měl vypadat nějak takto:

   ```Output
   c:\hello>cl /EHsc hello.cpp
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   hello.cpp
   Microsoft (R) Incremental Linker Version 14.10.25017.0
   Copyright (C) Microsoft Corporation.  All rights reserved.

   /out:hello.exe
   hello.obj
   ```

   > [!NOTE]
   > Pokud se zobrazí chyba, například "" CL "není rozpoznán jako interní nebo externí příkaz, spustitelný program nebo dávkový soubor," Error C1034 nebo Error LINKERŮ LNK1104 ", váš příkazový řádek pro vývojáře není správně nastavený. Informace o tom, jak tento problém vyřešit, získáte zpět do části **otevření příkazového řádku pro vývojáře** .

   > [!NOTE]
   > Pokud získáte jiný kompilátor nebo chybu linkeru nebo upozornění, zkontrolujte zdrojový kód a opravte všechny chyby a pak ho uložte a spusťte kompilátor znovu. Informace o konkrétních chybách najdete v poli hledání na této stránce MSDN, kde najdete číslo chyby.

1. Chcete-li spustit program Hello. exe, zadejte do příkazového řádku `hello`.

   Program zobrazí tento text a ukončí:

   ```Output
   Hello, world, from Visual C++!
   ```

   Gratulujeme, zkompilujete a spustíte C++ program pomocí nástrojů příkazového řádku.

## <a name="next-steps"></a>Další kroky

Příklad: "Hello, World" je jednoduché, protože C++ program může získat. Programy v reálném světě mají hlavičkové soubory a další zdrojové soubory, propojí se do knihoven a potřebují pracovat.

Můžete použít kroky v tomto návodu k sestavení vlastního C++ kódu namísto psaní vzorového kódu, který je zobrazen. Můžete také vytvořit mnoho C++ ukázkových programů kódu, které najdete jinde. Můžete vložit svůj zdrojový kód a sestavit své aplikace v jakémkoli adresáři s možností zápisu. Ve výchozím nastavení rozhraní IDE sady Visual Studio vytváří projekty ve složce Dokumenty v podsložce projektu složky sady Visual Studio s názvem pro vaši verzi sady Visual Studio.

Chcete-li zkompilovat program, který obsahuje další soubory zdrojového kódu, zadejte je do příkazového řádku, například:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

Možnost příkazového řádku `/EHsc` instruuje kompilátor, aby povoloval C++ zpracování výjimek. Další informace naleznete v tématu [/EH (model zpracování výjimek)](reference/eh-exception-handling-model.md).

Když zadáte další zdrojové soubory, kompilátor použije první vstupní soubor k vytvoření názvu programu. V tomto případě výstup vytvoří program s názvem Soubor1. exe. Chcete-li změnit název na Program1. exe, přidejte možnost linkeru [/out](reference/out-output-file-name.md) :

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

A k automatickému zachycení chyb programování doporučujeme kompilovat pomocí možnosti [/w3](reference/compiler-option-warning-level.md) nebo [/W4](reference/compiler-option-warning-level.md) úrovně upozornění:

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Kompilátor, CL. exe má mnoho dalších možností, které můžete použít pro sestavení, optimalizaci, ladění a analýzu kódu. Pro rychlý seznam zadejte `cl /?` do příkazového řádku pro vývojáře. Můžete také kompilovat a propojit samostatně a použít Možnosti linkeru ve složitějších scénářích sestavení. Další informace o možnostech kompilátoru a linkeru a použití naleznete v tématu [CC++ /Building reference](reference/c-cpp-building-reference.md).

K nakonfigurování a sestavování složitějších projektů na příkazovém řádku můžete použít NMAKE a makefiles nebo soubory MSBuild a Project. Další informace o použití těchto nástrojů naleznete v tématu [reference NMAKE](reference/nmake-reference.md) a [MSBuild](msbuild-visual-cpp.md).

Jazyky C a C++ jsou podobné, ale nikoli stejné. Kompilátor MSVC používá jednoduché pravidlo k určení jazyka, který se má použít při kompilování kódu. Ve výchozím nastavení zpracovává kompilátor MSVC všechny soubory, které končí. c jako zdrojový kód jazyka C a všechny soubory, které končí. cpp jako C++ zdrojový kód. Chcete-li vynutit, aby kompilátor považoval C++ všechny soubory za nezávislé na příponě názvu souboru, použijte možnost kompilátoru [/TP](reference/tc-tp-tc-tp-specify-source-file-type.md) .

Kompilátor MSVC zahrnuje běhovou knihovnu jazyka C (CRT), která je kompatibilní se standardem ISO C99, ale není výhradně kompatibilní. Ve většině případů bude přenosný kód zkompilován a spuštěn podle očekávání. Vizuál C++ nepodporuje některé změny CRT v ISO C11. Některé funkce knihovny a názvy funkcí POSIX jsou v kompilátoru MSVC zastaralé. Funkce jsou podporovány, ale preferované názvy se změnily. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md) a [Upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
