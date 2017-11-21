---
title: -HEAP (nastavit velikost haldy) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
dev_langs: C++
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 702b8dfa6561d79f8ea9bf496e9652f89c8d34f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="heap-set-heap-size"></a>/HEAP (Nastavit velikost haldy)
```  
/HEAP:reserve[,commit]  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost /HEAP nastaví velikost haldy v bajtech. Tato možnost je jenom pro použití při vytváření souboru s příponou .exe.  
  
 *Rezervovat* argument určuje přidělení celkový haldy ve virtuální paměti. Výchozí velikost haldy je 1 MB. Linkeru zaokrouhlí na nejbližší 4 bajtů zadanou hodnotu.  
  
 Volitelné `commit` argument podléhá interpretace v operačním systému. V systému Windows NT, Windows 2000 určuje množství fyzické paměti k přidělení najednou. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. A vyšší `commit` hodnota šetří čas, kdy aplikace vyžaduje více místa na haldy, ale zvyšuje požadavky na paměť a případně čas spuštění.  
  
 Zadejte *rezervovat* a `commit` hodnoty v desítkový nebo jazyka C zápis.  
  
 Tato funkce je také dostupná prostřednictvím soubor definice modulu s [velikost HALDY](../../build/reference/heapsize.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **systému** stránku vlastností.  
  
4.  Změnit **potvrdit velikost haldy** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)