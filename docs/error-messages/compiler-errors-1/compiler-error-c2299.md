---
title: "C2299 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2299
dev_langs: C++
helpviewer_keywords: C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8190511605a7f01dc399e1d8a8b4af96477fa407
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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