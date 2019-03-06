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
ms.openlocfilehash: 41b415889465441b0c53f12ec7f4aa412a636562
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418080"
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr (Vytvořit soubor .Sbr)

Vytvoří soubory .sbr.

## <a name="syntax"></a>Syntaxe

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>Poznámky

Během procesu sestavení, nástroje Microsoft procházet informace souboru údržby Utility (BSCMAKE) používá k vytvoření těchto souborů. Soubor BSC, který se používá k zobrazení informací o procházení.

**/FR** vytvoří soubor .sbr s úplné symbolické informace.

**/FR** vytvoří soubor .sbr bez informací o lokálních proměnných.

Pokud nezadáte `filename`, soubor .sbr získá stejný základní název zdrojového souboru.

**/FR** je zastaralá; použijte **/FR** místo. Další informace najdete v tématu zastaralé a odebrat možnosti kompilátoru v [možnosti kompilátoru seřazené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).

> [!NOTE]
>  Neměňte .sbr rozšíření. BscMake – vyžaduje zprostředkující soubory, které chcete mít tuto příponu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. V navigačním podokně, vyberte **C/C++**, **informace o procházení** stránku vlastností.

1. Upravit **soubor s informacemi o procházení** nebo **povolit informace o procházení** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti výstupního souboru (/F)](../../build/reference/output-file-f-options.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Určení názvu cesty](../../build/reference/specifying-the-pathname.md)
