---
title: Skalární typy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5490bb33cafd8d2942e434ab9c50e34441506463
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381168"
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
|**INT16**|**short**|2|Word|  
|**UINT16**|**short bez znaménka**|2|Word|  
|**INT32**|**int, dlouho**|4|Doubleword|  
|**UINT32**|**nepodepsané int, long bez znaménka**|4|Doubleword|  
|**INT64**|`__int64`|8|Quadword|  
|**UINT64**|**__int64 bez znaménka**|8|Quadword|  
|**FP32 (jednoduchá přesnost)**|**float**|4|Doubleword|  
|**FP64 (Dvojitá přesnost)**|**double**|8|Quadword|  
|**UKAZATELE**|**\***|8|Quadword|  
|`__m64`|**__m64 – struktura**|8|Quadword|  
|`__m128`|**__m128 – struktura**|16|Octaword|  
  
## <a name="see-also"></a>Viz také  
 [Typy a úložiště](../build/types-and-storage.md)