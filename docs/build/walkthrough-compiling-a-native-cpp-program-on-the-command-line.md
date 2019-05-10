---
title: 'Návod: Kompilace nativního programu C++ v příkazovém řádku'
description: Použití služby Microsoft C++ kompilátoru z příkazového řádku.
ms.custom: conceptual
ms.date: 04/23/2019
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: 64300c8683dd5d1c40638ba7d50acfca6abc40c0
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217710"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Návod: Kompilace nativního programu C++ v příkazovém řádku

Visual Studio obsahuje příkazového řádku C++ kompilátor, který můžete použít k vytvoření čehokoliv od základních konzolové aplikace do aplikací pro univerzální platformu Windows, aplikací klasické pracovní plochy, ovladačů zařízení a komponenty rozhraní .NET.

V tomto návodu vytvoříte základní, "Hello, World"-stylu programu C++ pomocí textového editoru a jeho následnou kompilaci v příkazovém řádku. Pokud chcete zkusit IDE sady Visual Studio namísto z příkazového řádku, naleznete v tématu [názorný postup: Práce s projekty a řešeními (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) nebo [pomocí sady Visual Studio IDE pro C++ Desktop Development](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

V tomto podrobném návodu můžete použít aplikaci Visual C++ místo zadání ten, který se zobrazí nebo můžete pomocí vzorového kódu Visual C++ z jiného článku nápovědy.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu, musíte instalaci sady Visual Studio a volitelné **vývoj desktopových aplikací pomocí C++** úlohy nebo nástroje příkazového řádku Build Tools pro Visual Studio.

Visual Studio je výkonné integrované vývojové prostředí (IDE), který podporuje editoru se plně funkční, správce prostředků, ladicí programy a kompilátory pro mnoho jazyky a platformy. Informace o tom, ke stažení a instalaci sady Visual Studio, včetně bezplatné edice Visual Studio Community a zahrnuje podporu pro vývoj v jazyce C/C++, naleznete v tématu [podpora instalace jazyka C++ v sadě Visual Studio](vscpp-step-0-installation.md).

Nástroje Build Tools pro Visual Studio nainstaluje pouze kompilátory příkazového řádku, nástroje a knihovny, které potřebujete k vytváření programů jazyka C a C++. Je ideální pro testovací prostředí pro sestavování nebo classroom vykonává a nainstaluje poměrně rychle. Pokud chcete nainstalovat jenom nástroje příkazového řádku, najít Build Tools pro Visual Studio na [stahování sady Visual Studio](https://visualstudio.microsoft.com/downloads/) stránky.

Před sestavením programu jazyka C nebo C++ v příkazovém řádku, je nutné ověřit, že jsou nainstalované nástroje a že je můžete přistupovat k nim z příkazového řádku. Visual C++ má složité požadavky na prostředí příkazového řádku nástroje, hlavičky a knihovny, které používá. **Visual C++ nelze použít v okně prostý příkazového řádku** aniž by některé přípravy. Naštěstí Visual C++ nainstaluje zástupce můžete spustit příkazový řádek pro vývojáře, který má prostředí pro sestavení příkazového řádku. Bohužel se liší v téměř všechny verze aplikace Visual C++ a různými verzemi Windows názvy zkratky příkazového řádku pro vývojáře a kde jsou umístěny. Vaše první úkol návod nalézá ten správný používat.

> [!NOTE]
> Zástupce příkazového řádku pro vývojáře automaticky nastaví správnou cesty kompilátoru a nástrojů a pro jakékoli požadované hlavičky a knihovny. Musíte nastavit tyto hodnoty prostředí sami používáte běžný **příkazového řádku** okna. Další informace najdete v tématu [nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md). Doporučujeme, abyste že místo vytváření vlastních použijete zástupce příkazového řádku pro vývojáře.

### <a name="open-a-developer-command-prompt"></a>Otevřete příkazový řádek pro vývojáře

1. Pokud jste nainstalovali Visual Studio 2017 nebo později ve Windows 10, otevřete nabídku Start a zvolte **všechny aplikace**. Přejděte dolů a otevřete **sady Visual Studio** složku (nikoli aplikace Visual Studio). Zvolte **Developer Command Prompt for VS** otevřete okno příkazového řádku.

   Pokud jste nainstalovali Microsoft Visual C++ Build Tools 2015 ve Windows 10, otevřete **Start** nabídku a zvolte **všechny aplikace**. Přejděte dolů a otevřete **Visual C++ Build Tools** složky. Zvolte **příkazového řádku nativních nástrojů Visual C++ 2015 x86** otevřete okno příkazového řádku.

   Funkce vyhledávání Windows můžete použít také k vyhledání "developer command prompt" a vyberte ten, který odpovídá vaší nainstalované verzi sady Visual Studio. Chcete-li otevřít okno příkazového řádku použijte klávesovou zkratku.

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

   Pokud nemůžete najít vývojář zástupce příkazového řádku, nebo pokud se zobrazí chybová zpráva při zadání `cl`, pak instalaci aplikace Visual C++ může mít potíže. Zkuste znovu nainstalovat součásti Visual C++ v sadě Visual Studio, nebo znovu nainstalujte Microsoft Visual C++ Build Tools. Není přejděte k další části dokud to funguje. Další informace o instalaci a řešení potíží s Visual C++, naleznete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > V závislosti na verzi systému Windows v počítači a konfiguraci zabezpečení systému, bude pravděpodobně nutné klikněte pravým tlačítkem na otevřete místní nabídku pro zástupce příkazového řádku pro vývojáře a klikněte na tlačítko **spustit jako správce** do úspěšně sestavíte a spustíte program, který vytvoříte podle tohoto postupu.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Vytvořte zdrojový soubor jazyka Visual C++ a jeho kompilace na příkazovém řádku

1. V okně příkazového řádku pro vývojáře zadejte `md c:\hello` vytvoření adresáře, a pak zadejte `cd c:\hello` pro přechod do této složky. Tento adresář je, kde jsou vytvářeny zdrojový soubor a zkompilovaný program v.

1. Zadejte `notepad hello.cpp` v okně příkazového řádku.

   Zvolte **Ano** při Poznámkový blok vás vyzve k vytvoření souboru. Tento krok otevře se prázdné okno Poznámkový blok, můžete zadat kód do souboru s názvem hello.cpp.

1. V programu Poznámkový blok zadejte následující řádky kódu:

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Tento kód je jednoduchý program, který bude zapisovat jeden řádek textu na obrazovce a poté ukončete. Chcete-li minimalizovat chyby, zkopírujte tento kód a vložte ho do poznámkového bloku.

1. Uložte svou práci! V poznámkovém bloku na **souboru** nabídce zvolte **Uložit**.

   Blahopřejeme, vytvořili jste C++ zdrojový soubor, hello.cpp, který je připravený ke kompilaci.

1. Přepněte zpět do okna příkazového řádku pro vývojáře. Zadejte `dir` příkazového řádku k výpisu obsahu adresáře c:\hello. Měli byste vidět hello.cpp zdrojového souboru v seznamu adresářů, který vypadá zhruba v tomto tvaru:

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

   Kalendářní data a další podrobnosti se bude lišit v počítači. Pokud nevidíte souboru zdrojového kódu, hello.cpp, ujistěte se, že jste změnili c:\hello adresáře, který jste vytvořili a v programu Poznámkový blok, ujistěte se, že jste uložili zdrojový soubor v tomto adresáři. Také se ujistěte, že jste uložili zdrojového kódu s příponou názvu .cpp soubor, nikoli příponu .txt.

1. Na příkazovém řádku pro vývojáře zadejte `cl /EHsc hello.cpp` kompilace programu.

   Kompilátor cl.exe vygeneruje soubor .obj, který obsahuje zkompilovaný kód a pak spustí linkeru, aby vytvořil spustitelný program s názvem hello.exe. Tento název se zobrazí v řádcích výstupních informací, které kompilátor zobrazí. Výstup kompilátoru by měla vypadat podobně jako:

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
   > Pokud dojde k chybě, jako je "'cl' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru" Chyba C1034 nebo chyba LNK1104, příkazový řádek pro vývojáře není správně nastavený. Informace o tom, jak tento problém vyřešit, přejděte zpět **otevřete příkazový řádek pro vývojáře** oddílu.

   > [!NOTE]
   > Pokud se zobrazí různých kompilátoru nebo linkeru chybu nebo upozornění, zkontrolujte zdrojový kód opravte všechny chyby, pak jej uložit a znovu spusťte kompilátor. Informace o konkrétní chyby použijte vyhledávací pole na této stránce MSDN a vyhledejte číslo chyby.

1. Chcete-li spustit hello.exe program příkazového řádku, zadejte `hello`.

   Program zobrazí tento text a ukončení:

   ```Output
   Hello, world, from Visual C++!
   ```

   Blahopřejeme, jste kompilaci a spuštění programu v jazyce C++ pomocí nástroje příkazového řádku.

## <a name="next-steps"></a>Další kroky

V tomto příkladu "Hello, World" je přibližně stejně jednoduché jako programu v jazyce C++ můžete získat. Programy reálného světa mít hlavičkové soubory a další zdrojové soubory, na odkaz v knihovnách a dělat užitečnou práci.

Kroky v tomto názorném postupu můžete vytvořit vlastní kód C++ místo zadání vzorový kód ukazuje. Můžete také vytvořit mnoho C++ kód ukázkové aplikace, které jinde nenajdete. Můžete umístit svůj zdrojový kód a sestavujte aplikace v jakékoli zapisovatelné adresáře. Ve výchozím nastavení integrovaném vývojovém prostředí sady Visual Studio vytvoří projekty ve složce Dokumenty v podsložce s projekty sady Visual Studio složku s názvem pro vaši verzi sady Visual Studio.

Pro kompilaci program, který obsahuje další zdrojové soubory, zadejte je na příkazovém řádku, jako je:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

`/EHsc` Možnost příkazového řádku instruuje kompilátor, aby povolit zpracování výjimek jazyka C++. Další informace najdete v tématu [/EH (Model zpracování výjimek)](reference/eh-exception-handling-model.md).

Když zadáte další zdrojové soubory, kompilátor používá prvního vstupního souboru chcete-li vytvořit název programu. V takovém případě výstupy program s názvem file1.exe. Chcete-li změnit název na program1.exe, přidejte [/out](reference/out-output-file-name.md) – možnost linkeru:

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

K zachycení více programovacích chyb automaticky, doporučujeme při kompilaci pomocí [w3](reference/compiler-option-warning-level.md) nebo [/W4](reference/compiler-option-warning-level.md) upozornění úrovně možnost:

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Kompilátor, cl.exe má mnoho dalších možností, můžete použít k sestavení, optimalizovat, ladit a analyzovat svůj kód. Stručný seznam, zadejte `cl /?` příkazového řádku pro vývojáře. Můžete také zkompilovat a propojit samostatně a použít možnosti linkeru v podobě komplexních scénářů sestavení. Další informace o kompilátoru a možnosti propojovacího programu a jeho použití najdete v tématu [Reference sestavení C/C++](reference/c-cpp-building-reference.md).

NMAKE a soubory pravidel nebo MSBuild a soubory projektu můžete použít ke konfiguraci a sestavit projekty složitější na příkazovém řádku. Další informace o použití těchto nástrojů naleznete v tématu [NMake – odkaz](reference/nmake-reference.md) a [MSBuild](msbuild-visual-cpp.md).

Jazyky C a C++ jsou podobné, ale nejsou stejné. Kompilátor MSVC používá jednoduché pravidlo k určení jazyk, který se má použít při kompilaci kódu. Ve výchozím nastavení a kompilátorem MSVC zpracovává všechny soubory, které končí .c jako zdrojový kód jazyka C a všechny soubory, které končí .cpp jako zdrojový kód jazyka C++. Chcete-li vynutit na kompilátoru, aby považoval všechny soubory jako C++ nezávislé na příponu názvu souboru, použijte [/TC](reference/tc-tp-tc-tp-specify-source-file-type.md) – možnost kompilátoru.

Kompilátor MSVC zahrnuje C Runtime Library (CRT), který je kompatibilní se standardem ISO C99, ale není striktně kompatibilní. Ve většině případů bude přenositelný kód zkompilovat a spustit podle očekávání. Visual C++ nepodporuje některé změny CRT v ISO C11. Některé funkce knihovny a POSIX – názvy funkcí jsou zastaralé kompilátorem MSVC. Jsou podporované, ale upřednostňované názvy změnily. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md) a [upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
