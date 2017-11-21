---
title: "Skalární typy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 279c4eefb072c6caab85a61bba3abc73be22d3a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="scalar-types"></a>Skalární typy
I když přístupu k datům může pocházet z jakéhokoliv uspořádání, se doporučuje, aby se data zarovnán na jeho přirozené hranic, aby se zabránilo ztrátě výkonu (nebo jeho násobek). Výčty jsou konstantní celá čísla a jsou považovány za 32bitová celá čísla. Následující tabulka popisuje definice typu a doporučené úložiště pro ni, protože se vztahuje k přidružení pomocí následujících hodnot zarovnání:  
  
-   Byte – 8 bitů  
  
-   Word – 16 bitů  
  
-   Hodnota typu Double Word - 32bitová verze  
  
-   Čtyřportové Word - 64 bitů  
  
-   Word okta - 128 bitů  
  
|||||  
|-|-|-|-|  
|Skalární typ.|C – datový typ|Velikost úložiště (v bajtech)|Doporučené zarovnání|  
|**INT8**|`char`|1|Byte|  
|**UINT8**|`unsigned char`|1|Byte|  
|**INT16**|**krátký**|2|Word|  
|**UINT16**|**short bez znaménka**|2|Word|  
|**INT32**|**int, dlouho**|4|Doubleword|  
|**UINT32**|**nepodepsané int, long bez znaménka**|4|Doubleword|  
|**INT64**|`__int64`|8|Quadword|  
|**UINT64**|**__int64 bez znaménka**|8|Quadword|  
|**FP32 (jednoduchá přesnost)**|**plovoucí desetinná čárka**|4|Doubleword|  
|**FP64 (Dvojitá přesnost)**|**Double**|8|Quadword|  
|**UKAZATELE**|**\***|8|Quadword|  
|`__m64`|**__m64 – struktura**|8|Quadword|  
|`__m128`|**__m128 – struktura**|16|Octaword|  
  
## <a name="see-also"></a>Viz také  
 [Typy a úložiště](../build/types-and-storage.md)