---
title: "C3873 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3873
helpviewer_keywords: C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b2e95250fd2bf789425585b704f50bd4d1c51b2c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3873"></a>C3873 chyby kompilátoru
"char": Tento znak není povolen jako první znak identifikátoru  
  
 Kompilátor C++ odpovídá C ++ 11 standard na povolených znaků v identifikátor. V identifikátoru jsou povoleny pouze určitý rozsah znaků a univerzální názvy znaků. Další omezení se použijí na počáteční znak identifikátoru. Další informace a seznam povolených a rozsahy název universal znaků najdete v tématu [identifikátory](../../cpp/identifiers-cpp.md).  
  
 Rozsah znaků povolených v identifikátoru je méně omezující při kompilování C + +/ CLI kódu. Postupujte podle identifikátory v kódu zkompilovat pomocí/CLR [standardní standardy ECMA-335: společné jazykové infrastruktury (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Následující ukázka generuje C3873:  
  
```  
// C3873.cpp  
int main() {  
   int \u036F_abc;   // C3873, not in allowed range for initial character  
   int abc_\u036F;   // OK, in allowed range for non-initial character  
}  
```