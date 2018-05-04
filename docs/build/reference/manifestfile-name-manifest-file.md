---
title: -MANIFESTFILE (název souboru manifestu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ManifestFile
dev_langs:
- C++
helpviewer_keywords:
- MANIFESTFILE linker option
- -MANIFESTFILE linker option
- /MANIFESTFILE linker option
ms.assetid: befa5ab2-a9cf-4c9b-969a-e7b4a930f08d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b95337afc790436187c547bba108da2161b0738b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="manifestfile-name-manifest-file"></a>/MANIFESTFILE (název souboru manifestu)
```  
/MANIFESTFILE:filename  
```  
  
## <a name="remarks"></a>Poznámky  
 / MANIFESTFILE umožňuje změnit výchozí název souboru manifestu.  Výchozí název souboru manifestu je název souboru manifest připojí.  
  
 / MANIFESTFILE nebude mít žádný vliv, pokud je také nepropojovat s [/MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **souboru Manifest** stránku vlastností.  
  
5.  Změnit **souboru Manifest** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ManifestFile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)