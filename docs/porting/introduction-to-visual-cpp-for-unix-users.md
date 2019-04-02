---
title: Úvod do prostředí Visual C++ pro uživatele systému UNIX
ms.date: 09/01/2017
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 2b0736bca9cc0b67f9ea8ac83dc18fadaeefdb3c
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780818"
---
# <a name="introduction-to-visual-c-for-unix-users"></a>Úvod do prostředí Visual C++ pro uživatele systému UNIX

Toto téma obsahuje informace pro uživatele systému UNIX, kteří se ještě sadu Visual Studio a chcete se stát produktivity pomocí C++ a Visual Studio integrované vývojové prostředí (IDE).

## <a name="getting-started-on-the-command-line"></a>Začínáme na příkazovém řádku

Kompilátor C++ z příkazového řádku můžete použít podobným způsobem použijete prostředí příkazového řádku systému UNIX. Při kompilaci z příkazového řádku pomocí příkazového řádku kompilátoru jazyka C a C++ (CL. Soubor EXE) linkeru (odkaz. Soubor EXE) a další nástroje, včetně NMAKE. Soubor EXE, Microsoft verze systémů UNIX Zkontrolujte nástroj.

V systému UNIX příkazy jsou nainstalovány v běžné složky, například/usr/bin. V sadě Visual Studio nástroje příkazového řádku jsou nainstalovány v adresáři instalace sady Visual Studio v podadresáři VC\bin a jeho podadresářích. Na rozdíl od systému UNIX tyto nástroje nejsou k dispozici v okně prostý příkazového řádku. Použití nástrojů příkazového řádku, použijte zástupce příkazového řádku pro vývojáře nebo spustit příkaz vývojář souboru, například vcvarsall.bat. Tím se nastaví cesta i ostatním proměnným prostředí, které jsou nezbytné pro kompilaci programy v jazyce C++ z příkazového řádku. Další informace najdete v tématu [kódu sestavení C/C++ v příkazovém řádku](../build/building-on-the-command-line.md) a [názorný postup: Kompilace nativního programu C++ v příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).

Chcete-li spustit nástroj zástupce příkazového řádku pro vývojáře, zadejte *příkazový řádek pro vývojáře* v desktopu hledat ovládací prvek a vyberte **Developer Command Prompt** výsledek pro vaši verzi sady Visual Studio. Chcete-li vyberte příkazový řádek pro vývojáře, který je předem konkrétního hostitele a Cílová architektura, otevřete **Start** nabídky (Windows ikonu v pravém rohu plochy) a přejděte do složky pro vaši verzi sady Visual Studio , jako například **Visual Studio 2017**. Otevřete složku a zvolte zástupce příkazového řádku pro upřednostňované hostitele a cílové architektury.

Využívat výkonnější projekt funkce, jako je ladicí program sady Visual Studio, vyhledávání a příkaz dokončování kódu IntelliSense, vizuální návrhářské nástroje, Správa a tak dále, musíte použít Visual Studio IDE.

## <a name="debugging-your-code"></a>Ladění kódu

Pokud používáte příkazový řádek a spouštění aplikací na stanici vývoje, uvidíte, že pokud váš kód zjistí narušení přístupu k paměti, neošetřené výjimky nebo další neopravitelné, zobrazí se dialogové okno spustit ladicí program sady Visual Studio chyby. Vyberete-li **OK**, pak spuštění vývojového prostředí sady Visual Studio a ladicí program se otevře do bodu selhání. Chcete-li ladit tímto způsobem vašich aplikací a v takovém případě zdrojový kód by být k dispozici pouze pokud kompilujete s [/Z7, / zi, /ZI (formát informací o ladění)](../build/reference/z7-zi-zi-debug-information-format.md) přepnout. Další informace najdete v tématu [ladění nativního kódu](/visualstudio/debugger/debugging-native-code) a [pomocí integrovaného vývojového prostředí sady Visual Studio pro vývoj v jazyce C++ Desktop](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="using-the-development-environment"></a>Použití vývojového prostředí

Je jednodušší použít vývojové prostředí pro úpravy a vytváření zdrojového kódu *projektu*. Projekt je kolekce zdroje a související soubory, které budou zkompilovány do jedné jednotky, jako je například knihovna nebo spustitelný soubor. Projekt obsahuje také informace o tom, jak mají být vytvořeny soubory. Informace o projekty jsou uloženy v souboru projektu s příponou .prj.

Aplikace, která se skládá z více knihoven a spustitelné soubory, každý potenciálně integrované s různou sadou možností kompilátoru nebo dokonce i v jiném jazyce, jsou uloženy ve více projektech, které jsou součástí jedné *řešení*. Řešení je abstrakcí pro kontejner k seskupení více projektů. Informace o řešení jsou uloženy v souboru s příponou .sln řešení. Další informace najdete v tématu [řešení a projekty v sadě Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) a [pomocí integrovaného vývojového prostředí sady Visual Studio pro vývoj v jazyce C++ Desktop](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="importing-your-existing-code"></a>Import existujícího kódu

Kompilátor C++ můžete použít k sestavení existující kód, který je nastavený na kompilovat s nebo bez souboru pravidel a vložit ho do projektu sady Visual Studio. Další informace najdete v tématu [jak: Vytvoření projektu jazyka C++ z existujícího kódu](../build/how-to-create-a-cpp-project-from-existing-code.md).

## <a name="creating-a-new-project"></a>Vytvoření nového projektu

Vytvořit nové projekty ve vývojovém prostředí. Visual Studio poskytuje mnoho šablon, které poskytují standardní kód pro mnoho běžných projektů. Průvodci aplikací můžete použít ke generování projektů s obrysy kódu pro různé typy aplikací.

Můžete začít s prázdným projektem pomocí **Konzolová aplikace (Win32) průvodce**. Vyberte **prázdný projekt** zaškrtávací políčko. Potom přidáte nové i stávající soubory do projektu později.

Když vytvoříte projekt, je třeba zadat název projektu. Ve výchozím nastavení název projektu rovná název dynamická knihovna (DLL) nebo spustitelný soubor, který je sestaven z projektu. Další informace najdete v tématu [vytváření řešení a projekty](/visualstudio/ide/creating-solutions-and-projects).

## <a name="microsoft-specific-modifiers"></a>Modifikátory specifické pro společnost Microsoft

Kompilátor jazyka Microsoft Visual C++ implementuje několik rozšíření pro standardní programovací jazyk C++ pro podporu programování pro operační systémy Windows. Tato rozšíření se používají k určení atributů třídy úložiště, konvence volání funkce a adresování, mimo jiné. Úplný seznam všech podporovaných rozšíření jazyka C++, naleznete v tématu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).

Pomocí můžete zakázat všechna rozšíření specifické pro společnost Microsoft c++ `/Za` – možnost kompilátoru. Tato možnost se doporučuje, pokud chcete napsat kód, který spouští na více platformách. Další informace o `/Za` – možnost kompilátoru, naleznete v tématu [/Za, /Ze (zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md). Další informace o přizpůsobení kompilátoru C++, naleznete v tématu [shoda jazyka Visual C++](../overview/visual-cpp-language-conformance.md) a [nestandardní chování](../cpp/nonstandard-behavior.md).

## <a name="precompiled-headers"></a>Předkompilované hlavičky

Kompilátory Microsoft C a C++ poskytují možnosti pro předkompilaci kódu jakékoli jazyka C nebo C++, včetně vložený kód. Pomocí této výkonné funkce, můžete zkompilovat stabilní části kódu, uložit zkompilovaný kód do souboru a, při následných kompilací kombinovat předkompilovaný kód s kódem, který je stále ve vývoji. Každé následné kompilace je rychlejší, protože není potřeba překompilovat stabilní kód.

Ve výchozím nastavení je všechny předkompilovaný kód zadaný do souborů stdafx.h a stdafx.cpp. **Nový projekt** průvodce automaticky vytvoří tyto soubory můžete pokud nezrušíte **Předkompilovaná hlavička** možnost. Další informace o předkompilovaných hlaviček, naleznete v tématu [vytváření Předkompilované soubory hlaviček](../build/creating-precompiled-header-files.md).

## <a name="related-sections"></a>Související oddíly

Další informace najdete v tématu [Portování ze systému UNIX do Win32](../porting/porting-from-unix-to-win32.md).

## <a name="see-also"></a>Viz také:

[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)
