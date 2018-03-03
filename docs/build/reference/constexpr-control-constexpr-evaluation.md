---
title: "-constexpr (zkušební constexpr ovládací prvek) | Microsoft Docs"
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /constexpr
- -constexpr
dev_langs:
- C++
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e594eb697c8972d28b513a3638d3eb704258b5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (zkušební constexpr řízení)  
  
Použití **/constexpr** – možnosti kompilátoru řízení parametry pro `constexpr` vyhodnocení v době kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
> /constexpr:Depth*N*  
> /constexpr:backtrace*N*  
> /constexpr:steps*N*  
  
## <a name="arguments"></a>Arguments  
  
**Hloubka***N*  
Omezení hloubky rekurzivní `constexpr` fungovat na vyvolání *N* úrovně. Výchozí hodnota je 512.  
  
**backtrace***N*  
Zobrazit až *N* `constexpr` hodnocení v diagnostice. Výchozí hodnota je 10.  
  
**kroky***N*  
Ukončit `constexpr` zkušební verzi po *N* kroky. Výchozí hodnota je 100 000.  
  
## <a name="remarks"></a>Poznámky  
  
**/Constexpr** – možnosti kompilátoru řízení kompilaci vyhodnocení `constexpr` výrazy. Postup vyhodnocení, rekurze úrovně a backtrace hloubka jsou ovládaná zabránit kompilátor výdaje příliš mnoho času na `constexpr` vyhodnocení. Další informace o `constexpr` prvek jazyka najdete v části [constexpr (C++)](../../cpp/constexpr-cpp.md).  

**/Constexpr** možnosti jsou dostupné od ve Visual Studiu 2015.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete váš projekt **stránky vlastností** dialogové okno.   
  
2. V části **vlastnosti konfigurace**, rozbalte **C/C++** složky a vyberte **příkazového řádku** stránku vlastností.  
  
3. Zadejte všechny **/constexpr** kompilátoru možnosti v **další možnosti** pole. Zvolte **OK** nebo **použít** uložte provedené změny.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
  
[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)