---
title: C2040 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C2040
dev_langs:
- C++
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f102b1fea23c89debc86970d7548ba7da152cd37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2040"></a>C2040 chyby kompilátoru
'operátor': "identifier1" se liší v úrovních dereference z 'identifier2.  
  
 Výraz zadaný operandy zahrnující má nekompatibilní operandem nebo implicitně převést typy operandů. Pokud jsou oba operandy aritmetické nebo jsou obě nonarithmetic (například pole nebo ukazatel), použijí se beze změny. Pokud je jeden operand aritmetické a dalších není, aritmetické operand je převést na typ nonarithmetic operandu.  
  
 Tato ukázka generuje C2040 a ukazuje, jak ji odstranit.  
  
```  
// C2040.cpp  
// Compile by using: cl /c /W3 C2040.cpp  
bool test() {  
   char c = '3';  
   return c == "3"; // C2446, C2040  
   // return c == '3'; // OK  
}  
```