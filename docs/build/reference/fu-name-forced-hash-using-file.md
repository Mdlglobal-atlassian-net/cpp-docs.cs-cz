---
title: '-FU (vynuceným názvem #using souboru) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
dev_langs:
- C++
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a92e8d30d2c15ac07bc5a6ff3e6438da46438674
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597498"
---
# <a name="fu-name-forced-using-file"></a>/FU (soubor s vynuceným názvem #using)
Možnost kompilátoru, který slouží jako alternativu k předání názvu souboru pro [# direktiva using](../../preprocessor/hash-using-directive-cpp.md) ve zdrojovém kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/FU file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Určuje soubor metadat má odkazovat v této kompilaci.  
  
## <a name="remarks"></a>Poznámky  
 /FU přepínač má pouze jeden název souboru. Pokud chcete zadat více souborů, pomocí /FU každé z nich.  
  
 Pokud používáte C + +/ CLI a jsou odkazuje na metadata k použití [přátelských sestavení](../../dotnet/friend-assemblies-cpp.md) funkci nelze použít **/FU**. Metadata v kódu musí odkazovat pomocí `#using`– spolu s `[as friend]` atribut. Přátelská sestavení nejsou podporované v rozšíření součásti Visual C++ C + +/ CX.  
  
 Informace o tom, jak vytvořit sestavení nebo modul pro modul common language runtime (CLR), najdete v části [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md). Informace o tom, jak vytvořit v jazyce C + +/ CX, viz [sestavování aplikací a knihoven](../../cppcx/building-apps-and-libraries-c-cx.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **Upřesnit** stránku vlastností.  
  
4.  Upravit **platnost #using** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)