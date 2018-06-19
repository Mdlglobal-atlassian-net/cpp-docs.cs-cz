---
title: Typy Integer jazyka C s nastavenou velikostí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a61d9ae386efb25171cfdbedc5889c1ffa76e30
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381860"
---
# <a name="c-sized-integer-types"></a>Typy Integer jazyka C s nastavenou velikostí
**Konkrétní Microsoft**  
  
 Jazyk Microsoft C obsahuje podporu pro celočíselné typy s velikostí. 8 - 16-, 32- nebo 64bitovou celočíselnou hodnotu proměnné můžou deklarovat pomocí __int*n* zadejte specifikátor, kde *n* je velikost v bitech, proměnné, celé číslo. Hodnota *n* může být 8, 16, 32 nebo 64. Následující příklad deklaruje jednu proměnnou každého ze čtyř celočíselných typů s velikostí:  
  
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