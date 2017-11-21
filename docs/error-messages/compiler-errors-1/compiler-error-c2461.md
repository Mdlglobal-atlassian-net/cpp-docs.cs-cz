---
title: "C2461 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2461
dev_langs: C++
helpviewer_keywords: C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 18413443abb074d16c0d813de660555f8ba2b4c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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