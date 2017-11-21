---
title: "sizeof Operator (C) operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sizeof
dev_langs: C++
helpviewer_keywords: sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 11fa4acae05c5488ce1d90873ec816744c7e83df
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sizeof-operator-c"></a>sizeof – operátor (C)
Operátor `sizeof` poskytuje velikost úložiště (v bajtech) potřebného k uložení objektu typu operandu. Tento operátor umožňuje Vyhněte se zadání velikosti data závislá na počítače ve vašich aplikacích.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sizeof unary-expression  
sizeof ( type-name )  
```  
  
## <a name="remarks"></a>Poznámky  
Operand je buď identifikátor, který je *unární výraz*, nebo výraz přetypování (to znamená, specifikátor typu uzavřený v závorkách). *Unární výraz* nelze představovat objekt pole bit, typ neúplné nebo označení funkce. Výsledkem je celočíselná konstanta bez znaménka. Standardní hlavička STDDEF. H definuje tento typ jako **size_t –**.  
  
Při použití operátoru `sizeof` na identifikátor pole bude výsledkem velikost celého pole namísto velikosti ukazatele reprezentovaného tímto identifikátorem pole.  
  
Při použití operátoru `sizeof` na název typu struktury nebo sjednocení nebo na identifikátor typu struktury nebo sjednocení bude výsledkem počet bajtů v této struktuře nebo sjednocení, včetně vnitřního a koncového odsazení. Tato velikost může zahrnovat vnitřní a koncové odsazení použité pro zarovnání členů struktury nebo sjednocení na hranicích paměti. Proto výsledek nemusí nutně odpovídat velikosti vypočítané sečtením požadavků na úložiště jednotlivých členů.  
  
Je-li posledním prvkem struktury pole bez velikosti, operátor `sizeof` vrátí velikost struktury bez tohoto pole.  
  
```  
buffer = calloc(100, sizeof (int) );  
```  
  
V tomto příkladu je operátor `sizeof` použit pro předání velikosti typu `int`, který se mezi počítači liší, jako argumentu funkce modulu runtime s názvem `calloc`. Hodnota vrácená touto funkcí je uložena v `buffer`.  
  
```  
static char *strings[] = {  
      "this is string one",  
      "this is string two",  
      "this is string three",  
   };  
const int string_no = ( sizeof strings ) / ( sizeof strings[0] );   
```  
  
V tomto příkladu je proměnná `strings` pole ukazatelů na typ `char`. Počet ukazatelů je počet prvků v poli, ale není zadán. Chcete-li vypočítat počet prvků v tomto poli, lze počet ukazatelů snadno určit pomocí operátoru `sizeof`. **Const** celočíselná hodnota `string_no` je inicializována tak, aby toto číslo. Protože je **const** hodnotu `string_no` nelze upravit.  
  
## <a name="see-also"></a>Viz také  
[Operátory jazyka C](c-operators.md)  
[Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
  