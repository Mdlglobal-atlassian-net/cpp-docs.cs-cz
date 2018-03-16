---
title: "Deklarátory abstraktu jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e16711a61b3c8060396ce10aa2061600903499e
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
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