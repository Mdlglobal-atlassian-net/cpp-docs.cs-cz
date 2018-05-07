---
title: C3537 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3537
dev_langs:
- C++
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f03f02062e61e4034f0a809784ba571ce532e07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3537"></a>C3537 chyby kompilátoru
'type': nejde přetypovat na typ, který obsahuje 'auto'  
  
 Proměnné pro zadaný typ nejde přetypovat, protože obsahuje typ `auto` – klíčové slovo a ve výchozím nastavení [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) – možnost kompilátoru je v platnosti.  
  
## <a name="example"></a>Příklad  
 Následující kód vypočítá C3537, protože jsou proměnné přetypovat na typ, který obsahuje `auto` – klíčové slovo.  
  
```  
// C3537.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int value = 123;  
   auto(value);                        // C3537  
   (auto)value;                        // C3537  
   auto x1 = auto(value);              // C3537  
   auto x2 = (auto)value;              // C3537  
   auto x3 = static_cast<auto>(value); // C3537  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../../cpp/auto-keyword.md)