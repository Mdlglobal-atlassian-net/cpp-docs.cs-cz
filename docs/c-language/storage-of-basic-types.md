---
title: "Úložiště základních typů | Microsoft Docs"
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
- specifiers [C++], type
- integral types, storage
- storage [C++], types
- floating-point numbers, storage
- type specifiers [C++], sizes
- arithmetic operations [C++], types
- int data type
- short data type
- signed types [C++], storage
- long double keyword [C], storage
- long keyword [C]
- double data type, storage
- types [C], arithmetic
- integral types
- data types [C], specifiers
- storing types [C++]
- unsigned types [C++], storage
- data types [C], storage
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dff8df934a0c812ca798d5a1e87188e2468902ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="storage-of-basic-types"></a>Úložiště základních typů
Následující tabulka shrnuje úložiště přidružená ke každému základnímu typu.  
  
### <a name="sizes-of-fundamental-types"></a>Velikost základní typy  
  
|Typ|Úložiště|  
|----------|-------------|  
|`char`, `unsigned char`, **podepsané char**|1 bajt|  
|**krátký**, **prostě bez znaménka**|2 bajtů|  
|`int`, `unsigned int`|4 bajty|  
|**dlouhé**,`unsigned long`|4 bajty|  
|**float**|4 bajty|  
|**double**|8 bajtů|  
|`long double`|8 bajtů|  
  
 Datové typy jazyka C spadají do hlavních kategorií. "Integrální typy" `char`, `int`, **krátké**, **dlouho**, **podepsané**, `unsigned`, a `enum`. "Plovoucí typy" **float**, **dvojité**, a `long double`. „Aritmetické typy“ zahrnují všechny typy s plovoucí desetinnou čárkou a celočíselné typy.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace a typy](../c-language/declarations-and-types.md)