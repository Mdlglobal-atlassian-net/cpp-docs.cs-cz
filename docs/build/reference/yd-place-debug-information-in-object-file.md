---
title: -Yd (umístit informace o ladění do souboru objektu) | Microsoft Docs
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
ms.openlocfilehash: 39b03b0faf975caba8c5a287c88afcdf53f7a71f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378230"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd (Umístit informace o ladění do souboru objektu)
Mezerami dokončení ladicí informace ve všech souborů objektu vytvořeny ze souboru předkompilovaných hlaviček (.pch) při použití s [/Yc](../../build/reference/yc-create-precompiled-header-file.md) a [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) možnosti. Zastaralé  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Yd  
```  
  
## <a name="remarks"></a>Poznámky  
 **/Yd** je zastaralý; [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] nyní podporuje použití více objektů zápisu do souboru PDB jeden **/Zi** místo. Seznam – možnosti kompilátoru zastaralé, najdete v části **zastaralé a odebrat – možnosti kompilátoru** v [kompilátoru možnosti uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
 Pokud je nutné distribuovat knihovny obsahující informace o ladění, používat [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost místo **/Z7** a **/Yd**.  
  
 Ukládání informací o dokončení ladění do každého souboru .obj je nezbytné pouze k distribuci knihovny, které obsahují informace o ladění. Ho zpomalí kompilace a vyžaduje značné místo na disku. Když **/Yc** a **/Z7** použijí bez **/Yd**, kompilátor ukládá běžných informací o ladění do první souboru .obj vytvořen ze souboru .pch. Kompilátor nevkládá tyto informace do soubory .obj následně vytvořené ze souboru .pch; Vloží křížové odkazy na informace. Bez ohledu na to, kolik soubory .obj použít soubor .pch obsahuje pouze jeden soubor .obj běžných informací o ladění.  
  
 I když toto výchozí chování za následek rychlejší sestavení časy a snižuje nároky na místo na disku, není žádoucí, pokud vyžaduje malou změnu znovu sestavit .obj souboru, který obsahuje informace o běžných ladění. V takovém případě kompilátor nutné znovu vytvořit všechny soubory .obj obsahující křížové odkazy na původní soubor .obj. Navíc pokud běžné souboru .pch používají různé projekty, spoléhat na křížové odkazy na soubor jednoho .obj je obtížné.  
  
 Další informace o předkompilovaných hlaviček najdete v tématu:  
  
-   [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md)  
  
-   [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="examples"></a>Příklady  
 Předpokládejme, že máte dva základní soubory, F.cpp a G.cpp, každý obsahující tyto **#include** příkazy:  
  
```  
#include "windows.h"  
#include "etc.h"  
```  
  
 Následující příkaz vytvoří předkompilovaný hlavičkový soubor ETC.pch a soubor objektu F.obj:  
  
```  
CL /YcETC.H /Z7 F.CPP  
```  
  
 Soubor objektu F.obj zahrnuje typ a informací o symbolu odkazující na Windows a ETC.h (a další hlavičkové soubory, které obsahují). Teď můžete použít předkompilovaný hlavičkový ETC.pch ke kompilaci zdrojového souboru G.cpp:  
  
```  
CL /YuETC.H /Z7 G.CPP  
```  
  
 Soubor objektu G.obj nezahrnuje informace o ladění pro předkompilované hlavičky ale jednoduše odkazuje na tyto informace v souboru F.obj. Všimněte si, že je nutné propojit s F.obj souboru.  
  
 Pokud nebyl předkompilovaných hlaviček kompilovat s **/Z7**, když můžete nadále používat v novější kompilace pomocí **/Z7**. Ale informace o ladění je umístěn v aktuální objekt souboru, a lokální symboly pro typy definované v předkompilovaných hlaviček a funkce nejsou k dispozici pro ladicí program.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)