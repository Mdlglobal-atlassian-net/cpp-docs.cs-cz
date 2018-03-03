---
title: "__alignof – operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- alignas_cpp
- __alignof_cpp
- alignof_cpp
dev_langs:
- C++
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: faceca31928d9c49f3c1cf5b933a65767ece7453
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="alignof-operator"></a>__alignof – operátor
Zavádí c ++ 11 `alignof` operátor, který vrátí zarovnání, v bajtech zadaného typu. Pro maximální přenositelnost použijte operátor alignof místo __alignof – operátor specifické pro společnost Microsoft.  
  
 **Microsoft Specific**  
  
 Vrátí hodnotu typu **size_t –** tedy požadavek zarovnání typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  __alignof( type )
```  
  
## <a name="remarks"></a>Poznámky  
 Příklad:  
  
|Výraz|Hodnota|  
|----------------|-----------|  
|**__alignof – (char)**|1|  
|**__alignof – (krátký)**|2|  
|**__alignof – (int)**|4|  
|**__alignof( \__int64 )**|8|  
|**__alignof – (float)**|4|  
|**__alignof – (double)**|8|  
|**__alignof – (char\* )**|4|  
  
 Hodnota `__alignof` je stejná jako hodnota `sizeof` pro základní typy. Uvažme však tento příklad:  
  
```  
typedef struct { int a; double b; } S;  
// __alignof(S) == 8  
```  
  
 V tomto případě je hodnota `__alignof` požadavkem zarovnání největšího prvku ve struktuře.  
  
 Podobně pro  
  
```  
typedef __declspec(align(32)) struct { int a; } S;  
```  
  
 `__alignof(S)`se rovná `32`.  
  
 Jedno použití `__alignof` by bylo parametrem pro jednu z vlastních rutin přidělení paměti. Například s ohledem na následující definovanou strukturu `S` lze volat rutinu přidělení paměti s názvem `aligned_malloc` pro přidělení paměti na hranici určitého zarovnání.  
  
```  
typedef __declspec(align(32)) struct { int a; double b; } S;  
int n = 50; // array size  
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));  
```  
  
 Další informace o úpravách zarovnání naleznete v:  
  
-   [pack](../preprocessor/pack.md)  
  
-   [Zarovnat](../cpp/align-cpp.md)  
  
-   [__unaligned](../cpp/unaligned.md)  
  
-   [/Zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md)  
  
-   [Příklady zarovnání struktur](../build/examples-of-structure-alignment.md) (x64 konkrétní)  
  
 Další informace o rozdíly v zarovnání v kódu pro x86 a x64 najdete v tématu:  
  
-   [Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)