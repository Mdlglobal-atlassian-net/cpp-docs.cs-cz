---
title: "C2593 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2593
dev_langs:
- C++
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 675c929995e7b0c4043586cf081343136d8e7a5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2593"></a>C2593 chyby kompilátoru
"operátor identifikátor" je nejednoznačný  
  
 Pro přetížené operátor není definován více než jeden možný operátor.  
  
 Tato chyba může být stanovena, pokud používáte explicitní přetypování na jeden nebo více skutečných parametrů.  
  
 Následující ukázka generuje C2593:  
  
```  
// C2593.cpp  
struct A {};  
struct B : A {};  
struct X {};  
struct D : B, X {};  
void operator+( X, X );  
void operator+( A, B );  
D d;  
  
int main() {  
   d +  d;         // C2593, D has an A, B, and X   
   (X)d + (X)d;    // OK, uses operator+( X, X )  
}  
```  
  
 Tato chyba může být způsobeno serializaci s plovoucí desetinnou čárkou proměnné pomocí `CArchive` objektu. Kompilátor identifikuje `<<` operátor jako nejednoznačný. C++ jenom primitivní typy, `CArchive` může serializovat jsou typy pevné velikosti `BYTE`, `WORD`, `DWORD`, a `LONG`. Všechny typy celého čísla musí být převedena na jeden z těchto typů pro serializaci. Typy s plovoucí desetinnou čárkou musí být archivovány pomocí `CArchive::Write()` – členská funkce.  
  
 Následující příklad ukazuje, jak k archivaci proměnné s plovoucí desetinnou čárkou (`f`) do archivu `ar`:  
  
```  
ar.Write(&f, sizeof( float ));  
```