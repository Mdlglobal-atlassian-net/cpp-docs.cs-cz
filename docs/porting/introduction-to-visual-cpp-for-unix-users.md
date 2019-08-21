---
title: Úvod do prostředí Visual C++ pro uživatele systému UNIX
ms.date: 09/01/2017
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 7f73e51e02eafe46c279a8f828803912d8cd190a
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631700"
---
# <a name="introduction-to-visual-c-for-unix-users"></a>Úvod do prostředí Visual C++ pro uživatele systému UNIX

Toto téma poskytuje informace pro uživatele systému UNIX, kteří jsou noví v C++ aplikaci Visual Studio, a chtějí se starat o produktivitu a integrované vývojové prostředí (IDE) sady Visual Studio.

## <a name="getting-started-on-the-command-line"></a>Začínáme na příkazovém řádku

C++ Kompilátor z příkazového řádku můžete použít podobným způsobem, jako byste používali prostředí příkazového řádku UNIX. Zkompilujete z příkazového řádku pomocí příkazového řádku C a C++ kompilátoru (CL. EXE), Linker (odkaz). EXE) a další nástroje, včetně nástroje NMAKE. EXE, verze programu pro systém UNIX.

V systému UNIX se příkazy instalují do společné složky, jako je například/usr/bin. V aplikaci Visual Studio jsou nástroje příkazového řádku nainstalovány v instalačním adresáři sady Visual Studio v podadresáři VC\bin a jeho podadresářích. Na rozdíl od systému UNIX nejsou tyto nástroje k dispozici v prostém okně příkazového řádku. Chcete-li použít nástroje příkazového řádku, použijte zástupce příkazového řádku pro vývojáře nebo spusťte soubor příkazu pro vývojáře, například vcvarsall. bat. Tím se nastaví cesta a další proměnné prostředí, které jsou nezbytné pro zkompilování C++ programů z příkazového řádku. Další informace naleznete v tématu [sestavení C/C++ kód na příkazovém řádku](../build/building-on-the-command-line.md) a [Návod: Kompilování nativního C++ programu na příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).

Zástupce příkazového řádku pro vývojáře otevřete tak, že v ovládacím prvku pro hledání na ploše zadáte *příkaz Developer Command Prompt* a zvolíte **Developer Command Prompt** výsledek pro vaši verzi sady Visual Studio. Chcete-li zvolit příkazový řádek vývojáře, který je předem nakonfigurován pro konkrétní hostitele a cílovou architekturu, otevřete nabídku **Start** (ikonu Windows v rohu plochy) a přejděte do složky vaší verze aplikace Visual Studio, jako je například **vizuál Studio 2017**. Otevřete složku a vyberte zástupce příkazového řádku pro preferovanou hostitele a cílovou architekturu.

Chcete-li využít výhod výkonnějších funkcí, jako je například ladicí program sady Visual Studio, vyhledávání kódu technologie IntelliSense a dokončování příkazů, vizuální návrháře, řízení projektů a tak dále, je nutné použít rozhraní IDE sady Visual Studio.

## <a name="debugging-your-code"></a>Ladění kódu

Použijete-li příkazový řádek a spustíte své aplikace na vaší vývojové pracovní stanici, zobrazí se dialogové okno pro spuštění ladicího programu sady Visual Studio, když váš kód narazí na narušení přístupu k paměti, Neošetřená výjimka nebo jiná neodstranitelná. vyskytl. Pokud kliknete na tlačítko **OK**, bude spuštěno vývojové prostředí sady Visual Studio a ladicí program se otevře v bodě selhání. Je možné ladit aplikace tímto způsobem, a v tomto případě by váš zdrojový kód byl k dispozici pouze v případě, že jste zkompilováni s přepínačem [/Z7,/Zi,/Zi (formát ladicích informací)](../build/reference/z7-zi-zi-debug-information-format.md) . Další informace naleznete v tématu [ladění nativního kódu](/visualstudio/debugger/debugging-native-code) a [použití integrovaného vývojového C++ prostředí (IDE) sady Visual Studio pro desktopový vývoj](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="using-the-development-environment"></a>Použití vývojového prostředí

Pro úpravu a sestavení zdrojového kódu v *projektu*je snazší použít vývojové prostředí. Projekt je kolekce zdrojových a souvisejících souborů, které budou zkompilovány do jedné jednotky, například knihovny nebo spustitelného souboru. Projekt obsahuje také informace o tom, jak mají být soubory sestaveny. Informace o projektech jsou uloženy v souboru projektu s příponou. prj.

Aplikace, která se skládá z více knihoven a spustitelných souborů, z nichž každá je potenciálně sestavena s jinou sadou možností kompilátoru nebo dokonce v jiném jazyce, je uložena ve více projektech, které jsou součástí jednoho *řešení*. Řešení je abstrakcí pro kontejner, který seskupuje více projektů dohromady. Informace o řešeních jsou uloženy v souboru řešení s příponou. sln. Další informace naleznete v tématu [řešení a projekty v aplikaci Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) a [používání integrovaného vývojového C++ prostředí (IDE) sady Visual Studio pro desktopový vývoj](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="importing-your-existing-code"></a>Import existujícího kódu

C++ Kompilátor můžete použít k sestavení stávajícího kódu, který je nastaven pro kompilaci s nebo bez souboru pravidel a jeho vložení do projektu aplikace Visual Studio. Další informace najdete v tématu [jak: Vytvoří C++ projekt z existujícího kódu](../build/how-to-create-a-cpp-project-from-existing-code.md).

## <a name="creating-a-new-project"></a>Vytvoření nového projektu

Ve vývojovém prostředí můžete vytvořit nové projekty. Visual Studio poskytuje mnoho šablon, které poskytují standardní kód pro různé běžné projekty. Můžete použít Průvodce aplikací ke generování projektů s osnovami kódu pro různé typy aplikací.

Můžete začít s prázdným projektem pomocí **Průvodce konzolovou aplikací (Win32)** . Zaškrtněte políčko **prázdný projekt** . Později můžete přidat nové a existující soubory do projektu.

Při vytváření projektu je nutné projekt pojmenovat. Ve výchozím nastavení se název projektu rovná názvu dynamické knihovny (DLL) nebo spustitelného souboru, který je sestaven z projektu. Další informace najdete v tématu [vytváření řešení a projektů](/visualstudio/ide/creating-solutions-and-projects).

## <a name="microsoft-specific-modifiers"></a>Modifikátory specifické pro společnost Microsoft

Kompilátor společnosti C++ Microsoft implementuje několik rozšíření standardního C++ programovacího jazyka pro podporu programování pro operační systémy Windows. Tato rozšíření slouží k určení atributů třídy úložiště, konvencí volání funkce a adresování založeného mimo jiné věci. Úplný seznam všech podporovaných C++ rozšíření najdete v tématu Modifikátory [specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).

Všechna rozšíření specifická pro C++ společnost Microsoft můžete zakázat pomocí `/Za` možnosti kompilátoru. Tato možnost se doporučuje, pokud chcete napsat kód, který se spustí na více platformách. Další informace o `/Za` možnosti kompilátoru naleznete v tématu [/za,/ze (Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md). Další informace o C++ souladu s kompilátorem naleznete v tématu formace a nestandardní [chování](../cpp/nonstandard-behavior.md) [jazyka Visual C++ Language](../overview/visual-cpp-language-conformance.md) .

## <a name="precompiled-headers"></a>Předkompilované hlavičky

Microsoft C a C++ kompilátory poskytují možnosti pro předkompilování kódu C nebo C++ kód, včetně vloženého kódu. Pomocí této funkce výkonu můžete kompilovat stabilní tělo kódu, ukládat zkompilovaný stav kódu v souboru a během následných kompilací kombinovat předkompilovaný kód s kódem, který je stále ve vývoji. Každá následná kompilace je rychlejší, protože stabilní kód není nutné znovu kompilovat.

Ve výchozím nastavení je celý předkompilovaný kód určen v souborech *PCH. h* a *PCH. cpp* (*stdafx. h* a *stdafx. cpp* v aplikaci Visual Studio 2017 a starší). Průvodce **novým projektem** automaticky vytvoří tyto soubory, pokud nevyberete možnost **Předkompilovaná hlavička** . Další informace o předkompilovaných hlavičkách naleznete v tématu [vytváření předkompilovaných hlavičkových souborů](../build/creating-precompiled-header-files.md).

## <a name="related-sections"></a>Související oddíly

Další informace najdete v tématu [přenos ze systému UNIX do Win32](../porting/porting-from-unix-to-win32.md).

## <a name="see-also"></a>Viz také:

[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)
