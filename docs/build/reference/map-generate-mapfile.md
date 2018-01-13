---
title: "-MAP (Generovat soubor mapování) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
dev_langs: C++
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f01daff11d41263766b66ed335c60d4bf83ced45
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="map-generate-mapfile"></a>/MAP (Generovat soubor mapování)
```  
/MAP[:filename]  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Název souboru*  
 Název souboru mapování zadaného uživatelem. Nahradí výchozí název.  
  
## <a name="remarks"></a>Poznámky  
 Možnost/map informuje linkeru pro vytvoření souboru mapování.  
  
 Ve výchozím nastavení názvy linkeru souboru mapování se základní název programu a .map rozšíření. Volitelné *filename* umožňuje potlačit výchozí název souboru mapování.  
  
 Souboru mapování je textový soubor, který obsahuje následující informace o propojovaném programu:  
  
-   Název modulu, což je základní název souboru  
  
-   Časové razítko z hlavičky souboru programu (nikoli z systém souborů)  
  
-   Seznam skupin v programu, s každou skupinu počáteční adresa (jako *části*:*posun*), délka, název skupiny a – třída  
  
-   Seznam veřejné symboly, z nichž každá (jako *části*:*posun*), symbolů název, plochý adresu a kde je definován symbol souboru .obj  
  
-   Vstupní bod (jako *části*:*posun*)  
  
 [/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md) možnost určuje další informace, které mají být zahrnuty do souboru mapování.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **ladění** stránku vlastností.  
  
4.  Změnit **generování souboru s mapováním** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)