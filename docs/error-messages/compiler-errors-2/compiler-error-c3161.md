---
title: C3161 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3161
dev_langs:
- C++
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2d7aff3eb41c03f5be774704922340ac54126fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250700"
---
# <a name="compiler-error-c3161"></a>C3161 chyby kompilátoru
"rozhraní": vnoření třídy, struktury, sjednocení nebo rozhraní v rozhraní je neplatný; vnoření rozhraní ve třídě, struktura nebo sjednocení je neplatný  
  
 [__Interface](../../cpp/interface.md) může vyskytovat pouze v globálním oboru nebo v oboru názvů. Třída, struktura nebo union nelze vložit do rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3161.  
  
```  
// C3161.cpp  
// compile with: /c  
__interface X {  
   __interface Y {};   // C3161 A nested interface  
};  
```