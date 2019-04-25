---
title: '/FU (soubor s vynuceným názvem #using)'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
ms.openlocfilehash: c47a45208ac5b5c7e0000516ed114c008feda7ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292286"
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

Pokud používáte C++/rozhraní příkazového řádku a vyhoví se jim odkazující na metadata k použití [přátelských sestavení](../../dotnet/friend-assemblies-cpp.md) funkce, nemůžete použít **/FU**. Metadata v kódu musí odkazovat pomocí `#using`– spolu s `[as friend]` atribut. Přátelská sestavení nejsou podporované ve Vizuálu C++ rozšíření komponent C++/CX.

Informace o tom, jak vytvořit sestavení nebo modul pro modul common language runtime (CLR), najdete v části [/CLR (kompilace Common Language Runtime)](clr-common-language-runtime-compilation.md). Informace o tom, jak vytvářet C++/CX, naleznete v tématu [sestavování aplikací a knihoven](../../cppcx/building-apps-and-libraries-c-cx.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **Upřesnit** stránku vlastností.

1. Upravit **platnost #using** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
