---
title: Skalární typy | Dokumentace Microsoftu
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
ms.openlocfilehash: 6af598ec6e27138f4e666007018ce803177697b3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211138"
---
# <a name="scalar-types"></a>Skalární typy
I když přístupu k datům může pocházet z libovolné zarovnání, doporučuje se, že data být zarovnány na jeho přirozené hranice předcházet ztrátě výkonu (nebo jeho násobek). Výčty jsou konstantních celých čísel a jsou považovány za 32bitová celá čísla. Následující tabulka popisuje definice typu a doporučené úložiště pro něj, protože se týkají zarovnání použitím následujících hodnot zarovnání:  
  
-   Byte – 8 bitů  
  
-   Word – 16 bitů  
  
-   Double Word – 32 bitů  
  
-   Čtyř Word - 64 bitů  
  
-   Okta Word - 128 bitů  
  
|||||  
|-|-|-|-|  
|Skalární typ.|Datový typ jazyka C|Velikost úložiště (v bajtech)|Doporučené zarovnání|  
|**INT8**|**char**|1|Byte|  
|**UINT8**|**unsigned char**|1|Byte|  
|**INT16**|**short**|2|Word|  
|**UINT16**|**short bez znaménka**|2|Word|  
|**INT32**|**int**, **dlouhý**|4|Doubleword|  
|**UINT32**|**unsigned int, unsigned long**|4|Doubleword|  
|**INT64**|**__int64**|8|Quadword|  
|**UINT64**|**unsigned __int64**|8|Quadword|  
|**FP32 (jednoduché přesnosti)**|**float**|4|Doubleword|  
|**FP64 (Dvojitá přesnost)**|**double**|8|Quadword|  
|**UKAZATEL**|<strong>\*</strong>|8|Quadword|  
|**__m64**|**__m64 – struktura**|8|Quadword|  
|**__m128**|**__m128 – struktura**|16|Octaword|  
  
## <a name="see-also"></a>Viz také  
 [Typy a úložiště](../build/types-and-storage.md)