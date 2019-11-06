---
title: Úvod do Microsoft C++ pro uživatele systému UNIX
ms.date: 10/23/2019
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 791c513553acbd300204746ae1e1dddf7a3ae5c4
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626992"
---
# <a name="introduction-to-microsoft-c-for-unix-users"></a>Úvod do Microsoft C++ pro uživatele systému UNIX

Toto téma poskytuje informace pro uživatele všech charakterů systému UNIX, kteří jsou v nástroji C++ Visual Studio novinkou, a chtějí se stát produktivním z příkazového řádku nebo pomocí sady Visual Studio. Můžete použít Visual Studio s kompilátorem Microsoftu C++ pro cílení na Windows. Můžete také použít integrované vývojové prostředí (IDE) sady Visual Studio s nástrojem RSZ nebo Clang v prostředích systému UNIX, jako jsou například vzdálené počítače se systémem Linux, MinGW-W64 a subsystém Windows pro Linux. Pro použití C++ v aplikaci Visual Studio je nutné nainstalovat **desktopový vývoj s C++**  úlohou. Otevřete Instalační program pro Visual Studio a nainstalujte úlohu nebo přidejte nebo odeberte volitelné součásti. Pokud budete cílit na vzdálený počítač se systémem Linux, nainstalujte také **vývoj pro Linux pomocí C++**  úlohy. Pro vývoj pro Android nebo iOS nainstalujte **mobilní vývoj s C++**  využitím úlohy.

## <a name="getting-started-on-the-command-line"></a>Začínáme s příkazovým řádkem

Kompilátor společnosti Microsoft C++ z příkazového řádku můžete použít podobným způsobem, jako byste používali prostředí příkazového řádku UNIX. Zkompilujete z příkazového řádku pomocí příkazového řádku C a C++ kompilátoru (CL. EXE), Linker (odkaz). EXE) a další nástroje, včetně nástroje NMAKE. EXE, verze programu pro systém UNIX.

V systému UNIX se příkazy instalují do společné složky, jako je například/usr/bin. V aplikaci Visual Studio jsou nástroje příkazového řádku nainstalovány v instalačním adresáři sady Visual Studio v podadresáři VC\bin a jeho podadresářích. Na rozdíl od systému UNIX nejsou tyto nástroje k dispozici v prostém okně příkazového řádku. Chcete-li použít nástroje příkazového řádku, je nutné použít speciální příkazový řádek pro vývojáře, který nastaví cestu a další proměnné prostředí, které jsou nezbytné pro C++ kompilování programů. Další informace naleznete v tématu [sestavení C/C++ kód na příkazovém řádku](../build/building-on-the-command-line.md) a [Návod: kompilování nativního C++ programu na příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).

## <a name="debugging-your-code"></a>Ladění kódu

Můžete použít ladicí program sady Visual Studio pro projekty C++ společnosti Microsoft z příkazového řádku nebo v rámci integrovaného vývojového prostředí (IDE). Zkompilujte pomocí přepínače [/Z7,/Zi,/Zi (formát ladicích informací),](../build/reference/z7-zi-zi-debug-information-format.md) abyste umožnili krokování prostřednictvím zdrojů. Další informace naleznete v tématu [ladění nativního kódu](/visualstudio/debugger/debugging-native-code) a [použití integrovaného vývojového C++ prostředí (IDE) sady Visual Studio pro desktopový vývoj](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

V případě programů kompilovaných pomocí nástroje RSZ nebo Clang vyvolá Visual Studio GDB, LLDB nebo libovolný vlastní ladicí program, který zadáte.

## <a name="visual-studio-project-system"></a>Systém projektu sady Visual Studio

Systém projektu sady Visual Studio se nazývá MSBuild. Používá soubory projektu ve formátu XML; C++ soubory projektu mají příponu. vcxproj. Aplikace, která se skládá z více knihoven a spustitelných souborů, z nichž každá je potenciálně sestavena s jinou sadou možností kompilátoru nebo dokonce v jiném jazyce, je uložena ve více projektech, které jsou součástí jednoho *řešení*. Řešení je abstrakcí pro kontejner, který seskupuje více projektů dohromady. Informace o řešeních jsou uloženy v souboru řešení s příponou. sln. Další informace naleznete v tématu [řešení a projekty v aplikaci Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) a [používání integrovaného vývojového C++ prostředí (IDE) sady Visual Studio pro desktopový vývoj](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). V hlavní nabídce vyberte **soubor** > **Nový** > **projekt** , abyste viděli dostupné šablony projektů sady Visual Studio.

Od sady Visual Studio 2017 se přidá podpora pro projekty CMake a také možnosti pro použití kompilátoru společnosti Microsoft C++ s libovolným systémem sestavení nebo s volnou složkou zdrojových souborů a bez souborů projektu. Další informace najdete v tématu [projekty cmake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md) a [otevřené projekty složek v sadě Visual Studio](../build/open-folder-projects-cpp.md).

## <a name="microsoft-specific-modifiers"></a>Modifikátory specifické pro společnost Microsoft

Kompilátor společnosti C++ Microsoft implementuje několik rozšíření standardního C++ programovacího jazyka pro podporu programování pro operační systémy Windows. Tato rozšíření slouží k určení atributů třídy úložiště, konvencí volání funkce a adresování založeného mimo jiné věci. Úplný seznam všech podporovaných C++ rozšíření najdete v tématu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).

Všechna rozšíření specifická pro C++ společnost Microsoft můžete zakázat pomocí možnosti kompilátoru `/Za`. Tato možnost se doporučuje, pokud chcete napsat kód, který se spustí na více platformách. Další informace o možnosti kompilátoru `/Za` naleznete v tématu [/za,/ze (Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md). Další informace o C++ souladu s kompilátorem najdete v tématu [tabulka C++ shody jazyka Microsoft](../overview/visual-cpp-language-conformance.md) a [nestandardní chování](../cpp/nonstandard-behavior.md).

## <a name="precompiled-headers"></a>Předkompilované hlavičky

Microsoft C a C++ kompilátory poskytují možnosti pro předkompilování kódu C nebo C++ kód, včetně vloženého kódu. Pomocí této funkce výkonu můžete kompilovat stabilní tělo kódu, ukládat zkompilovaný stav kódu v souboru a během následných kompilací kombinovat předkompilovaný kód s kódem, který je stále ve vývoji. Každá následná kompilace je rychlejší, protože stabilní kód není nutné znovu kompilovat.

Ve výchozím nastavení je celý předkompilovaný kód určen v souborech *PCH. h* a *PCH. cpp* (*stdafx. h* a *stdafx. cpp* v aplikaci Visual Studio 2017 a starší). Další informace o předkompilovaných hlavičkách naleznete v tématu [vytváření předkompilovaných hlavičkových souborů](../build/creating-precompiled-header-files.md).

## <a name="related-sections"></a>Související oddíly

Další informace najdete v tématu [spouštění programů systému Linux ve Windows](../porting/porting-from-unix-to-win32.md).

## <a name="see-also"></a>Viz také:

[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)
