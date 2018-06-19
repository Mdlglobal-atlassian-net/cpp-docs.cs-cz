---
title: C2040 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2040
dev_langs:
- C++
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6b19a5dd647e51efb46ef9798b7f7cdff5339b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167538"
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