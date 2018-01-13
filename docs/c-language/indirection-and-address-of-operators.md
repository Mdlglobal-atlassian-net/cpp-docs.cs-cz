---
title: "Deferenční operátory a operátory adresy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- address-of operator (&)
- '* operator'
- operators [C++], address-of
- ampersand operator (&)
- '* operator, indirection operator'
- addresses [C++], indirection
- addresses [C++]
- indirection operator
- '& operator, address-of operator'
- null pointers [C++]
- '* operator, address-of operator'
- operators [C++], indirection
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 715221da8ea960f19e9c4ab0e386afc61c3439fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="indirection-and-address-of-operators"></a>Deferenční operátory a operátory adresy
Deferenční operátor (**\***) přistupuje hodnotu nepřímo prostřednictvím ukazatele. Operandem musí být hodnota ukazatele. Výsledkem operace je hodnota adresovaná operandem, tedy hodnota na adrese, na kterou operand ukazuje. Typ výsledku je typ adresovaný operandem.  
  
 Ukazuje-li operand na funkci, je výsledkem označení funkce. Ukazuje-li na umístění úložiště, je výsledkem l-hodnota označující umístění úložiště.  
  
 Pokud je hodnota ukazatele je neplatná, výsledkem nedefinovaný. Následující seznam zahrnuje některé z nejběžnějších situací, které zneplatňují hodnotu ukazatele.  
  
-   Ukazatel je nulový.  
  
-   Ukazatel určuje adresu místní položky, která není v době reference viditelná.  
  
-   Ukazatel určuje adresu, která je pro typ objektu, na který ukazatel ukazuje, nesprávně zarovnána.  
  
-   Ukazatel určuje adresu, která není používána spuštěným programem.  
  
 Address-of – operátor (**&**) poskytuje adresu jeho operand. Operand operátoru adresa může být označení funkce nebo je l hodnota, který určuje objekt, který není pole bit a není deklarovaný s **zaregistrovat** – specifikátor třídy úložiště.  
  
 Výsledkem operace adresa je ukazatel na operand. Typ adresovaný ukazatelem je typ operandu.  
  
 Operátor adresa lze použít pouze pro proměnné základních typů, struktur nebo sjednocení deklarovaných na úrovni souboru nebo na indexované reference polí. V těchto výrazech lze konstantní výraz, který neobsahuje operátor adresa, přičíst nebo odečíst od výrazu adresy.  
  
## <a name="examples"></a>Příklady  
 Následující příklady používají tyto deklarace:  
  
```  
int *pa, x;  
int a[20];  
double d;  
```  
  
 Tento příkaz používá operátor adresa:  
  
```  
pa = &a[5];  
```  
  
 Address-of – operátor (**&**) přebírá adresu šesté elementu pole `a`. Výsledek je uložen v proměnné ukazatele `pa`.  
  
```  
x = *pa;  
```  
  
 Deferenční operátor (**\***) se v tomto příkladu používá pro přístup `int` hodnotu na adrese uložené v `pa`. Hodnota je přiřazená k celočíselné proměnné `x`.  
  
```  
if( x == *&x )  
    printf( "True\n" );  
```  
  
 Tento příklad vytiskne slovo `True` jako ukázku, že je výsledek použití operátoru dereference na adresu proměnné `x` shodný s výrazem `x`.  
  
```  
int roundup( void );     /* Function declaration */  
  
int  *proundup  = roundup;  
int  *pround  = &roundup;  
```  
  
 Po deklaraci funkce `roundup` jsou na tuto funkci `roundup` deklarovány a inicializovány dva ukazatele. První ukazatel `proundup` je inicializován pouze pomocí názvu funkce, zatímco druhý ukazatel `pround` v inicializaci používá operátor adresa. Tyto inicializace jsou ekvivalentní.  
  
## <a name="see-also"></a>Viz také  
 [Deferenční operátor: *](../cpp/indirection-operator-star.md)   
 [Operátor address-of: &](../cpp/address-of-operator-amp.md)