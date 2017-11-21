---
title: "Návod: Kompilace programu v jazyce C na příkazovém řádku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
caps.latest.revision: "46"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dfd16b0c3393b6b0a27e88a971042cf772fbd9b1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Návod: Kompilace programu v jazyce C na příkazovém řádku
Visual C++ obsahuje kompilátor C, který můžete použít k vytvoření všechno, co od základní konzoly programy úplné aplikace na ploše systému Windows, mobilní aplikace a další.  
  
 Tento návod ukazuje, jak vytvořit základní, "Hello, World"-stylu programu C pomocí textového editoru a pak jeho kompilace příkazového řádku. Pokud by se místo fungovat v jazyce C++ v příkazovém řádku, najdete v části [návod: kompilace nativního programu C++ v příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Pokud chcete akci prostředí Visual Studio IDE místo pomocí příkazového řádku najdete v tématu [návod: práce s projekty a řešeními (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) nebo [pomocí prostředí Visual Studio IDE pro vývoje v jazyce C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## <a name="prerequisites"></a>Požadavky  
 Pro dokončení tohoto návodu, musíte instalaci sady Visual Studio a volitelné součásti Visual C++ nebo Microsoft Visual C++ sestavení nástroje.  
  
 Visual Studio je výkonný integrované vývojové prostředí, které podporuje o plně vybavený editor, správci prostředků, ladicí programy a kompilátory pro mnoho jazyky a platformy. Informace o těchto funkcích a o tom, jak stáhnout a nainstalovat Visual Studio, včetně edice free Visual Studio Community, najdete v části [VisualStudio.com](https://www.visualstudio.com/).  
  
 Visual Studio Tools sestavení nainstaluje pouze kompilátory příkazového řádku, nástroje a knihovny, které potřebujete k vytvoření programy C a C++. Je ideální pro prostředí sestavení nebo učebny vykonává a nainstaluje poměrně rychle. Chcete-li nainstalovat jenom nástroje příkazového řádku, stáhněte [sestavení nástroje sady Visual Studio](https://go.microsoft.com/fwlink/?linkid=840931) a spusťte instalační program. Další informace najdete v tématu [nástroje sestavení Visual C++](http://landinghub.visualstudio.com/visual-cpp-build-tools).  
  
 Před sestavením programu jazyka C nebo C++ v příkazovém řádku, je nutné ověřit, zda jsou nainstalovány nástroje a že se dostanete z příkazového řádku. Visual C++ má komplexní požadavky na prostředí příkazového řádku a hledat tak nástroje, hlavičky a knihovny, které používá. **Visual C++ nelze použít v okně příkazového řádku prostý**. Je nutné *příkazový řádek vývojáře* okno, které je okno regulární příkazového řádku, který nemá všechny požadované prostředí proměnné nastavit. Naštěstí Visual C++ nainstaluje zástupce můžete spustit na příkazovém řádku vývojáře se mají nastavit pro sestavení příkazového řádku prostředí. Bohužel názvy zástupce příkazového řádku vývojáře a kde se nacházejí se liší v téměř všechny verze aplikace Visual C++ a v různých verzích systému Windows. První úlohu návod je nalezení správné zástupce, který chcete použít.  
  
> [!NOTE]
>  Zástupce příkazového řádku vývojáře automaticky nastaví správné cesty pro kompilátoru a nástroje a pro všechny požadované hlavičky a knihovny. Některé z těchto hodnot se liší u každé konfiguraci sestavení. Je nutné nastavit tyto hodnoty prostředí sami Pokud nepoužijete mezi zástupce. Další informace najdete v tématu [nastavit cesty a proměnných prostředí pro sestavení příkazového řádku](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Protože je komplexní prostředí sestavení, důrazně doporučujeme, že abyste použili zástupce příkazového řádku vývojáře místo vytváření vlastní.  
  
## <a name="open-a-developer-command-prompt"></a>Otevřete příkazový řádek vývojáře  
  
1.  Pokud jste nainstalovali Visual Studio 2017 ve Windows 10, otevření nabídky Start a potom přejděte dolů a otevřete **Visual Studio 2017** složce (ne aplikace Visual Studio 2017). Zvolte **příkazový řádek vývojáře pro VS 2017** a otevřete okno příkazového řádku.  
  
     Pokud jste nainstalovali Microsoft Visual C++ sestavení nástroje 2015 na Windows 10, otevřete **spustit** nabídce a potom přejděte dolů a otevřete **nástroje sestavení Visual C++** složky. Zvolte **Visual C++ 2015 x86 nativní nástroje příkazového řádku** a otevřete okno příkazového řádku.  
  
     Pokud používáte jinou verzi sady Visual Studio nebo běží s jinou verzí systému Windows, vyhledejte v nabídce Start nebo úvodní stránka pro složky nástroje pro Visual Studio, který obsahuje zástupce příkazového řádku vývojáře. Funkce vyhledávání systému Windows můžete použít také k hledání "příkazový řádek vývojáře" a vyberte ten, který se shoduje s nainstalovanou verzí sady Visual Studio. Otevřete okno příkazového řádku pomocí klávesové zkratky.  
  
2.  Dále ověřte, zda příkazový řádek vývojáře Visual C++ je správně. V okně příkazového řádku zadejte `cl` a ověřte, že výstup vypadá přibližně takto:  
  
    ```Output  
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl  
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
    
    usage: cl [ option... ] filename... [ /link linkoption... ]  
    
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>  
    ```  
  
     Může docházet k rozdílům v aktuálním adresáři nebo číslo verze, a to v závislosti na verzi Visual C++ a nainstalovány žádné aktualizace. Pokud je to podobné co vidíte, pak jste připraveni k sestavení programy C nebo C++ v příkazovém řádku.  
  
    > [!NOTE]
    >  Pokud dojde k chybě, jako je "'cl' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru" Chyba C1034 nebo chyba LNK1104 při spuštění **cl** příkaz, pak buď nejsou pomocí příkazového řádku vývojáře nebo je něco špatně s instalací sady Visual C++. Než budete pokračovat, je nutné opravit tento problém.  
  
     Pokud nemůžete najít vývojář zástupce příkazového řádku, nebo pokud se zobrazí chybové hlášení, když zadáte `cl`, pak instalaci aplikace Visual C++ pravděpodobně došlo k potížím. Zkuste znovu nainstalovat součást Visual C++ v sadě Visual Studio nebo Visual Studio Tools sestavení přeinstalujte. Nemáte přejděte k další části dokud to funguje. Další informace o instalaci a řešení potíží s Visual C++ najdete v tématu [instalaci sady Visual Studio](/visualstudio/install/install-visual-studio).  
  
    > [!NOTE]
    >  V závislosti na verzi Windows na počítači a konfiguraci zabezpečení systému, možná budete muset pravým tlačítkem a otevřete místní nabídku pro vývojáře zástupce příkazového řádku a potom zvolte **spustit jako správce** na úspěšně sestavit a spustit program, který vytvoříte podle tohoto návodu.  
  
## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Vytvoření C zdrojového souboru a jeho kompilace příkazového řádku  
  
1.  V okně příkazového řádku vývojáře zadejte **cd c:\\**  změnit aktuální pracovní adresář na kořenové jednotce C:. Potom zadejte **md c:\simple** vytvořte adresář, a potom zadejte **cd c:\simple** tohoto adresáře. Toto je adresář, který bude obsahovat zdrojový soubor a zkompilovaný program.  
  
2.  Zadejte **simple.c Poznámkový blok** příkazového řádku vývojáře. V výstrahy dialogovém okně Poznámkový blok, která se objeví, zvolte **Ano** k vytvoření nového souboru simple.c v pracovní adresář.  
  
3.  V poznámkovém bloku zadejte následující řádky kódu:  
  
    ```C  
    #include <stdio.h>  
  
    int main()  
    {  
        printf("Hello, World! This is a native C program compiled on the command line.\n");  
        return 0;  
    }   
    ```  
  
4.  V řádku nabídek Poznámkový blok, zvolte **soubor**, **Uložit** uložit simple.c v pracovním adresáři.  
  
5.  Přepněte zpátky na okno příkazového řádku vývojáře. Zadejte **dir** na příkazovém řádku zobrazit obsah adresáře c:\simple. Měli byste vidět simple.c souboru zdroje v seznamu adresářů, která vypadá přibližně takto:  
  
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
  
     Kalendářní data a další podrobnosti se budou lišit v počítači. Pokud nevidíte vašeho souboru se zdrojovým kódem, simple.c, ujistěte se, že jste změnili c:\simple adresář, který jste vytvořili a v poznámkovém bloku, ujistěte se, že jste uložili zdrojový soubor v tomto adresáři. Ujistěte se také ukládají zdrojový kód s .c příponu názvu, příponu .txt.  
  
6.  Kompilace programu, zadejte **cl simple.c** příkazového řádku vývojáře.  
  
     Zobrazí název spustitelný program simple.exe řádků kompilátor zobrazí výstup informace:  
  
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
    >  Pokud dojde k chybě, jako je "'cl' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru" Chyba C1034 nebo chyba LNK1104, vaše příkazový řádek vývojáře není správně nastaven. Informace o tom, jak tento problém vyřešit, přejděte zpět na **otevřete příkazový řádek vývojáře** části.  
  
    > [!NOTE]
    >  Pokud se objeví jiné kompilátoru nebo linkeru chyby nebo upozornění, zkontrolujte zdrojový kód a opravte všechny chyby, pak jej uložit a znovu spusťte kompilátoru. Informace o konkrétní chyby použijte pole hledání na této stránce MSDN hledání číslo chyby.  
  
7.  Chcete-li spustit program, zadejte **jednoduché** na příkazovém řádku.  
  
     Program zobrazí tento text a pak bude ukončen:  
  
    ```Output  
    Hello, World! This is a native C program compiled on the command line.  
    ```  
  
     Blahopřejeme, jste právě zkompilovat a spuštění programu C pomocí příkazového řádku.  
  
## <a name="next-steps"></a>Další kroky  
 V tomto příkladu "Hello, World" je o stejně jednoduché jako programu C můžete získat. Programy skutečných mít soubory hlaviček a další zdrojové soubory, na odkaz v knihovnách a užitečné práci.  
  
 Kroky v tomto návodu můžete použít k vytvoření vlastního kódu C místo zadání ukázkový kód ukazuje. Můžete také vytvořit mnoho C kód ukázkové programy, které můžete najít jinde. Kompilace programu, který má více soubory zdrojového kódu, zadejte je všechny na příkazovém řádku, například takto:  
  
 `cl file1.c file2.c file3.c`  
  
 Kompilátor výstupy program s názvem file1.exe. Chcete-li změnit název na program1.exe, přidejte [/out](../build/reference/out-output-file-name.md) – možnost linkeru:  
  
 `cl file1.c file2.c file3.c /link /out:program1.exe`  
  
 K zachycení více programovacích chyb automaticky, doporučujeme zkompilujete pomocí [/W3](../build/reference/compiler-option-warning-level.md) nebo [/W4](../build/reference/compiler-option-warning-level.md) upozornění úrovně možnost:  
  
 `cl /W4 file1.c file2.c file3.c /link /out:program1.exe`  
  
 Kompilátor, cl.exe, má mnoho dalších možností, můžete použít k sestavení, optimalizace, ladění a analýze kódu. Seznam rychlé zadejte **cl /?** na příkazovém řádku vývojáře. Můžete také zkompilovat a propojit samostatně a použít možnosti linkeru ve složitějších scénářích sestavení. Další informace o kompilátoru a linkeru možnosti a využití najdete v tématu [odkaz sestavení C/C++](../build/reference/c-cpp-building-reference.md).  
  
 NMAKE a soubory pravidel nebo MSBuild a projekt soubory můžete použít ke konfiguraci a složitější projekty sestavení na příkazovém řádku. Další informace o používání těchto nástrojů najdete v tématu [NMAKE – odkaz](../build/nmake-reference.md) a [MSBuild](../build/msbuild-visual-cpp.md).  
  
 Jazyky C a C++ jsou podobné, ale nejsou stejné. Kompilátor Visual C++ pomocí jednoduché pravidlo určuje jazyk, který se má použít při kompilaci kódu. Ve výchozím nastavení Visual C++ compiler zpracovává všechny soubory, které končí jako zdrojový kód C a všechny soubory, které končí sada jako C++ zdrojového kódu. Chcete-li vynutit kompilátor považovat všechny soubory C bez ohledu na příponu názvu souboru, použijte [/Tc](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) – možnost kompilátoru.  
  
 Kompilátor Visual C++ C je obecně kompatibilní se standardem ISO C99, ale výhradně kompatibilní. Ve většině případů přenosné C – kód zkompilování a spouštějí se podle očekávání. Visual C++ nepodporuje většinu změn v ISO C11. Visual C++ compiler nepoužívají určité funkce knihovny a názvy funkcí POSIX. Jsou podporované, ale upřednostňované názvy změnily. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md) a [upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření standardního programu C++ (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)   
 [Referenční dokumentace jazyka C](../c-language/c-language-reference.md)   
 [Sestavení C/C++ programů](../build/building-c-cpp-programs.md)   
 [Kompatibilita](../c-runtime-library/compatibility.md)