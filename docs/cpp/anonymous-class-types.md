---
title: "Anonymní typy třídy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 854f15dcc597f2fc6e32f8385c1e9d27cfb37362
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="anonymous-class-types"></a>Anonymní typy třídy
Třídy může být anonymní – to znamená, že lze deklarovat bez *identifikátor*. Tato možnost je užitečná při nahrazení názvu třídy názvem `typedef` (viz následující příklad):  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
> [!NOTE]
>  Použití anonymních tříd uvedené v předchozím příkladu je užitečné pro zachování kompatibility se stávajícím kódem jazyka C. V některých kódech jazyka C převládá použití názvu `typedef` ve spojení s anonymními strukturami.  
  
 Anonymní třídy jsou také užitečné, pokud chcete odkazovat člena třídy, jako by nebyl obsažen v samostatné třídě (viz následující příklad):  
  
```  
struct PTValue  
{  
    POINT ptLoc;  
    union  
    {  
        int  iValue;  
        long lValue;  
    };  
};  
  
PTValue ptv;  
```  
  
 V předchozí kód `iValue` je přístupná pomocí operátoru objekt výběru členů (**.**) následujícím způsobem:  
  
```  
int i = ptv.iValue;  
```  
  
 Na anonymní třídy se vztahují jistá omezení. (Další informace o anonymní sjednocení najdete v tématu [sjednocení](../cpp/unions.md).) Anonymní třídy:  
  
-   Nemohou mít konstruktor ani destruktor.  
  
-   Nelze je předat jako argumenty funkcím (pokud není zrušena kontrola typu pomocí operátoru tři tečky).  
  
-   Nelze je vrátit jako návratové hodnoty funkcí.  
  
## <a name="anonymous-structs"></a>Anonymní struktury  
  
### <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Rozšíření jazyka Microsoft C umožňuje deklarovat proměnnou struktury v jiné struktuře bez zadání názvu. Tyto vnořené struktury se nazývají anonymní struktury. Jazyk C++ nepovoluje anonymní struktury.  
  
 Ke členům anonymní struktury lze přistupovat, jako kdyby byly členy obsahující struktury.  
  
```  
// anonymous_structures.c  
#include <stdio.h>  
  
struct phone  
{  
    int  areacode;  
    long number;  
};  
  
struct person  
{  
    char   name[30];  
    char   gender;  
    int    age;  
    int    weight;  
    struct phone;    // Anonymous structure; no name needed  
} Jim;  
  
int main()  
{  
    Jim.number = 1234567;  
    printf_s("%d\n", Jim.number);     
}  
//Output: 1234567  
```  
  
**Konkrétní Microsoft END**  
  
