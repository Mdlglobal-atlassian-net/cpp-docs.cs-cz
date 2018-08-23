---
title: -Yd (umístění informací o ladění do souboru objektu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yd
dev_langs:
- C++
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86cb8a42b77cd0a932530455f1125125a9f546d9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42585964"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd (Umístit informace o ladění do souboru objektu)
Úplné ladicí informace do všech objektových souborů mezery vytvořené ze souboru předkompilované hlavičky (pch) při použití s [/Yc](../../build/reference/yc-create-precompiled-header-file.md) a [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) možnosti. Zastaralé  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Yd  
```  
  
## <a name="remarks"></a>Poznámky  
 **/Yd** je zastaralá; Jazyk Visual C++ teď podporuje více objektů zápisu do souboru PDB jeden, použijte **/zi** místo. Seznam zastaralých kompilátoru možnosti najdete v tématu **zastaralé a odebrat možnosti kompilátoru** v [možnosti kompilátoru seřazené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
 Pokud budete muset distribuovat knihovny obsahuje ladicí informace, použijte [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost spíše než **/Z7** a **/Yd**.  
  
 Ukládání kompletní informaci o ladění do každého souboru .obj je nezbytné pouze k distribuci knihoven, které obsahují informace o ladění. Zpomaluje kompilace a vyžaduje značné místo na disku. Když **/Yc** a **/Z7** použijí bez **/Yd**, kompilátor uloží v prvním souboru .obj vytvořeného ze souboru .pch běžných informací o ladění. Kompilátor nevkládá tyto informace do souborů obj následně vytvořené ze souboru .pch; Vloží křížové odkazy na informace. Bez ohledu na to, kolik souborů .obj používat soubor .pch obsahuje pouze jeden soubor .obj běžných informací o ladění.  
  
 I když toto výchozí chování výsledky v rychlejší doby sestavení a snižuje požadavky na místo na disku, nežádoucí, pokud vyžaduje malou změnu znovu sestavit soubor .obj obsahující běžných informací o ladění. V tomto případě kompilátor nutné znovu sestavit všechny soubory .obj, který obsahuje křížové odkazy na původní soubor .obj. Navíc pokud běžné souboru .pch používají různé projekty, závislost na křížové odkazy na soubor .obj jeden je obtížné.  
  
 Další informace o předkompilovaných hlaviček naleznete v tématu:  
  
-   [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md)  
  
-   [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte na tlačítko **C/C++** složky.  
  
3.  Klikněte na tlačítko **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do kompilátoru **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="examples"></a>Příklady  
 Předpokládejme, že máte dva základní soubory F.cpp a G.cpp každé prostředí bude obsahovat tyto **#include** příkazy:  
  
```  
#include "windows.h"  
#include "etc.h"  
```  
  
 Následující příkaz vytvoří předkompilované hlavičky souboru ETC.pch a soubor objektu F.obj:  
  
```  
CL /YcETC.H /Z7 F.CPP  
```  
  
 Soubor objektu F.obj obsahuje typ a informace o symbolech pro WINDOWS.h a ETC.h (a další hlavičkové soubory, které patří mezi ně). Teď můžete použít předkompilovanou hlavičku ETC.pch pro kompilaci zdrojového G.cpp:  
  
```  
CL /YuETC.H /Z7 G.CPP  
```  
  
 Soubor objektu G.obj jednoduše odkazuje tyto informace v souboru F.obj však neobsahuje ladicí informace pro předkompilované hlavičky. Všimněte si, že je třeba propojit s F.obj souboru.  
  
 Pokud předkompilované hlavičky se nezkompilovalo s **/Z7**, ji mohou dál používat v pozdější kompilace pomocí **/Z7**. Ale informace o ladění je umístěn v aktuálním objektu souboru a místní symboly pro funkce a typy definované v předkompilované hlavičce nejsou k dispozici v ladicím programu.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)