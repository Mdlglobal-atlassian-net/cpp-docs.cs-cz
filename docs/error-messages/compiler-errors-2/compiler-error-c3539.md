---
title: C3539 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3539
dev_langs:
- C++
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f704bd283ab5228a8988d587707e978aa5b49e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256399"
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