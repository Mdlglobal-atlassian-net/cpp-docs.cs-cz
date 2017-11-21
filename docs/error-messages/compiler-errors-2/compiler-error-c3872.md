---
title: "C3872 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3872
dev_langs: C++
helpviewer_keywords: C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e42ebb3e1fc286e40662eb7fcce83893b1e4007f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3872"></a>C3872 chyby kompilátoru
"char": Tento znak není povolen v identifikátoru  
  
 Kompilátor C++ odpovídá C ++ 11 standard na povolených znaků v identifikátor. V identifikátoru jsou povoleny pouze určitý rozsah znaků a univerzální názvy znaků. Další omezení se použijí na počáteční znak identifikátoru. Další informace a seznam povolených a rozsahy název universal znaků najdete v tématu [identifikátory](../../cpp/identifiers-cpp.md).  
  
 Rozsah znaků povolených v identifikátoru je méně omezující při kompilování C + +/ CLI kódu. Postupujte podle identifikátory v kódu zkompilovat pomocí/CLR [standardní standardy ECMA-335: společné jazykové infrastruktury (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Následující ukázka generuje C3872:  
  
```  
// C3872.cpp  
int main() {  
   int abc_\u0040;   // C3872, U+0040 is in base char set  
   int abc_\u3001;   // C3872, U+3001 is not in allowed range  
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range  
}  
```