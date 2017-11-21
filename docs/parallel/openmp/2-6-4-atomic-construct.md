---
title: "2.6.4 atomic – konstrukce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ea1cc2474a8420227dcf2b6b6e87f255ce144cf4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="264-atomic-construct"></a>2.6.4 atomic – konstrukce
`atomic` – Direktiva zajišťuje, atomicky, aktualizaci umístění konkrétní paměti místo vystavení možnost více souběžných vláken zápis. Syntaxe `atomic` – Direktiva vypadá takto:  
  
```  
#pragma omp atomic new-lineexpression-stmt  
```  
  
 Příkaz výrazu musí mít jednu z následujících podob:  
  
 *x binop*= *expr*  
  
 x ++  
  
 ++ x  
  
 x –  
  
 – x  
  
 V předchozím výrazy:  
  
-   *x* je výraz lvalue s skalárního typu.  
  
-   *Expr* je výraz s skalárního typu a neodkazuje objektu určeném *x*.  
  
-   `binop`není přetížené operátor a je jedním z +, *, -, / &, ^, &#124; <\<, nebo >>.  
  
 I když je definované implementací jestli implementace nahradí všechny `atomic` direktivy s **kritické** direktivy, které mají stejnou jedinečný *název*, `atomic` – direktiva Povolí lepší optimalizace. Často hardwaru pokyny jsou k dispozici, můžete provést atomic aktualizace s nejmenším režie.  
  
 Zatížení a ukládání objektu určeném *x* jsou atomic; vyhodnocení *expr* není atomic. Abyste se vyhnuli časování, by měly být chráněné všechny aktualizace umístění paralelně s `atomic` direktivy, kromě těch, které jsou známé jako bezplatné časování.  
  
 Omezení `atomic` – direktiva jsou následující:  
  
-   Atomic všude, kde x umístění úložiště v rámci programu musí mít kompatibilní typ.  
  
## <a name="examples"></a>Příklady:  
  
```  
extern float a[], *p = a, b;  
/* Protect against races among multiple updates. */  
#pragma omp atomic  
a[index[i]] += b;  
/* Protect against races with updates through a. */  
#pragma omp atomic  
p[i] -= 1.0f;  
  
extern union {int n; float x;} u;  
/* ERROR - References through incompatible types. */  
#pragma omp atomic  
u.n++;  
#pragma omp atomic  
u.x -= 1.0f;  
```