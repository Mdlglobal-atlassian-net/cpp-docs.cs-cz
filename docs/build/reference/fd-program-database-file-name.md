---
title: -Fd (název souboru databáze programu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07ab9f1d9c5c611b8da8b19860fe9e0c05351d75
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fd-program-database-file-name"></a>/Fd (Název souboru databáze programu)
Určuje název souboru pro soubor databáze (PDB) programu vytvořené [/Z7, / zi, /ZI (formát informace ladění)](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Fdpathname  
```  
  
## <a name="remarks"></a>Poznámky  
 Bez **/Fd**, výchozí název souboru PDB VC*x*0.pdb, kde *x* je hlavní verzi Visual C++ v použití.  
  
 Pokud zadáte název cesty, která neobsahuje název souboru (cesta končí v zpětné lomítko), kompilátor vytvoří soubor .pdb s názvem VC*x*pdb 0 v určeném adresáři.  
  
 Pokud zadáte název souboru, který nezahrnuje rozšíření, kompilátor použije PDB jako rozšíření.  
  
 Tato možnost také názvy soubor stavu (IDB) použitý pro minimální opětovné sestavení a přírůstkové kompilace.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **výstupní soubory** stránku vlastností.  
  
4.  Změnit **název souboru databáze programu** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>.  
  
## <a name="example"></a>Příklad  
 Tento příkaz vytvoří soubor .pdb s názvem PROG.pdb a IDB soubor s názvem PROG.idb:  
  
```  
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP  
```  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Určení názvu cesty](../../build/reference/specifying-the-pathname.md)