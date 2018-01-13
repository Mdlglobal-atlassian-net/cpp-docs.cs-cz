---
title: "-FU (vynuceným názvem #using souboru) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
dev_langs: C++
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17b62859aaf0c9dc6b3313fbb726602b5b83a82c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fu-name-forced-using-file"></a>/FU (soubor s vynuceným názvem #using)
Možnost kompilátoru, která můžete použít jako alternativu k předání názvu souboru pro [#using – direktiva](../../preprocessor/hash-using-directive-cpp.md) ve zdrojovém kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/FU file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Určuje soubor metadat, chcete-li v této kompilaci.  
  
## <a name="remarks"></a>Poznámky  
 Přepínač /FU má jenom jeden název souboru. Chcete-li zadat více souborů, použijte /FU s každé z nich.  
  
 Pokud používáte [!INCLUDE[cppcli](../../build/reference/includes/cppcli_md.md)] a odkazují na metadata používat [přátelských sestavení](../../dotnet/friend-assemblies-cpp.md) funkce, nemůžete použít **/FU**. Metadata v kódu musí odkazovat pomocí `#using`– společně s `[as friend]` atribut. Přátelská sestavení nejsou podporovány v [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]).  
  
 Informace o tom, jak vytvořit sestavení nebo modul common language runtime (CLR) najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md). Informace o tom, jak sestavit [!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)], najdete v části [vytváření aplikací a knihovny](../../cppcx/building-apps-and-libraries-c-cx.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **Upřesnit** stránku vlastností.  
  
4.  Změnit **Force #using** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)