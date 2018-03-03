---
title: "-STACK (přidělení zásobníku) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.StackReserveSize
- VC.Project.VCLinkerTool.StackCommitSize
- /stack
dev_langs:
- C++
helpviewer_keywords:
- STACK linker option
- -STACK linker option
- memory allocation, stack
- /STACK linker option
- stack, setting size
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6b487ff830abd3dfa97a748c81d541cbd9fdd0b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="stack-stack-allocations"></a>/STACK (přidělení zásobníku)
```  
/STACK:reserve[,commit]  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost /STACK nastaví velikost zásobníku v bajtech. Tuto možnost použijte pouze v případě, že sestavujete soubor .exe.  
  
 Hodnota `reserve` určuje celkové přidělení zásobníku ve virtuální paměti. Na počítačích s architekturou ARM, x86 a [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] je výchozí velikost zásobníku 1 MB.  
  
 Parametr `commit` podléhá interpretaci operačního systému. V systémech Windows RT určuje množství fyzické paměti, kterou lze v jednom okamžiku přidělit. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. Vyšší hodnota `commit` šetří čas, potřebuje-li aplikace více místa v zásobníku, ale zvyšuje požadavky na paměť a případně i čas spuštění. Na počítačích s architekturou ARM, x86 a [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] je výchozí potvrzená hodnota 4 kB.  
  
 Hodnoty `reserve` a `commit` zadávejte v desítkovém zápisu nebo v zápisu jazyka C.  
  
 Jiný způsob, jak nastavit velikost zásobníku je s [STACKSIZE](../../build/reference/stacksize.md) příkaz v souboru definice modulu (.def). **Velikost zásobníku** přepsání přidělení zásobníku (/ zásobníku) možnost, pokud jsou zadány oba. Velikost zásobníku můžete změnit po soubor .exe je sestavena pomocí [nástroje EDITBIN](../../build/reference/editbin-reference.md) nástroj.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **Linkeru** složky.  
  
3.  Vyberte **systému** stránku vlastností.  
  
4.  Upravte jednu z následujících vlastností:  
  
    -   **Potvrzená velikost zásobníku**  
  
    -   **Velikost rezervy zásobníku**  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)