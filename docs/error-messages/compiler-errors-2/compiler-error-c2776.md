---
title: "C2776 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2776
dev_langs: C++
helpviewer_keywords: C2776
ms.assetid: 9d80addc-62c7-40fc-a2cc-60303abb87df
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5642335519263c3b191d1c14399f3d00f366a8c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2776"></a>C2776 chyby kompilátoru
jeden vlastnost lze zadat pouze jednu metodu "get"  
  
 Můžete určit pouze jeden `get` v fungovat [vlastnost](../../cpp/property-cpp.md) rozšířených atributů. Tato chyba nastane, když více `get` funkce nejsou zadány.  
  
 Následující ukázka generuje C2776:  
  
```  
// C2776.cpp  
struct A {  
   __declspec(property(get=GetProp,get=GetPropToo))  
   // try the following line instead  
   // __declspec(property(get=GetProp))  
      int prop;   // C2776  
   int GetProp(void);  
   int GetPropToo(void);  
};  
```