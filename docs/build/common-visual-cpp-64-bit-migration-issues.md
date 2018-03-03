---
title: "Běžné problémy s migrací 64-bit Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- upgrading Visual C++ applications, 32-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b9ea3690e04106f0836d236eefee4acd9dda3a82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Obecné problémy migrace v 64bitovém prostředí Visual C++

Použijete-li vytvářet aplikace na spouštění v operačním systému Windows 64-bit Visual C++, měli byste mít uvědomit následující skutečnosti:  
  
-   `int` a `long` jsou 32bitové hodnoty v operačních systémech Windows 64-bit. Pro programy, které máte v úmyslu zkompilovat pro 64bitové platformy byste měli být pozor, abyste jim ukazatele na 32-bit proměnné. Ukazatele jsou 64bitové na 64bitových platformách a zkrátit hodnotu ukazatele, chcete-li přiřadit ho k proměnné 32-bit.  
  
-   `size_t`, `time_t`, a `ptrdiff_t` jsou 64bitové hodnoty v operačních systémech Windows 64-bit.  
  
-   `time_t`je hodnota 32-bit v operačních systémech Windows 32-bit v jazyce Visual C++ verze před Visual C++ 2005. `time_t`je nyní 64bitovou celočíselnou hodnotu ve výchozím nastavení. Další informace najdete v tématu [Správa času](../c-runtime-library/time-management.md).  
  
     Byste měli vědět, kde váš kód přebírá `int` hodnotu a zpracovává je jako `size_t` nebo `time_t` hodnotu. Je možné, že číslo může být větší než 32bitové číslo a data budou zkráceny, když je předán zpět do `int` úložiště.  
  
%X (šestnáctkových `int` formátu) `printf` modifikátor nebude fungovat podle očekávání 64bitová verze operačního systému Windows. Toto pravidlo bude pracovat pouze na první 32 bity hodnoty, který je předán.  
  
-   Použijte % I32x, chcete-li zobrazit typu 32bitové celočíselné v šestnáctkovém formátu.  
  
-   % I64x použijte k zobrazení typu 64bitové celočíselné v šestnáctkovém formátu.  
  
-   %P (šestnáctkový formát pro ukazatel) bude fungovat podle očekávání 64bitová verze operačního systému Windows.  
  
Další informace naleznete v tématu:  
  
-   [Možnosti kompilátoru](../build/reference/compiler-options.md)  
  
-   [Tipy pro migraci](http://msdn.microsoft.com/library/windows/desktop/aa384214)  
  
## <a name="see-also"></a>Viz také  

[Konfigurace Visual C++ pro 64bitové, x64 cíle](../build/configuring-programs-for-64-bit-visual-cpp.md)   
[Průvodce přenosem a upgradem Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)