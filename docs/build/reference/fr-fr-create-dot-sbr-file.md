---
title: -FR, -Fr (vytvořit. Soubor SBR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
dev_langs:
- C++
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6f61a3360c820a2d47d54f7c174af484079d154
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr (Vytvořit soubor .Sbr)
Vytvoří soubory .sbr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/FR[pathname[\filename]]  
/Fr[pathname[\filename]]  
```  
  
## <a name="remarks"></a>Poznámky  
 Během procesu sestavení Microsoft vyhledejte informace o souboru údržby nástroj (BSCMAKE) používá k vytvoření těchto souborů. BSC souboru, který se používá k zobrazení informací procházení.  
  
 **/FR** vytvoří soubor .sbr s úplné symbolické informace.  
  
 **/FR** vytvoří soubor .sbr bez informací o na lokální proměnné.  
  
 Pokud nezadáte `filename`, soubor .sbr získá základní stejný název jako zdrojový soubor.  
  
 **/FR** je zastaralý, pomocí **/FR** místo. Další informace najdete v tématu zastaralé a odebrat – možnosti kompilátoru v [kompilátoru možnosti uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
> [!NOTE]
>  Neměňte .sbr rozšíření. BSCMAKE vyžaduje zprostředkující soubory tak, aby měl rozšíření.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  V navigačním podokně, vyberte **C/C++**, **informacemi o procházení** stránku vlastností.  
  
3.  Změnit **procházet soubor s informacemi o** nebo **povolit informacemi o procházení** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Určení názvu cesty](../../build/reference/specifying-the-pathname.md)