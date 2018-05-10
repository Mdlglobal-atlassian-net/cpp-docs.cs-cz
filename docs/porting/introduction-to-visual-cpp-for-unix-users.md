---
title: Úvod do jazyka Visual C++ pro uživatele systému UNIX | Microsoft Docs
ms.custom: ''
ms.date: 09/01/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f05d7d3d3d3fd6b40a5477b7765b89409747d3ce
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="introduction-to-visual-c-for-unix-users"></a>Úvod do prostředí Visual C++ pro uživatele systému UNIX

Toto téma obsahuje informace pro uživatele systému UNIX, kteří jsou nové pro Visual Studio a chcete zvýšení produktivity s C++ a prostředí Visual Studio integrované vývoj prostředí (IDE).
  
## <a name="getting-started-on-the-command-line"></a>Začínáme na příkazovém řádku  

Kompilátor C++ z příkazového řádku můžete použít podobným způsobem, že byste použili prostředí příkazového řádku systému UNIX. Při kompilaci z příkazového řádku pomocí příkazového řádku kompilátoru jazyka C a C++ (CL. Soubor EXE), linkeru (odkaz. Soubor EXE) a dalších nástrojů, včetně NMAKE. EXE verze Microsoft UNIX Zkontrolujte nástroj.  
  
V systému UNIX příkazy jsou nainstalovány v běžné složce, například/usr/bin. V sadě Visual Studio jsou nainstalované nástroje příkazového řádku v adresáři instalace sady Visual Studio v podadresáři VC\bin a jejích podadresářů. Na rozdíl od systému UNIX tyto nástroje nejsou k dispozici v okně prostý příkazového řádku. Použití nástroje příkazového řádku, použijte zástupce příkazového řádku vývojáře nebo spustit příkaz vývojář souboru, například vcvarsall.bat. Toto nastaví cestu a jiné proměnné prostředí, které jsou nezbytné pro kompilaci C++ – programy z příkazového řádku. Další informace najdete v tématu [kódu sestavení C/C++ v příkazovém řádku](../build/building-on-the-command-line.md) a [návod: kompilace nativního programu C++ v příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
Otevřete příkazový řádek vývojáře zástupce, zadejte *příkazového řádku vývojáře* v ploše vyhledávání ovládací prvek a vyberte **příkazový řádek vývojáře** výsledek pro vaši verzi sady Visual Studio. Chcete-li zvolit příkazový řádek vývojáře, který je předem nakonfigurován pro konkrétního hostitele a architektura cíl, otevřete **spustit** nabídky (ikona Windows v horním rohu plochy) a pak přejděte do složky pro vaši verzi sady Visual Studio , jako například **Visual Studio 2017**. Otevřete složku a zvolte zástupce příkazového řádku pro upřednostňované hostitele a cílové architektury.
  
Pokud chcete využít výhod výkonnější funkce, jako je ladicího programu sady Visual Studio, hledání a příkaz doplňování kódu technologie IntelliSense, vizuálních návrhářích projektu správy a tak dále, budete muset použít Visual Studio IDE.  
  
## <a name="debugging-your-code"></a>Ladění kódu  

Pokud používáte příkazového řádku a spuštění aplikace na stanici vývoje, zobrazí se dialogové okno pro spuštění [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] ladicí program se zobrazí v případě, že váš kód zjistí narušení přístupu paměti, neošetřené výjimky nebo jiné neopravitelné došlo k chybám. Pokud kliknete na tlačítko **OK**, pak je spuštěno vývojové prostředí sady Visual Studio a ladicí program se otevře s bodem selhání. Je možné k ladění aplikací tímto způsobem, a v takovém případě vašeho zdrojového kódu by být k dispozici pouze pokud kompilovat s [/Z7, / zi, /ZI (formát informace ladění)](../build/reference/z7-zi-zi-debug-information-format.md) přepínače. Další informace najdete v tématu [ladění nativního kódu](/visualstudio/debugger/debugging-native-code) a [pomocí prostředí Visual Studio IDE pro vývoje v jazyce C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## <a name="using-the-development-environment"></a>Použití vývojového prostředí  

Je jednodušší použít vývojového prostředí pro úpravy a vytváření vašeho zdrojového kódu v *projektu*. Projekt je kolekce zdroje a související soubory, které se zkompiluje do jedné jednotky, například knihovny nebo spustitelný soubor. Projekt obsahuje také informace o tom, jak jsou soubory má být sestaven. Informace o projekty jsou uloženy v projektu soubor s příponou .prj.  
  
Aplikace, která se skládá z více knihoven a spustitelné soubory, každý potenciálně vytvořené s jinou sadu možností kompilátoru nebo dokonce v jiném jazyce, jsou uloženy ve více projektech, které jsou součástí jednoho *řešení*. Řešení je abstrakci pro kontejner k seskupení více projektů. Informace o řešení jsou uloženy v souboru s příponou .sln řešení. Další informace najdete v tématu [řešení a projektů v sadě Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) a [pomocí prostředí Visual Studio IDE pro vývoje v jazyce C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## <a name="importing-your-existing-code"></a>Import existujícího kódu 
 
Kompilátor C++ můžete použít k vytvoření stávající kód, který je nastavený pro kompilaci s nebo bez souboru pravidel a umístí jej do [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] projektu. Další informace najdete v tématu [postupy: vytvoření projektu jazyka C++ z existujícího kódu](../ide/how-to-create-a-cpp-project-from-existing-code.md).  
  
## <a name="creating-a-new-project"></a>Vytvoření nového projektu  

Můžete vytvořit nové projekty ve vývojovém prostředí. Visual Studio poskytuje mnoho šablon, které poskytují standardní kód pro mnoho běžných projektů. Průvodci aplikací můžete použít ke generování projekty s osnovou kódu pro různé typy aplikací.  
  
Můžete začít s prázdným projektem pomocí **konzolové aplikace (Win32) průvodce**. Vyberte **prázdný projekt** zaškrtávací políčko. Můžete pak přidat nové nebo stávající soubory do projektu později.  
  
Když vytvoříte projekt, musí název projektu. Ve výchozím nastavení název projektu stejný název dynamická knihovna (DLL) nebo spustitelný soubor, který je sestaven z projektu. Další informace najdete v tématu [vytváření řešení a projekty](/visualstudio/ide/creating-solutions-and-projects).  
  
## <a name="microsoft-specific-modifiers"></a>Modifikátory specifické pro společnost Microsoft  

Microsoft Visual C++ compiler implementuje několik rozšíření pro standardní programovací jazyk C++ pro podporu programování pro operační systémy Windows. Tato rozšíření se používají k určení atributy třídy úložiště, zásad volání funkce a základní adresování kromě jiných věcí. Úplný seznam všech podporovaných rozšíření C++, najdete v části [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
Můžete zakázat všechna rozšíření specifické pro společnost Microsoft c++ pomocí **/Za** – možnost kompilátoru. Tato možnost se doporučuje, pokud chcete napsat kód pro spuštění ve více platformách. Další informace o **/Za** – možnost kompilátoru, najdete v části [/Za, /Ze (zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md). Další informace o přizpůsobení kompilátoru C++ najdete v tématu [přizpůsobení jazyka Visual C++](../visual-cpp-language-conformance.md) a [nestandardní chování](../cpp/nonstandard-behavior.md).  
  
## <a name="precompiled-headers"></a>Předkompilované hlavičky  

Kompilátory jazyka Microsoft C a C++ nabízí možnosti pro předkompilaci kódu žádné jazyka C nebo C++, včetně vloženého kódu. Pomocí této funkce výkonu můžete kompilovat stabilní tělo kódu, ukládat zkompilovaný kód v souboru a, během následných kompilací seskupovat předkompilovaný kód s kódem, který je pořád ve vývoji. Každá následná kompilace je rychlejší, protože není potřeba zopakovat kód stabilní.  
  
Ve výchozím nastavení, všechny předkompilovaný kód specifikován v souborech **stdafx.h** a **stdafx.cpp**. **Nový projekt** průvodce automaticky vytvoří tyto soubory můžete Pokud zrušíte výběr **předkompilované hlavičky** možnost. Další informace o předkompilovaných hlaviček v tématu [vytváření předkompilovaných hlavičkových souborů](../build/reference/creating-precompiled-header-files.md).  
  
## <a name="related-sections"></a>Související oddíly  

Další informace najdete v tématu [Portování ze systému UNIX do Win32](../porting/porting-from-unix-to-win32.md).  
  
## <a name="see-also"></a>Viz také  

[Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)