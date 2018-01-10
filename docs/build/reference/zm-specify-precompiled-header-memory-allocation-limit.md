---
title: "-Zm (zadat omezení přidělení paměti pro předkompilované hlavičky) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /zm
dev_langs: C++
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a45425215fcaf336c0b1630634d0adf37ba3984
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm (Zadat omezení přidělení paměti pro předkompilované hlavičky)
Určuje množství paměti, které kompilátor přiděluje k vytvoření předkompilovaných hlaviček.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Zmfactor  
```  
  
## <a name="arguments"></a>Arguments  
 `factor`  
 Škálovací faktor určující množství paměti, které kompilátor používá k vytvoření předkompilovaných hlaviček.  
  
 `factor` Argument je procento výchozí velikost vyrovnávací paměti definované kompilátoru práci. Výchozí hodnota `factor` je 100 (procent), ale můžete zadat větší nebo menší množství.  
  
## <a name="remarks"></a>Poznámky  
 Ve starších verzích jazyka Visual C++ používal kompilátor několik samostatných hald, přičemž každá měla konečný limit. V současné době kompilátor haldu dynamicky zvětšuje podle potřeby až do celkového limitu velikosti a vyrovnávací paměť fixní velikosti vyžaduje pouze k vytvoření předkompilovaných hlaviček. V důsledku toho **/Zm** – možnost kompilátoru obvykle není nutný.  
  
 Pokud kompilátor dojde místo haldy a vysílá [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) chybová zpráva při použití **/Zm** – možnost kompilátoru, obsahují rezervované příliš mnoho paměti. Zvažte odebrání **/Zm** možnost. Pokud kompilátor vydává [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) chybová zpráva, doplňujícími [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) určuje zpráva `factor` argument použijte, pokud je překompilovat pomocí **/Zm** – možnost kompilátoru.  
  
 Následující tabulka ilustruje jak `factor` argument ovlivňuje omezení přidělení paměti, pokud budete předpokládat, že je velikost vyrovnávací paměti pro předkompilované hlavičky výchozí 75 MB.  
  
|Hodnota`factor`|Limit přidělení paměti|  
|-----------------------|-----------------------------|  
|10|7.5 MB|  
|100|75 MB|  
|200|150 MB|  
|1000|750 MB|  
|2000|1 500 MB|  
  
## <a name="other-ways-to-set-the-memory-allocation-limit"></a>Jiné způsoby nastavení limitu přidělení paměti  
  
#### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení parametru kompilátoru /Zm ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  V navigačním podokně vyberte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku**.  
  
3.  Zadejte **/Zm** – možnost kompilátoru v **další možnosti** pole.  
  
#### <a name="to-set-the-zm-compiler-option-programmatically"></a>Programové nastavení parametru kompilátoru /Zm  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)