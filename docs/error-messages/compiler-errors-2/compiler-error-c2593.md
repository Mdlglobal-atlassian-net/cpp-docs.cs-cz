---
title: C2593 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2593
dev_langs:
- C++
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e419416266e0e3c4ebff8190b3b26b1c43c9ba0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229882"
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