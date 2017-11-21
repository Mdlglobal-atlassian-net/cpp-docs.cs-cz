---
title: "-Ge (Povolit sondy zásobníku) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /ge
dev_langs: C++
helpviewer_keywords:
- -Ge compiler option [C++]
- enable stack probes
- /Ge compiler option [C++]
- stack, stack probes
- stack probes
- stack checking calls
- Ge compiler option [C++]
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9c826b2f1d77e71d768ec73fb110f115bf7d0cfa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ge-enable-stack-probes"></a>/Ge (Povolit sondy zásobníku)
Aktivuje sondy zásobníku pro každé volání funkce, která vyžaduje úložiště pro místní proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Ge  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento mechanismus je užitečné, pokud přepisování funkce sondy zásobníku. Je doporučeno používat [/Gh (Povolit _penter – funkce háku)](../../build/reference/gh-enable-penter-hook-function.md) místo přepisování sondy zásobníku.  
  
 [/GS (řízení zásobníku kontrola volání)](../../build/reference/gs-control-stack-checking-calls.md) má stejný účinek.  
  
 **/Ge** je zastaralé; počínaje Visual Studio 2005, kompilátor automaticky generuje Kontrola zásobníku. Seznam – možnosti kompilátoru zastaralé, najdete v části **zastaralé a odebrat – možnosti kompilátoru** v [kompilátoru možnosti uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)