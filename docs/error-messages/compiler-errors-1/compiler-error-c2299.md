---
title: C2299 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e21213f08e25050932274a64d0ed56db96f2a453
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2299"></a>C2299 chyby kompilátoru
'function': změna v chování: explicitní specializace nemůže být kopírovacího konstruktoru nebo operátor přiřazení kopie  
  
 Tato chyba může být také vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual C++ 2005: předchozích verzí aplikace Visual C++ povolené explicitní specializací pro kopírovacího konstruktoru nebo operátor přiřazení kopírování.  
  
 Chcete-li vyřešit C2299, neprovádějte konstruktor copy nebo operátor přiřazení funkce šablony, ale spíš funkci bez šablony, která přebírá typu třídy. Kód, který volá konstruktor kopírování nebo operátor přiřazení explicitním zadáním argumenty šablony je potřeba odebrat argumenty šablony.  
  
 Následující ukázka generuje C2299:  
  
```  
// C2299.cpp  
// compile with: /c  
class C {  
   template <class T>  
   C (T t);  
  
   template <> C (const C&);   // C2299  
   C (const C&);   // OK  
};  
```