---
title: "-IMPLIB (knihovna importu názvů) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 523fc171aa8df3d0b4c6e09909db7c2c1dc0b833
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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