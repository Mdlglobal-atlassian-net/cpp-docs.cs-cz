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

Visual Studio obsahuje kompilátor příkazového řádku C a C++. Můžete ji použít k vytvoření všeho od základních konzolových aplikací až po aplikace univerzální platformy Windows, aplikace pro stolní počítače, ovladače zařízení a komponenty .NET.

V tomto návodu vytvoříte základní program jazyka C++ ve stylu "Hello, World" pomocí textového editoru a pak jej zkompilujete na příkazovém řádku. Pokud chcete zkusit IDE sady Visual Studio namísto použití příkazového řádku, [přečtěte si návod: Práce s projekty a řešení (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) nebo [použití ide Visual Studio pro vývoj plochy jazyka C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

V tomto návodu můžete použít vlastní program jazyka C++ namísto zadávání zobrazeného programu. Nebo můžete použít ukázku kódu jazyka C++ z jiného článku nápovědy.

## <a name="prerequisites"></a>Požadavky

Chcete-li dokončit tento návod, musíte mít nainstalovaný buď Visual Studio a volitelné desktop vývoj s úlohami **C++** nebo nástroje sestavení příkazového řádku pro Visual Studio.

Visual Studio je *integrované vývojové prostředí* (IDE). Podporuje plně vybavený editor, správce prostředků, ladicí program y a kompilátory pro mnoho jazyků a platforem. Verze, které jsou k dispozici, zahrnují bezplatnou edici Visual Studio Community a všechny mohou podporovat vývoj c a c++. Informace o stažení a instalaci sady Visual Studio naleznete [v tématu Instalace podpory jazyka C++ v sadě Visual Studio](vscpp-step-0-installation.md).

Nástroje sestavení pro Visual Studio nainstaluje pouze kompilátory příkazového řádku, nástroje a knihovny, které potřebujete k vytvoření programů Jazyka C a C++. Je ideální pro sestavení laboratoře nebo cvičení ve třídě a instaluje poměrně rychle. Pokud chcete nainstalovat jenom nástroje příkazového řádku, vyhledejte nástroj sestavení pro Visual Studio na stránce [Stažení sady Visual Studio.](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)

Před vytvořením programu Jazyka C nebo C++ na příkazovém řádku ověřte, zda jsou nástroje nainstalovány, a získejte k nim přístup z příkazového řádku. Visual C++ má složité požadavky pro prostředí příkazového řádku najít nástroje, záhlaví a knihovny, které používá. **Visual C++ nelze použít v okně příkazového řádku prosté,** aniž byste museli dělat nějakou přípravu. Visual C++ naštěstí nainstaluje zástupce, abyste spustili příkazový řádek pro vývojáře, který má prostředí nastavené pro sestavení příkazového řádku. Názvy zástupců příkazového řádku pro vývojáře a místa, kde se nacházejí, se bohužel liší téměř ve všech verzích visual c++ a v různých verzích systému Windows. Prvním úkolem návodu je najít ten správný k použití.

> [!NOTE]
> Zástupce příkazového řádku vývojáře automaticky nastaví správné cesty pro kompilátor a nástroje a pro všechny požadované hlavičky a knihovny. Pokud používáte běžné okno **příkazového řádku,** je nutné tyto hodnoty prostředí nastavit sami. Další informace naleznete [v tématu Nastavení proměnných cesty a prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md). Doporučujeme použít zástupce příkazového řádku pro vývojáře namísto vytváření vlastního.

### <a name="open-a-developer-command-prompt"></a>Otevření vývojářského příkazového řádku

1. Pokud jste nainstalovali Visual Studio 2017 nebo novější ve Windows 10, otevřete nabídku Start a zvolte **Všechny aplikace**. Posuňte se dolů a otevřete složku **Visual Studio** (ne aplikaci Visual Studio). Zvolte **Příkazový řádek pro vývojáře,** aby vS otevřel okno příkazového řádku.

   Pokud jste nainstalovali Microsoft Visual C++ Build Tools 2015 ve Windows 10, otevřete nabídku **Start** a zvolte **Všechny aplikace**. Posuňte se dolů a otevřete složku **Nástroje pro sestavení visual c++.** Zvolte **Visual C++ 2015 x86 Nativní nástroje Příkazový řádek** otevřít okno příkazového řádku.

   Pomocí funkce vyhledávání systému Windows můžete také vyhledat "příkazový řádek pro vývojáře" a vybrat ten, který odpovídá nainstalované verzi sady Visual Studio. Pomocí zástupce otevřete okno příkazového řádku.

1. Dále ověřte, zda je správně nastaven příkazový řádek vývojáře visual c++. V okně příkazového `cl` řádku zadejte a ověřte, zda výstup vypadá přibližně takto:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   V aktuálním adresáři nebo číslech verzí mohou být rozdíly. Tyto hodnoty závisí na verzi visual c++ a všechny aktualizace nainstalovány. Pokud je výše uvedený výstup podobný tomu, co vidíte, pak jste připraveni k vytvoření programů C nebo C++ na příkazovém řádku.

   > [!NOTE]
   > Pokud se při spuštění **`cl`** příkazu zobrazí chyba jako "cl' není rozpoznán jako interní nebo externí příkaz, funkční program nebo dávkový soubor", chyba C1034 nebo chyba LNK1104, pak buď nepoužíváte příkazový řádek pro vývojáře, nebo je něco v nepořádku s instalací aplikace Visual C++. Tento problém je nutné vyřešit, než budete moci pokračovat.

   Pokud nemůžete najít zástupce příkazového řádku pro vývojáře nebo pokud `cl`se při zadávání zobrazí chybová zpráva , může mít instalace visual c++ potíže. Zkuste přeinstalovat komponentu Visual C++ v sadě Visual Studio nebo znovu nainstalujte nástroje pro sestavení jazyka Microsoft Visual C++. Nepokračujte k další části, **`cl`** dokud příkaz nefunguje. Další informace o instalaci a řešení potíží s visual c++ naleznete v [tématu Instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > V závislosti na verzi systému Windows v počítači a konfiguraci zabezpečení systému může být nutné klepnutím pravým tlačítkem myši otevřít místní nabídku zástupce příkazového řádku vývojáře a potom zvolit **Spustit jako správce,** chcete-li úspěšně sestavit a spustit program, který vytvoříte, pomocí tohoto návodu.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Vytvoření zdrojového souboru visual c++ a jeho kompilace na příkazovém řádku

1. V okně příkazového řádku `md c:\hello` vývojáře zadejte, `cd c:\hello` chcete-li vytvořit adresář, a potom jej změňte. Tento adresář je místo, kde jsou vytvořeny zdrojový soubor a zkompilovaný program.

1. Zadejte `notepad hello.cpp` do okna příkazového řádku.

   Zvolte **Ano,** když vás poznámkový blok vyzve k vytvoření souboru. Tento krok otevře prázdné okno poznámkového bloku, připravené pro zadání kódu do souboru s názvem hello.cpp.

1. Do poznámkového bloku zadejte následující řádky kódu:

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Tento kód je jednoduchý program, který bude psát jeden řádek textu na obrazovce a pak ukončit. Chcete-li minimalizovat chyby, zkopírujte tento kód a vložte jej do poznámkového bloku.

1. Uložte si práci! V poznámkovém bloku v nabídce **Soubor** zvolte **Uložit**.

   Gratulujeme, vytvořili jste zdrojový soubor Jazyka C++hello.cpp, který je připraven ke kompilaci.

1. Přepněte zpět do okna příkazového řádku vývojáře. Zadáním `dir` příkazového řádku zobrazíte seznam obsahu adresáře c:\hello. Měli byste vidět zdrojový soubor hello.cpp v seznamu adresářů, který vypadá podobně:

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

   Data a další podrobnosti se v počítači budou lišit. Pokud soubor zdrojového kódu nevidíte, *hello.cpp*, ujistěte se, že jste změnili na *adresář\\c: hello,* který jste vytvořili. V poznámkovém bloku zkontrolujte, zda jste v tomto adresáři uložili zdrojový soubor. Také se ujistěte, že jste *`.cpp`* uložili zdrojový *`.txt`* kód s příponou názvu souboru, nikoli s příponou.

1. Na příkazovém řádku `cl /EHsc hello.cpp` vývojáře zadejte kompilaci programu.

   Kompilátor cl.exe vygeneruje soubor OBJ, který obsahuje zkompilovaný kód, a potom spustí propojovací program a vytvoří spustitelný program s názvem hello.exe. Tento název se zobrazí v řádcích výstupních informací, které kompilátor zobrazí. Výstup kompilátoru by měl vypadat nějak takto:

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
   > Pokud se zobrazí chyba, například "cl' není rozpoznán jako interní nebo externí příkaz, funkční program nebo dávkový soubor", chyba C1034 nebo chyba LNK1104, příkazový řádek vývojáře není správně nastaven. Informace o tom, jak tento problém vyřešit, naleznete v části **Otevřít vývojářský příkazový řádek.**

   > [!NOTE]
   > Pokud se zobrazí jiná chyba nebo upozornění kompilátoru nebo propojovacího programu, zkontrolujte zdrojový kód, abyste opravili všechny chyby, uložte jej a znovu spusťte kompilátor. Informace o konkrétních chybách získáte pomocí vyhledávacího pole na této stránce MSDN a vyhledejte číslo chyby.

1. Chcete-li spustit program hello.exe, zadejte na příkazovém řádku program `hello`.

   Program zobrazí tento text a ukončí:

   ```Output
   Hello, world, from Visual C++!
   ```

   Blahopřejeme, zkompilovali jste a spusťte program jazyka C++ pomocí nástrojů příkazového řádku.

## <a name="next-steps"></a>Další kroky

Tento příklad "Hello, World" je asi tak jednoduché, jak může získat program Jazyka C++. Programy reálného světa mají obvykle soubory hlaviček, více zdrojových souborů a odkaz na knihovny.

Pomocí kroků v tomto návodu můžete vytvořit vlastní kód C++ namísto zadání zobrazeného ukázkového kódu. Tyto kroky také umožňují vytvořit mnoho ukázkových programů kódu jazyka C++, které najdete jinde. Zdrojový kód můžete umístit a vytvářet aplikace v libovolném adresáři, který lze zapisovat. Ve výchozím nastavení ide sady Visual Studio vytvoří projekty ve vaší uživatelské složce ve *zdrojové\\podsložce pro odpojení.* Starší verze mohou umístit projekty do složky *Documents\\Visual Studio \<verze>\\ *Projects*.

Chcete-li zkompilovat program, který má další soubory zdrojového kódu, zadejte je všechny na příkazovém řádku, například:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

Možnost `/EHsc` příkazového řádku instruuje kompilátor, aby povolil standardní chování zpracování výjimek Jazyka C++. Bez něj vyvolána výjimky může mít za následek nezničené objekty a nevracení prostředků. Další informace naleznete v tématu [/EH (Model zpracování výjimek).](reference/eh-exception-handling-model.md)

Při zadávání dalších zdrojových souborů kompilátor použije první vstupní soubor k vytvoření názvu programu. V tomto případě výstupy program s názvem file1.exe. Chcete-li změnit název na program1.exe, přidejte možnost propojovacího programu [/out:](reference/out-output-file-name.md)

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

A chcete-li zachytit více chyb programování automaticky, doporučujeme zkompilovat pomocí možnosti [/W3](reference/compiler-option-warning-level.md) nebo [/W4](reference/compiler-option-warning-level.md) úrovně upozornění:

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Kompilátor cl.exe má mnoho dalších možností. Můžete je použít k sestavení, optimalizaci, ladění a analýze kódu. Rychlý seznam najdete `cl /?` na příkazovém řádku vývojáře. Můžete také zkompilovat a propojit samostatně a použít možnosti propojovacího systému ve složitějších scénářích sestavení. Další informace o možnostech kompilátoru a propojovacího programu a použití naleznete v [tématu C/C++ Building Reference](reference/c-cpp-building-reference.md).

Můžete použít NMAKE a makefiles, MSBuild a soubory projektu nebo CMake, ke konfiguraci a sestavení složitější projekty na příkazovém řádku. Další informace o použití těchto nástrojů naleznete v [tématu NMAKE Reference](reference/nmake-reference.md), [MSBuild](msbuild-visual-cpp.md)a [CMake projekty v sadě Visual Studio](cmake-projects-in-visual-studio.md).

Jazyky C a C++ jsou podobné, ale nejsou stejné. Kompilátor MSVC používá jednoduché pravidlo k určení jazyka, který se má použít při kompilaci kódu. Ve výchozím nastavení kompilátor MSVC zachází *`.c`* se soubory, které končí *`.cpp`* jako zdrojový kód Jazyka C, a soubory, které končí jako zdrojový kód jazyka C++. Chcete-li vynutit kompilátor považovat všechny soubory jako C++ nezávisle na příponu názvu souboru, použijte možnost kompilátoru [/TP.](reference/tc-tp-tc-tp-specify-source-file-type.md)

Kompilátor MSVC obsahuje knihovnu C Runtime Library (CRT), která odpovídá standardu ISO C99, s menšími výjimkami. Přenosný kód obvykle zkompiluje a spustí podle očekávání. Některé zastaralé funkce knihovny a několik názvů funkcí POSIX jsou překladrezí MSVC zastaralé. Funkce jsou podporovány, ale upřednostňované názvy byly změněny. Další informace naleznete [v tématu funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md) a [upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Viz také

[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
