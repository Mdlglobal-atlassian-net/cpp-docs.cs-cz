---
title: "Kompilátoru (úroveň 4) upozornění C4459 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4459
dev_langs: C++
helpviewer_keywords: C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 11a4122bf58ac5645c4430f8c6a41de7ed19f430
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4459"></a>C4459 kompilátoru upozornění (úroveň 4)
  
> prohlášení o '*identifikátor*' skryje globální deklarace
  
Prohlášení o *identifikátor* v oboru místní skryje deklaraci stejně jako názvem *identifikátor* v globálním oboru. Toto upozornění informacemi o tom, který odkazuje na *identifikátor* v tomto rozsahu odkazující na lokálně deklarovaný verze, ne globální verzi, která mohou nebo nemusí být vašich představ. Obecně platí doporučujeme, abyste že minimalizujete použití globální proměnné dobrý technického hlediska. Chcete-li minimalizovat znečištění globálního oboru názvů, doporučujeme použít s názvem oboru názvů pro globální proměnné.  
  
Toto upozornění se nové v sadě Visual Studio 2015, v jazyce Visual C++ verze kompilátoru 18.00 hodin. Chcete-li potlačit upozornění z této verze kompilátoru nebo později během migrace kódu, použijte [/Wv:18](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru. 

## <a name="example"></a>Příklad
  
 Následující ukázka generuje C4459:  
  
```cpp  
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() { 
    int global_or_local; // warning C4459 
    global_or_local = 2;
} 
```  
  
Jedním ze způsobů řešení tohoto problému je vytvoření oboru názvů pro vaše globals, ale nechcete použít `using` – direktiva tím tento obor názvů, do oboru, proto musíte použít všechny odkazy jednoznačným kvalifikovaný názvy:  
  
```cpp  
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() { 
    int global_or_local; // OK 
    global_or_local = 2;
    globals::global_or_local = 3;
} 
```  
