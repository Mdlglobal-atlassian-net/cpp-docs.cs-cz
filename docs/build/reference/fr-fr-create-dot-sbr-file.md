---
title: /FR, /Fr (Vytvořit soubor .Sbr)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
ms.openlocfilehash: 58f55811f5d2bb81bc77da38a87c35bae91ce6cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320522"
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr (Vytvořit soubor .Sbr)

Vytvoří soubory .sbr.

## <a name="syntax"></a>Syntaxe

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Přestože BSCMAKE je stále nainstalován s Visual Studio, je již používán ide. Od aplikace Visual Studio 2008 jsou informace o procházení a symbolech automaticky uloženy v souboru SQL Server .sdf ve složce řešení.

Během procesu sestavení nástroj BSCMAKE (Microsoft Browse Information File Maintenance Utility) používá tyto soubory k vytvoření . BSC soubor, který se používá k zobrazení informací o procházení.

**/FR** vytvoří soubor .sbr s úplnými symbolickými informacemi.

**/Fr** vytvoří soubor .sbr bez informací o místních proměnných.

Pokud nezadáte `filename`, soubor .sbr získá stejný základní název jako zdrojový soubor.

**/Fr** je zastaralé; místo toho použijte **/FR.** Další informace naleznete v tématu Zastaralé a odebrané možnosti kompilátoru v [možnostech kompilátoru uvedených podle kategorie](compiler-options-listed-by-category.md).

> [!NOTE]
> Neměňte rozšíření .sbr. BSCMAKE vyžaduje, aby zprostředkující soubory měly tuto příponu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. V navigačním podokně zvolte stránku vlastností **C/C++**, **Procházet informace.**

1. Upravte vlastnost **Procházet informační soubor** nebo **Povolit informace o procházení.**

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>a .

## <a name="see-also"></a>Viz také

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Určení názvu cesty](specifying-the-pathname.md)
