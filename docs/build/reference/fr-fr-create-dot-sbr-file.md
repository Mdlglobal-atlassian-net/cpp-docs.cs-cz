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
ms.openlocfilehash: a75a9d143012dee7946591d708921d6734b2acda
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811872"
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

**/FR** je zastaralá; použijte **/FR** místo. Další informace najdete v tématu zastaralé a odebrat možnosti kompilátoru v [možnosti kompilátoru seřazené podle kategorie](compiler-options-listed-by-category.md).

> [!NOTE]
>  Neměňte .sbr rozšíření. BscMake – vyžaduje zprostředkující soubory, které chcete mít tuto příponu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. V navigačním podokně, vyberte **C/C++**, **informace o procházení** stránku vlastností.

1. Upravit **soubor s informacemi o procházení** nebo **povolit informace o procházení** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Určení názvu cesty](specifying-the-pathname.md)
