---
title: "C2040 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2040
dev_langs: C++
helpviewer_keywords: C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3504c8e18637ef907d5ab9c941ef7ad550daedf0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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