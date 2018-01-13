---
title: "Převody z ostatních typů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8dbf2d3d269f5df3a028a5c416f8adca015be6dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="conversions-from-other-types"></a>Převody z ostatních typů
Jelikož hodnota typu `enum` je dle definice hodnotou typu `int`, jsou převody na hodnotu typu `enum` a zpět stejné jako převody pro typ `int`. Pro kompilátor Microsoft C celé číslo, je stejná jako **dlouho**.  
  
 **Konkrétní Microsoft**  
  
 Nejsou povoleny žádné převody mezi typy struktury a sjednocení.  
  
 Jakoukoli hodnotu lze převést na typ `void`, ale výsledek takového převodu lze použít pouze v kontextu, kde je hodnota výrazu zahozena, například v příkazu výrazu.  
  
 Typ `void` nemá dle definice žádnou hodnotu. Proto jej nelze převést na žádný jiný typ a jiné typy nemohou být na typ `void` převedeny přiřazením. Ale explicitně převést hodnotu na typ `void`, jak je popsáno v [převody přetypování](../c-language/type-cast-conversions.md).  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Převody přiřazení](../c-language/assignment-conversions.md)