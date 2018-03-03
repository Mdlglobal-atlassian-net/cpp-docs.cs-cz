---
title: "Typy Integer jazyka C s nastavenou velikostí | Microsoft Docs"
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
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 609d932b92d40fd4e080d12d13a8872417b56440
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c-sized-integer-types"></a>Typy Integer jazyka C s nastavenou velikostí
**Konkrétní Microsoft**  
  
 Jazyk Microsoft C obsahuje podporu pro celočíselné typy s velikostí. 8 - 16-, 32- nebo 64bitovou celočíselnou hodnotu proměnné můžou deklarovat pomocí __int *n*  zadejte specifikátor, kde  *n*  je velikost v bitech, proměnné, celé číslo. Hodnota  *n*  může být 8, 16, 32 nebo 64. Následující příklad deklaruje jednu proměnnou každého ze čtyř celočíselných typů s velikostí:  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 První tři typy celočíselných typů s velikostí jsou synonyma pro typy ANSI, které mají stejnou velikost, a jsou užitečné pro psaní přenositelného kódu, který se na různých platformách chová stejně. Upozorňujeme, že se datový typ __int8 totožná s znakový typ \__int16 je totožná s krátkou, typ a \__int32 je totožná s typu int. \__Int64 typ nemá ekvivalentní protějšek ANSI.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Úložiště základních typů](../c-language/storage-of-basic-types.md)