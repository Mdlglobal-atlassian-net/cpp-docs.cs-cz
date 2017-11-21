---
title: "Na základě Pointers (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c50bc36fbc88dc6ac6f2efd2686f13f49c28aa19
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="based-pointers-c"></a>Základní ukazatelé (C)
**Konkrétní Microsoft**  
  
 [__based (referenční dokumentace jazyka C++)](../cpp/based-pointers-cpp.md)  
  
 Pro C kompilátory Microsoft 32bitové a 64bitové verze je založené na ukazatel 32bitovou nebo 64bitovou posun z 32bitové nebo 64bitové ukazatel základní. Na základě adresování je užitečné pro vykonávat kontrolu oddíly, které jsou přiděleny objekty, a tím snížení velikosti spustitelný soubor a zvýšit rychlost provádění. Obecně je formulář pro zadání založené na ukazatele  
  
```  
  
type  
__based(  
base  
)  
declarator  
  
```  
  
 "Podle ukazatel" typu variant na základě adres umožňuje specifikaci ukazatel jako základ. Na základě ukazatele, pak je posun do části paměti od začátku ukazatele, na kterých je založena. Ukazatele na základě adres ukazatel jsou pouze formu `__based` – klíčové slovo v 32bitové a 64bitové verze kompilace. V takové kompilaci jsou 32bitovou nebo 64bitovou posunutí ze základní 32bitové nebo 64bitové verze.  
  
 Jedním použitím ukazatelů na základě ukazatelů jsou trvalé identifikátory, které obsahují ukazatele. Propojený seznam, který se skládá z ukazatelů založených na ukazateli lze uložit na disk a následně jej lze znovu načíst na jiné místo v paměti, při současném zachování platnosti ukazatelů.  
  
 Následující příklad ukazuje ukazatel založené na ukazatel.  
  
```  
void *vpBuffer;  
  
struct llist_t  
{  
    void __based( vpBuffer ) *vpData;  
    struct llist_t __based( vpBuffer ) *llNext;  
};  
```  
  
 Ukazateli `vpBuffer` je přiřazena adresa paměti, která je přidělena v programu později. Propojený seznam je přemístěn vzhledem k hodnotě `vpBuffer`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)