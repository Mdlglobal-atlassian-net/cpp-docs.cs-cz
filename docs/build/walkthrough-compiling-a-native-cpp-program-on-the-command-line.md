---
title: "Návod: Kompilace nativního programu C++ v příkazovém řádku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
caps.latest.revision: "63"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64bd526bfd72c16cc993d3992c179f107a35fbd8
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Návod: Kompilace nativního programu C++ v příkazovém řádku
Visual C++ zahrnuje příkazového řádku kompilátoru C++, který můžete použít k vytvoření všechno z základní konzole aplikace pro univerzální aplikace pro Windows, aplikace pro Windows Store a součásti rozhraní .NET.  
  
 V tomto návodu vytvoříte základní, "Hello, World"-stylu programu C++ pomocí textového editoru a pak jeho kompilace příkazového řádku. Pokud chcete akci prostředí Visual Studio IDE místo pomocí příkazového řádku najdete v tématu [návod: práce s projekty a řešeními (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) nebo [pomocí prostředí Visual Studio IDE pro vývoje v jazyce C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
 V tomto návodu můžete použít vlastní program Visual C++ místo zadání ten, který se zobrazí, nebo můžete ukázku kódu jazyka Visual C++ z jiný článek nápovědy.  
  
## <a name="prerequisites"></a>Požadavky  
 Pro dokončení tohoto návodu, musíte instalaci sady Visual Studio a volitelné součásti Visual C++ nebo Microsoft Visual C++ sestavení nástroje.  
  
 Visual Studio je výkonný integrované vývojové prostředí, které podporuje o plně vybavený editor, správci prostředků, ladicí programy a kompilátory pro mnoho jazyky a platformy. Informace o těchto funkcích a o tom, jak stáhnout a nainstalovat Visual Studio, včetně edice free Visual Studio Community, najdete v části [VisualStudio.com](https://www.visualstudio.com/).  
  
 Visual Studio Tools sestavení nainstaluje pouze kompilátory příkazového řádku, nástroje a knihovny, které potřebujete k vytvoření programy C a C++. Je ideální pro prostředí sestavení nebo učebny vykonává a nainstaluje poměrně rychle. Chcete-li nainstalovat jenom nástroje příkazového řádku, stáhněte [sestavení nástroje sady Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=840931) a spusťte instalační program. Další informace najdete v tématu [nástroje sestavení Visual C++](http://landinghub.visualstudio.com/visual-cpp-build-tools).  
  
 Před sestavením programu jazyka C nebo C++ v příkazovém řádku, je nutné ověřit, zda jsou nainstalovány nástroje a že se dostanete z příkazového řádku. Visual C++ má komplexní požadavky na prostředí příkazového řádku a hledat tak nástroje, hlavičky a knihovny, které používá. **Visual C++ nelze použít v okně příkazového řádku prostý**. Naštěstí Visual C++ nainstaluje zástupce můžete spustit příkazový řádek vývojáře, který má prostředí pro sestavení příkazového řádku. Bohužel názvy zástupce příkazového řádku vývojáře a kde se nacházejí se liší v téměř všechny verze aplikace Visual C++ a v různých verzích systému Windows. První úlohu návod je hledání ten správný používat.  
  
> [!NOTE]
>  Zástupce příkazového řádku vývojáře automaticky nastaví správné cesty pro kompilátoru a nástroje a pro všechny požadované hlavičky a knihovny. Je nutné nastavit tyto hodnoty prostředí sami používáte-li regulární okno příkazového řádku. Další informace najdete v tématu [nastavit cesty a proměnných prostředí pro sestavení příkazového řádku](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Doporučujeme, že abyste použili zástupce příkazového řádku vývojáře místo vytváření vlastní.  
  
### <a name="open-a-developer-command-prompt"></a>Otevřete příkazový řádek vývojáře  
  
1.  Pokud jste nainstalovali Visual Studio 2017 na Windows 10, otevřete nabídku Start a zvolte **všechny aplikace**. Přejděte dolů a otevřete **Visual Studio 2017** složce (ne aplikace Visual Studio 2017). Zvolte **příkazový řádek vývojáře pro VS 2017** a otevřete okno příkazového řádku.  
  
     Pokud jste nainstalovali Microsoft Visual C++ sestavení nástroje 2015 na Windows 10, otevřete **spustit** nabídky a zvolte **všechny aplikace**. Přejděte dolů a otevřete **nástroje sestavení Visual C++** složky. Zvolte **Visual C++ 2015 x86 nativní nástroje příkazového řádku** a otevřete okno příkazového řádku.  
  
     Pokud používáte jinou verzi sady Visual Studio nebo běží s jinou verzí systému Windows, vyhledejte v nabídce Start nebo úvodní stránka pro složky nástroje pro Visual Studio, který obsahuje zástupce příkazového řádku vývojáře. Funkce vyhledávání systému Windows můžete použít také k hledání "příkazový řádek vývojáře" a vyberte ten, který se shoduje s nainstalovanou verzí sady Visual Studio. Otevřete okno příkazového řádku pomocí klávesové zkratky.  
  
2.  Dále ověřte, zda příkazový řádek vývojáře Visual C++ je správně. V okně příkazového řádku zadejte `cl` a ověřte, že výstup vypadá přibližně takto:  
  
    ```Output  
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl  
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
    
    usage: cl [ option... ] filename... [ /link linkoption... ]  
    ```  
  
     Může docházet k rozdílům v aktuálním adresáři nebo číslo verze, a to v závislosti na verzi Visual C++ a nainstalovány žádné aktualizace. Pokud je to podobné co vidíte, pak jste připraveni k sestavení programy C nebo C++ v příkazovém řádku.  
  
    > [!NOTE]
    >  Pokud dojde k chybě, jako je "'cl' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru" Chyba C1034 nebo chyba LNK1104 při spuštění **cl** příkaz, pak buď nejsou pomocí příkazového řádku vývojáře nebo je něco špatně s instalací sady Visual C++. Než budete pokračovat, je nutné opravit tento problém.  
  
     Pokud nemůžete najít vývojář zástupce příkazového řádku, nebo pokud se zobrazí chybové hlášení, když zadáte `cl`, pak instalaci aplikace Visual C++ pravděpodobně došlo k potížím. Zkuste znovu nainstalovat součást Visual C++ v sadě Visual Studio, nebo znovu nainstalovat sadu Microsoft Visual C++ sestavení Tools. Nemáte přejděte k další části dokud to funguje. Další informace o instalaci a řešení potíží s Visual C++ najdete v tématu [instalaci sady Visual Studio](/visualstudio/install/install-visual-studio).  
  
    > [!NOTE]
    >  V závislosti na verzi Windows na počítači a konfiguraci zabezpečení systému, možná budete muset pravým tlačítkem a otevřete místní nabídku pro vývojáře zástupce příkazového řádku a potom zvolte **spustit jako správce** na úspěšně sestavit a spustit program, který vytvoříte podle tohoto návodu.  
  
### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Vytvoření zdrojového souboru Visual C++ a jeho kompilace příkazového řádku  
  
1.  V okně příkazového řádku vývojáře zadejte **md c:\hello** vytvořte adresář, a potom zadejte **cd c:\hello** tohoto adresáře. Toto je adresář, který váš zdrojový soubor a zkompilovaný program se vytvoří v.  
  
2.  Zadejte **Poznámkový blok hello.cpp** v okně příkazového řádku.  
  
     Zvolte **Ano** při Poznámkový blok vás vyzve k vytvoření souboru. Otevře se okno prázdné Poznámkový blok připravené k zadejte svůj kód do souboru s názvem hello.cpp.  
  
3.  V poznámkovém bloku zadejte následující řádky kódu:  
  
    ```cpp  
    #include <iostream>  
    using namespace std;  
    void main()  
    {  
        cout << "Hello, world, from Visual C++!" << endl;  
    }  
    ```  
  
     To je velmi jednoduchý program, který bude zapisovat jeden řádek textu na obrazovce a poté ukončete. Chcete-li minimalizovat chyby, zkopírujte tento kód a vložte do poznámkového bloku.  
  
4.  Uložte si práci! V poznámkovém bloku na **soubor** nabídce zvolte **Uložit**.  
  
     Blahopřejeme, jste vytvořili zdrojový soubor Visual C++ hello.cpp, který je připraven ke kompilaci.  
  
5.  Přepněte zpátky na okno příkazového řádku vývojáře. Zadejte **dir** na příkazovém řádku zobrazit obsah adresáře c:\hello. Měli byste vidět hello.cpp souboru zdroje v seznamu adresářů, která vypadá přibližně takto:  
  
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
  
     Kalendářní data a další podrobnosti se budou lišit v počítači. Pokud nevidíte vašeho souboru se zdrojovým kódem, hello.cpp, ujistěte se, že jste změnili c:\hello adresář, který jste vytvořili a v poznámkovém bloku, ujistěte se, že jste uložili zdrojový soubor v tomto adresáři. Ujistěte se také ukládají zdrojový kód s sada příponu názvu, příponu .txt.  
  
6.  Zadejte na příkazovém řádku vývojáře `cl /EHsc hello.cpp` zkompilovat vašeho programu.  
  
     Kompilátor cl.exe vygeneruje soubor .obj, který obsahuje zkompilovaný kód a poté spustí linkeru pro vytvoření spustitelný program s názvem hello.exe. Tento název se zobrazí v řádků výstup informace, které zobrazí kompilátoru. Výstup kompilátoru by měl vypadat přibližně takto:  
  
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
    >  Pokud dojde k chybě, jako je "'cl' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru" Chyba C1034 nebo chyba LNK1104, vaše příkazový řádek vývojáře není správně nastaven. Informace o tom, jak tento problém vyřešit, přejděte zpět na **otevřete příkazový řádek vývojáře** části.  
  
    > [!NOTE]
    >  Pokud se objeví jiné kompilátoru nebo linkeru chyby nebo upozornění, zkontrolujte zdrojový kód a opravte všechny chyby, pak jej uložit a znovu spusťte kompilátoru. Informace o konkrétní chyby použijte pole hledání na této stránce MSDN hledání číslo chyby.  
  
7.  Chcete-li hello.exe program, spusťte na příkazovém řádku, zadejte `hello`.  
  
     Program zobrazí tento text a bude ukončen:  
  
    ```Output  
    Hello, world, from Visual C++!  
    ```  
  
     Blahopřejeme, jste právě zkompilovat a spuštění programu C++ pomocí nástroje příkazového řádku.  
  
## <a name="next-steps"></a>Další kroky  
 V tomto příkladu "Hello, World" je o stejně jednoduché jako programu C++ můžete získat. Programy skutečných mít soubory hlaviček a další zdrojové soubory, na odkaz v knihovnách a užitečné práci.  
  
 Kroky v tomto návodu můžete použít k vytvoření vlastního kódu C++ místo zadání ukázkový kód ukazuje. Můžete také vytvořit mnoho C++ kód ukázkové programy, které můžete najít jinde. Můžete vložit vašeho zdrojového kódu a sestavení aplikace v libovolného adresáře nelze zapisovat. Ve výchozím nastavení vytvoří Visual Studio IDE projekty do složky Dokumenty v podsložce projektů sady Visual Studio složku s názvem pro vaši verzi sady Visual Studio.  
  
 Kompilace programu, který má více soubory zdrojového kódu, zadejte je všechny na příkazovém řádku, například takto:  
  
 `cl /EHsc file1.cpp file2.cpp file3.cpp`  
  
 **/EHsc** možnost příkazového řádku dává pokyn kompilátoru umožňující zpracování výjimek jazyka C++. Další informace najdete v tématu [/EH (Model zpracování výjimek)](../build/reference/eh-exception-handling-model.md).  
  
 Pokud zadáte více zdrojových souborů, jako to, kompilátor použije první vstupní soubor vytvořit název programu. V takovém případě výstupy program s názvem file1.exe. Chcete-li změnit název na program1.exe, přidejte [/out](../build/reference/out-output-file-name.md) – možnost linkeru:  
  
 `cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`  
  
 K zachycení více programovacích chyb automaticky, doporučujeme zkompilujete pomocí [/W3](../build/reference/compiler-option-warning-level.md) nebo [/W4](../build/reference/compiler-option-warning-level.md) upozornění úrovně možnost:  
  
 `cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`  
  
 Kompilátor, cl.exe, má mnoho dalších možností, můžete použít k sestavení, optimalizace, ladění a analýze kódu. Seznam rychlé zadejte **cl /?** na příkazovém řádku vývojáře. Můžete také zkompilovat a propojit samostatně a použít možnosti linkeru ve složitějších scénářích sestavení. Další informace o kompilátoru a linkeru možnosti a využití najdete v tématu [odkaz sestavení C/C++](../build/reference/c-cpp-building-reference.md).  
  
 NMAKE a soubory pravidel nebo MSBuild a projekt soubory můžete použít ke konfiguraci a složitější projekty sestavení na příkazovém řádku. Další informace o používání těchto nástrojů najdete v tématu [NMAKE – odkaz](../build/nmake-reference.md) a [MSBuild](../build/msbuild-visual-cpp.md).  
  
 Jazyky C a C++ jsou podobné, ale nejsou stejné. Kompilátor Visual C++ pomocí jednoduché pravidlo určuje jazyk, který se má použít při kompilaci kódu. Ve výchozím nastavení Visual C++ compiler zpracovává všechny soubory, které končí jako zdrojový kód C a všechny soubory, které končí sada jako C++ zdrojového kódu. Chcete-li vynutit kompilátor považovat všechny soubory C++ bez ohledu na příponu názvu souboru, použijte [/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) – možnost kompilátoru.  
  
 Visual C++ compiler zahrnuje C Runtime Library (CRT), je obecně kompatibilní se standardem ISO C99, ale výhradně kompatibilní. Ve většině případů bude přenosné kód zkompilovat a spouštějí se podle očekávání. Visual C++ nepodporuje některé změny CRT v ISO C11. Visual C++ compiler nepoužívají určité funkce knihovny a názvy funkcí POSIX. Jsou podporované, ale upřednostňované názvy změnily. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md) a [upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Sestavení C/C++ programů](../build/building-c-cpp-programs.md)   
 [Možnosti kompilátoru](../build/reference/compiler-options.md)