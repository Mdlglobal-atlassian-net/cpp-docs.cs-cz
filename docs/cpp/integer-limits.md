---
title: "Omezení typu Integer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a302a3b5b4542274f037d622c7be24f7c0dbb13a
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="integer-limits"></a>Omezení typu Integer
**Microsoft Specific**  
  
 V následující tabulce jsou uvedené limity pro typy celého čísla. Tyto limity, je definována v souboru standardní hlavičku \<Limits.h – >.  
  
### <a name="limits-on-integer-constants"></a>Omezení konstanty typu Integer  
  
|Konstanta|Význam|Hodnota|  
|--------------|-------------|-----------|  
|**CHAR_BIT**|Počet bitů v nejmenší proměnné, která není pole verze.|8|  
|**SCHAR_MIN**|Minimální hodnota proměnné typu **podepsané char**.|-128|  
|**SCHAR_MAX**|Maximální hodnota proměnné typu **podepsané char**.|127|  
|**UCHAR_MAX**|Maximální hodnota proměnné typu `unsigned char`.|255 (0xff)|  
|**CHAR_MIN –**|Minimální hodnota proměnné typu `char`.|-128; 0, pokud /J možnost použít|  
|**CHAR_MAX**|Maximální hodnota proměnné typu `char`.|127; Pokud se používá možnost /J 255|  
|**MB_LEN_MAX**|Maximální počet bajtů v multicharacter konstanta.|5|  
|**SHRT_MIN**|Minimální hodnota proměnné typu **krátké**.|-32768|  
|**SHRT_MAX**|Maximální hodnota proměnné typu **krátké**.|32767|  
|**USHRT_MAX**|Maximální hodnota proměnné typu **nepodepsané prostě**.|65535 (0xffff)|  
|**INT_MIN**|Minimální hodnota proměnné typu `int`.|-2147483648|  
|**INT_MAX**|Maximální hodnota proměnné typu `int`.|2147483647|  
|**UINT_MAX**|Maximální hodnota proměnné typu `unsigned int`.|4294967295 (0xffffffff)|  
|**LONG_MIN**|Minimální hodnota proměnné typu **dlouho**.|-2147483648|  
|**LONG_MAX**|Maximální hodnota proměnné typu **dlouho**.|2147483647|  
|**ULONG_MAX**|Maximální hodnota proměnné typu `unsigned long`.|4294967295 (0xffffffff)|  
|**_I64_MIN**|Minimální hodnota proměnné typu`__int64`|-9223372036854775808|  
|**_I64_MAX**|Maximální hodnota proměnné typu`__int64`|9223372036854775807|  
|**_UI64_MAX**|Maximální hodnota proměnné typu **__int64 bez znaménka**|18446744073709551615 (0xffffffffffffffff)|  
  
 Pokud hodnota přesahuje reprezentace největší celé číslo, kompilátoru Microsoft generuje chybu.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Plovoucí omezení](../cpp/floating-limits.md)