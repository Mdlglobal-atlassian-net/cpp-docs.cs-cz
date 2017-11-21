---
title: "C3539 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3539
dev_langs: C++
helpviewer_keywords: C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 03283217be6aabbf216e2e60ad47abfc01a961d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3539"></a>C3539 chyby kompilátoru
'type': argumentem šablony nemůže být typu, který obsahuje 'auto'  
  
 Typ argumentu uvedené šablony nesmí obsahovat použití `auto` – klíčové slovo.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Nezadávejte argument šablony s `auto` – klíčové slovo.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3539.  
  
```  
// C3539.cpp  
// Compile with /Zc:auto  
template<class T> class C{};  
int main()  
{  
   C<auto> c;   // C3539  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../../cpp/auto-keyword.md)