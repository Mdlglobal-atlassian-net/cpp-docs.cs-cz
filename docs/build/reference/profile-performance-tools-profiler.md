---
title: -PROFILE (Profiler nástrojů výkonu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Profile
dev_langs:
- C++
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15379914b4c4852e3065d1abc03c2ce1b17fb044
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (profiler nástrojů výkonu)
Vytvoří výstupního souboru, který lze použít s profileru nástroje pro sledování výkonu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/PROFILE  
```  
  
## <a name="remarks"></a>Poznámky  
 / PROFILE znamená následující možnosti linkeru:  
  
-   [/ OPT: REF](../../build/reference/opt-optimizations.md)  
  
-   / OPT: NOICF  
  
-   [/ INCREMENTAL: NE](../../build/reference/incremental-link-incrementally.md)  
  
-   [/ FIXED: NE](../../build/reference/fixed-fixed-base-address.md)  
  
 / PROFILE způsobí, že linkeru pro generování oddíl přemístění do bitové kopie programu.  Oddíl přemístění umožňuje profileru k transformaci obrázek program, který má získat data profilu.  
  
 **/ PROFILU** je k dispozici pouze ve verzi Enterprise (vývoj v týmu).  Další informace o nástroj PREfast najdete v tématu [analýzy kódu pro C/C++ – přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **Upřesnit** stránku vlastností.  
  
5.  Změnit **profil** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)