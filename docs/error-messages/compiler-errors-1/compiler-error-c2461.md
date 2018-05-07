---
title: C2461 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2461
dev_langs:
- C++
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47aee3122dad3e875cf58d5a41bcadda297e1463
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2461"></a>C2461 chyby kompilátoru
  
> '*třída*': konstruktor Syntaxe chybí formální parametry  
  
 Konstruktor pro třídu neurčuje žádné formální parametry. Prohlášení o konstruktor musíte zadat seznam formální parametr. V seznamu nesmí být prázdné.  
  
Chcete-li tento problém vyřešit, přidejte po deklaraci pár závorek *třída*:: **třída*.  
  
## <a name="example"></a>Příklad  
  
Následující příklad ukazuje, jak opravit C2461:  
  
```cpp  
// C2461.cpp  
// compile with: /c  
class C {  
   C::C;     // C2461  
   C::C();   // OK  
};  
```