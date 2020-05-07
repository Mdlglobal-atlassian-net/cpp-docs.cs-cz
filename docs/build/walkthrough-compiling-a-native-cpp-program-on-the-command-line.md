---
title: 'Návod: Kompilace nativního programu C++ v příkazovém řádku'
description: Použijte kompilátor Microsoft C++ z příkazového řádku.
ms.custom: conceptual
ms.date: 04/02/2020
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: c24fdfdaef612059d5c2fbaaa58f10d83f5fe3a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335233"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Návod: Kompilace nativního programu C++ v příkazovém řádku

Visual Studio obsahuje kompilátor C a C++ příkazového řádku. Můžete ji použít k vytvoření všeho ze základních konzolových aplikací pro Univerzální platforma Windows aplikací, aplikací klasické pracovní plochy, ovladačů zařízení a komponent .NET.

V tomto návodu vytvoříte základní program C++ ve stylu "Hello, World" pomocí textového editoru a potom ho zkompilujete na příkazovém řádku. Pokud byste chtěli prostředí Visual Studio IDE vyzkoušet namísto použití příkazového řádku, přečtěte si [Návod: práce s projekty a řešeními (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) nebo [použití integrovaného vývojového prostředí (IDE) sady Visual Studio pro C++ Desktop Development](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

V tomto návodu můžete použít vlastní program jazyka C++ namísto zadávání zobrazeného ovládacího prvku. Případně můžete použít ukázku kódu jazyka C++ z jiného článku Help.

## <a name="prerequisites"></a>Požadavky

Chcete-li dokončit tento návod, je nutné nainstalovat aplikaci Visual Studio a volitelný **vývoj desktopových aplikací s** využitím úlohy C++ nebo nástroje pro sestavení příkazového řádku pro Visual Studio.

Visual Studio je *integrované vývojové prostředí* (IDE). Podporuje plně vybavený editor, správce prostředků, ladicí programy a kompilátory pro mnoho jazyků a platforem. Dostupné verze zahrnují bezplatnou edici Visual Studio Community Edition a všechny můžou podporovat vývoj v jazyce C a C++. Informace o tom, jak stáhnout a nainstalovat Visual Studio, najdete v tématu [Instalace podpory C++ v aplikaci Visual Studio](vscpp-step-0-installation.md).

Nástroje sestavení pro Visual Studio instalují pouze kompilátory, nástroje a knihovny příkazového řádku, které potřebujete k vytváření programů v jazyce C a C++. Je ideální pro Build Labs nebo cvičení v učebně a poměrně rychle se instaluje. Pokud chcete nainstalovat jenom nástroje příkazového řádku, hledejte na stránce [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) nástroje pro sestavení pro Visual Studio.

Předtím, než můžete vytvořit program C nebo C++ na příkazovém řádku, ověřte, zda jsou nástroje nainstalovány a zda k nim máte přístup z příkazového řádku. Visual C++ má složité požadavky na prostředí příkazového řádku pro vyhledání nástrojů, hlaviček a knihoven, které používá. **Nemůžete použít Visual C++ v prostém okně příkazového řádku** bez přípravy. Naštěstí Visual C++ nainstaluje zástupce pro spuštění příkazového řádku pro vývojáře, který má prostředí nastavené pro sestavení příkazového řádku. Názvy klávesových zkratek pro vývojáře a místa, kde se nacházejí, jsou v téměř každé verzi Visual C++ a v různých verzích systému Windows se však liší. První úkol Průvodce hledá, který z nich je nejvhodnější použít.

> [!NOTE]
> Zástupce příkazového řádku pro vývojáře automaticky nastaví správné cesty pro kompilátor a nástroje a pro všechny požadované hlavičky a knihovny. Pokud používáte běžné okno **příkazového řádku** , musíte tyto hodnoty prostředí nastavit sami. Další informace naleznete v tématu [Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md). Místo vytváření vlastního prostředí doporučujeme použít zástupce příkazového řádku pro vývojáře.

### <a name="open-a-developer-command-prompt"></a>Otevření příkazového řádku pro vývojáře

1. Pokud jste nainstalovali Visual Studio 2017 nebo novější ve Windows 10, otevřete nabídku Start a vyberte **všechny aplikace**. Posuňte se dolů a otevřete složku sady **Visual Studio** (ne aplikace Visual Studio). Vyberte možnost **Developer Command Prompt pro vs** . otevře se okno příkazového řádku.

   Pokud jste nainstalovali nástroje Microsoft Visual C++ Build Tools 2015 ve Windows 10, otevřete nabídku **Start** a vyberte **všechny aplikace**. Posuňte se dolů a otevřete složku **Nástroje pro Visual C++ sestavení** . Vyberte **Visual C++ 2015 x86 Native Tools Command Prompt** otevřete okno příkazového řádku.

   Můžete také použít funkci Windows Search k vyhledání "příkazového řádku pro vývojáře" a vybrat, který odpovídá nainstalované verzi sady Visual Studio. Pomocí zástupce otevřete okno příkazového řádku.

1. Dále ověřte, zda je správně nastaven příkaz Visual C++ Developer Command Prompt. V okně příkazového řádku zadejte `cl` a ověřte, že výstup vypadá nějak takto:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   V aktuálním adresáři nebo číslech verzí můžou být rozdíly. Tyto hodnoty závisí na verzi Visual C++ a nainstalovaných aktualizacích. Pokud je výše uvedený výstup podobný tomu, co vidíte, jste připraveni k sestavení programů C nebo C++ na příkazovém řádku.

   > [!NOTE]
   > Pokud se zobrazí chyba, například "" CL "není rozpoznán jako interní nebo externí příkaz, spustitelný program nebo dávkový soubor," Error C1034 nebo Error LINKERŮ LNK1104 při spuštění **`cl`** příkazu, pak buď nepoužíváte příkazový řádek pro vývojáře, nebo došlo k potížím s instalací Visual C++. Než budete pokračovat, musíte tento problém vyřešit.

   Pokud nemůžete najít zástupce příkazového řádku pro vývojáře, nebo pokud se vám zobrazí chybová zpráva, `cl`když zadáte, může dojít k potížím s instalací Visual C++. Zkuste přeinstalovat součást Visual C++ v aplikaci Visual Studio nebo přeinstalovat nástroje pro Microsoft Visual C++ sestavení. Nepoužívejte další oddíl, dokud **`cl`** příkaz nefunguje. Další informace o instalaci a řešení potíží s Visual C++ najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > V závislosti na verzi systému Windows v počítači a konfiguraci zabezpečení systému bude pravděpodobně nutné kliknutím pravým tlačítkem myši otevřít místní nabídku pro zástupce příkazového řádku pro vývojáře a potom zvolit možnost **Spustit jako správce** a úspěšně sestavit a spustit program, který vytvoříte pomocí tohoto návodu.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Vytvoření zdrojového souboru Visual C++ a jeho kompilace na příkazovém řádku

1. V okně příkazového řádku pro vývojáře zadejte `md c:\hello` , že chcete vytvořit adresář a pak ho `cd c:\hello` zadat pro změnu do tohoto adresáře. Tento adresář je místo, kde se vytváří zdrojový soubor a zkompilovaný program v nástroji.

1. V `notepad hello.cpp` okně příkazového řádku zadejte.

   Vyberte možnost **Ano** , pokud se zobrazí výzva k vytvoření souboru v programu Poznámkový blok. Tento krok otevře prázdné okno poznámkového bloku, které jste připraveni zadat kód do souboru s názvem Hello. cpp.

1. V programu Poznámkový blok zadejte následující řádky kódu:

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Tento kód je jednoduchý program, který na obrazovce zapíše jeden řádek textu a pak se ukončí. Chcete-li minimalizovat chyby, zkopírujte tento kód a vložte ho do poznámkového bloku.

1. Uložte svoji práci. V programu Poznámkový blok vyberte v nabídce **soubor** možnost **Uložit**.

   Gratulujeme, vytvořili jste zdrojový soubor C++ Hello. cpp, který je připravený ke kompilaci.

1. Přepněte zpět do okna příkazového řádku pro vývojáře. Zadáním `dir` příkazu na příkazovém řádku zobrazíte seznam obsahu adresáře c:\Hello. V seznamu adresářů by se měl zobrazit zdrojový soubor Hello. cpp, který vypadá nějak takto:

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

   Data a další podrobnosti se v počítači liší. Pokud nevidíte soubor zdrojového kódu, *Hello. cpp*, ujistěte se, že jste změnili adresář *c\\: Hello* , který jste vytvořili. V programu Poznámkový blok nezapomeňte uložit zdrojový soubor do tohoto adresáře. Také se ujistěte, že jste uložili zdrojový kód s příponou názvu *`.cpp`* souboru, nikoli s *`.txt`* příponou.

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

1. Chcete-li spustit program Hello. exe, zadejte `hello`na příkazovém řádku.

   Program zobrazí tento text a ukončí:

   ```Output
   Hello, world, from Visual C++!
   ```

   Gratulujeme, zkompilujete a spustíte program v jazyce C++ pomocí nástrojů příkazového řádku.

## <a name="next-steps"></a>Další kroky

Příklad "Hello, World" je jednoduché, protože program C++ může získat. Reálné programy obvykle mají hlavičkové soubory, více zdrojových souborů a odkazují na knihovny.

Můžete použít kroky v tomto návodu k sestavení vlastního kódu jazyka C++ namísto zadání ukázkového kódu, který je zobrazen. Tyto kroky také umožňují sestavit mnoho ukázkových programů kódu C++, které najdete jinde. Můžete vložit svůj zdrojový kód a sestavit své aplikace v jakémkoli adresáři s možností zápisu. Ve výchozím nastavení rozhraní IDE sady Visual Studio vytváří projekty ve složce uživatele v podsložce *zdrojové\\úložiště úložišť* . Starší verze mohou vkládat projekty do *dokumentů\\aplikace Visual Studio \<verze>\\ *projekty * složka.

Chcete-li zkompilovat program, který obsahuje další soubory zdrojového kódu, zadejte je do příkazového řádku, například:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

Možnost `/EHsc` příkazového řádku instruuje kompilátor, aby povoloval standardní chování zpracování výjimek jazyka C++. Bez této výjimky mohou vyvolání výjimek způsobit nezničitelné objekty a nevrácené prostředky. Další informace naleznete v tématu [/EH (model zpracování výjimek)](reference/eh-exception-handling-model.md).

Když zadáte další zdrojové soubory, kompilátor použije první vstupní soubor k vytvoření názvu programu. V tomto případě výstup vytvoří program s názvem Soubor1. exe. Chcete-li změnit název na Program1. exe, přidejte možnost linkeru [/out](reference/out-output-file-name.md) :

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

A k automatickému zachycení chyb programování doporučujeme kompilovat pomocí možnosti [/w3](reference/compiler-option-warning-level.md) nebo [/W4](reference/compiler-option-warning-level.md) úrovně upozornění:

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Kompilátor, CL. exe má mnoho dalších možností. Můžete je použít k sestavení, optimalizaci, ladění a analýze kódu. Pro rychlý seznam zadejte `cl /?` do příkazového řádku pro vývojáře. Můžete také kompilovat a propojit samostatně a použít Možnosti linkeru ve složitějších scénářích sestavení. Další informace o možnostech kompilátoru a linkeru a o použití naleznete v tématu [Reference pro sestavení C/C++](reference/c-cpp-building-reference.md).

K nakonfigurování a sestavování složitějších projektů na příkazovém řádku můžete použít NMAKE a makefiles, MSBuild a soubory projektu nebo CMake. Další informace o použití těchto nástrojů naleznete v tématech [Referenční příručka NMAKE](reference/nmake-reference.md), [MSBuild](msbuild-visual-cpp.md)a [projekty cmake v sadě Visual Studio](cmake-projects-in-visual-studio.md).

Jazyky C a C++ jsou podobné, ale ne stejné. Kompilátor MSVC používá jednoduché pravidlo k určení jazyka, který se má použít při kompilování kódu. Ve výchozím nastavení kompilátor MSVC zpracovává soubory, které končí *`.c`* jako zdrojový kód jazyka C, a soubory, které končí *`.cpp`* jako zdrojový kód jazyka C++. Chcete-li vynutit, aby kompilátor považoval všechny soubory za jazyk C++ nezávisle na příponě názvu souboru, použijte možnost kompilátoru [/TP](reference/tc-tp-tc-tp-specify-source-file-type.md) .

Kompilátor MSVC zahrnuje běhovou knihovnu jazyka C (CRT), která odpovídá standardu ISO C99, s menšími výjimkami. Přenosný kód obvykle kompiluje a spouští podle očekávání. Některé zastaralé funkce knihovny a několik názvů funkcí POSIX jsou v kompilátoru MSVC zastaralé. Funkce jsou podporovány, ale preferované názvy se změnily. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md) a [Upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Viz také

[Reference jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
