---
title: C3536 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3536
dev_langs:
- C++
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f88e656b0d63b6a7a4d60ace2f4cd5e2347d188
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250284"
---
# <a name="compiler-error-c3536"></a>C3536 chyby kompilátoru
'symbol': nelze použít před inicializací  
  
 Uvedené symbol nelze použít, před inicializací. V praxi to znamená, že proměnné nelze použít k chybě při inicializaci sám sebe.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Inicializace nezdařila proměnné sama se sebou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3536, protože každá proměnná je inicializován sama se sebou.  
  
```  
// C3536.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto a = a;     //C3536  
   auto b = &b;    //C3536  
   auto c = c + 1; //C3536  
   auto* d = &d;   //C3536  
   auto& e = e;    //C3536  
   return 0;  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../../cpp/auto-keyword.md)