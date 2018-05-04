---
title: -DEF (zadat soubor definice modulu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
dev_langs:
- C++
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0c712b81fbb755edd132c6f97efc906ba4f5ff9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="def-specify-module-definition-file"></a>/DEF (Zadat soubor definice modulu)
```  
/DEF:filename  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Název souboru*  
 Název souboru definice modulu (.def) mají být předány linkeru.  
  
## <a name="remarks"></a>Poznámky  
 Možnost/DEF předá soubor definice modulu (.def) linkeru. ODKAZ na lze zadat pouze jeden soubor .def. Podrobnosti o soubory .def najdete v tématu [soubory definice modulu](../../build/reference/module-definition-dot-def-files.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **vstup** stránku vlastností.  
  
4.  Změnit **soubor definice modulu** vlastnost.  
  
 K určení souboru .def v rámci vývojového prostředí, doporučujeme ho přidat do projektu spolu s další soubory a zadejte soubor možnosti/def.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)