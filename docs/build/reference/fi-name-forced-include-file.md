---
title: /FI (Zahrnutý soubor s povinným názvem)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ForcedIncludes
- VC.Project.VCCLCompilerTool.ForcedIncludeFiles
- VC.Project.VCCLWCECompilerTool.ForcedIncludeFiles
helpviewer_keywords:
- FI compiler option [C++]
- -FI compiler option [C++]
- /FI compiler option [C++]
- preprocess header file compiler option [C++]
ms.assetid: 07e79577-8152-4df9-a64c-aae08c603397
ms.openlocfilehash: 6460f75e2cad81bc1dcc540e3c687de5d0dc0d32
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439798"
---
# <a name="fi-name-forced-include-file"></a>/FI (Zahrnutý soubor s povinným názvem)

Způsobí, že preprocesor zpracuje zadaný hlavičkový soubor.

## <a name="syntax"></a>Syntaxe

```
/FI[ ]pathname
```

## <a name="remarks"></a>Poznámky

Tato možnost má stejný účinek jako zadání souboru s dvojitými uvozovkami v direktivě `#include` na prvním řádku každého zdrojového souboru zadaného v příkazovém řádku, v proměnné prostředí CL nebo v souboru příkazů. Pokud použijete více možností **/Fi** , soubory jsou zahrnuty v pořadí, ve kterém jsou zpracovávány pomocí CL.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **CC++ /a** .

1. Klikněte na stránku **Upřesnit** vlastnosti.

1. Upravte vlastnost **vynucený soubor k zahrnutí** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedIncludeFiles%2A>.

## <a name="see-also"></a>Viz také

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Určení názvu cesty](specifying-the-pathname.md)
