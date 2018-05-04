---
title: Deklarátory abstraktu jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc89682a6d092bd5291551f01d9d592d64fdff85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-abstract-declarators"></a>Deklarátory abstraktu jazyka C
Abstraktní deklarátor je deklarátor bez identifikátoru, sestávající z jednoho nebo více ukazatelů, polí nebo modifikátorů funkce. Modifikátor ukazatele (**\***) vždy předchází identifikátor v deklarátor; pole (**[]**) a funkce ( **()** ) modifikátory použijte identifikátor. Když toto víte, můžete určit, kde by se identifikátor v abstraktním deklarátoru měl objevit a interpretovat tento deklarátor odpovídajícím způsobem. V tématu [interpretace více složité Deklarátory](../c-language/interpreting-more-complex-declarators.md) Další informace a příklady složitých deklarátorů. Obecný `typedef` slouží ke zjednodušení deklarátorů. V tématu [Typedef – deklarace](../c-language/typedef-declarations.md).  
  
 Abstraktní deklarátory mohou být složité. Závorky ve složitých abstraktních deklarátorech určují konkrétní interpretaci, stejně jako je tomu u komplexních deklarátorů v deklaracích.  
  
 Tyto příklady ilustrují abstraktní deklarátory:  
  
```  
int *         // The type name for a pointer to type int:  
  
int *[3]      // An array of three pointers to int  
  
int (*) [5]   // A pointer to an array of five int  
  
int *()       // A function with no parameter specification  
              // returning a pointer to int  
  
// A pointer to a function taking no arguments and   
// returning an int  
  
int (*) ( void )    
  
// An array of an unspecified number of constant pointers to   
// functions each with one parameter that has type unsigned int   
// and an unspecified number of other parameters returning an int   
  
int (*const []) ( unsigned int, ... )  
```  
  
> [!NOTE]
>  Abstraktní deklarátor skládající se z sadu závorky, **()**, není povolena, protože je nejednoznačný. Není možné určit, zda implicitní identifikátor patří do závorek (v tomto případě je to nezměněný typ) nebo před závorky (v tomto případě je to typ funkce).  
  
## <a name="see-also"></a>Viz také  
 [Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)