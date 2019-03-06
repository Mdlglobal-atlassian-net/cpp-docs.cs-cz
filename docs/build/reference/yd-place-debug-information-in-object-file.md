---
title: /Yd (Umístit informace o ladění do souboru objektu)
ms.date: 11/04/2016
f1_keywords:
- /yd
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
ms.openlocfilehash: 55bb8197cd15243f65c90d7fbd2724f91fce23b4
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414873"
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

- [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md)

- [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

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

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
