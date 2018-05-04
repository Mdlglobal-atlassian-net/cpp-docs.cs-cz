---
title: -IMPLIB (knihovna importu názvů) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72edc0fcb1b216319d6f6c9924cb92a165b3196b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="implib-name-import-library"></a>/IMPLIB (knihovna importu názvů)
  
> / IMPLIB:*filename*  
  
## <a name="parameters"></a>Parametry  
  
*Název souboru*  
Název knihovny importu zadaného uživatelem. Nahradí výchozí název.  
  
## <a name="remarks"></a>Poznámky  
  
Možnost /IMPLIB přepíše výchozí název pro import knihovnu, která vytvoří odkaz k sestavení program, který obsahuje export. Výchozí název je vytvořen z základní název hlavní výstupní soubor a rozšíření. lib. Program obsahuje exportuje, pokud jsou zadané jeden nebo více následujících akcí:  
  
-   [__Declspec(dllexport)](../../cpp/dllexport-dllimport.md) – klíčové slovo ve zdrojovém kódu  
  
-   [EXPORTUJE](../../build/reference/exports.md) – příkaz souboru .def  
  
-   [/EXPORT](../../build/reference/export-exports-a-function.md) specifikace v příkazu odkaz  
  
 ODKAZ ignoruje /IMPLIB, když není vytváří knihovnu importu. Pokud nejsou zadány žádné export, nevytvoří odkaz knihovnu importu. Pokud soubor exportu se používá v sestavení, odkaz se předpokládá, že knihovnu importu již existuje a není vytvořit. Informace o importovanými knihovnami a exportovanými soubory, najdete v části [LIB odkaz](../../build/reference/lib-reference.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **knihovny importu** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)