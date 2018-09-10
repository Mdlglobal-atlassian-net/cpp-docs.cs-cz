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
ms.openlocfilehash: acf4afebc7288a953a0f8785e1f18097c21d71e3
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107383"
---
# <a name="fu-name-forced-using-file"></a>/FU (soubor s vynuceným názvem #using)

Možnost kompilátoru, který slouží jako alternativu k předání názvu souboru pro [# direktiva using](../../preprocessor/hash-using-directive-cpp.md) ve zdrojovém kódu.

## <a name="syntax"></a>Syntaxe

> **/FU** *souboru*

## <a name="arguments"></a>Arguments

*Soubor*<br/>
Určuje soubor metadat má odkazovat v této kompilaci.

## <a name="remarks"></a>Poznámky

/FU přepínač má pouze jeden název souboru. Pokud chcete zadat více souborů, pomocí /FU každé z nich.

Pokud používáte C + +/ CLI a jsou odkazuje na metadata k použití [přátelských sestavení](../../dotnet/friend-assemblies-cpp.md) funkci nelze použít **/FU**. Metadata v kódu musí odkazovat pomocí `#using`– spolu s `[as friend]` atribut. Přátelská sestavení nejsou podporované v rozšíření součásti Visual C++ C + +/ CX.

Informace o tom, jak vytvořit sestavení nebo modul pro modul common language runtime (CLR), najdete v části [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md). Informace o tom, jak vytvořit v jazyce C + +/ CX, viz [sestavování aplikací a knihoven](../../cppcx/building-apps-and-libraries-c-cx.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **Upřesnit** stránku vlastností.

1. Upravit **platnost #using** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.

## <a name="see-also"></a>Viz také

[Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)