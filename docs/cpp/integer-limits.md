---
title: Omezení typu Integer | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 656873dc510f53fc05250a28c61cc452078c4aca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="integer-limits"></a>Omezení typu Integer

**Konkrétní Microsoft**

V následující tabulce jsou uvedené limity pro typy celého čísla. Tyto limity, je definována v souboru standardní hlavičku < Limits.h – >.

## <a name="limits-on-integer-constants"></a>Omezení konstanty typu Integer

|Konstanta|Význam|Hodnota|
|--------------|-------------|-----------|
|**CHAR_BIT –**|Počet bitů v nejmenší proměnné, která není pole verze.|8|
|**SCHAR_MIN –**|Minimální hodnota proměnné typu **podepsané char**.|-128|
|**SCHAR_MAX**|Maximální hodnota proměnné typu **podepsané char**.|127|
|**UCHAR_MAX**|Maximální hodnota proměnné typu **nepodepsané char**.|255 (0xff)|
|**CHAR_MIN –**|Minimální hodnota proměnné typu **char**.|-128; 0, pokud /J možnost použít|
|**CHAR_MAX –**|Maximální hodnota proměnné typu **char**.|127; Pokud se používá možnost /J 255|
|**MB_LEN_MAX**|Maximální počet bajtů v multicharacter konstanta.|5|
|**SHRT_MIN –**|Minimální hodnota proměnné typu **krátké**.|-32768|
|**SHRT_MAX**|Maximální hodnota proměnné typu **krátké**.|32767|
|**USHRT_MAX**|Maximální hodnota proměnné typu **nepodepsané prostě**.|65535 (0xffff)|
|**INT_MIN –**|Minimální hodnota proměnné typu **int**.|-2147483648|
|**INT_MAX –**|Maximální hodnota proměnné typu **int**.|2147483647|
|**UINT_MAX**|Maximální hodnota proměnné typu **nepodepsané int**.|4294967295 (0xffffffff)|
|**LONG_MIN**|Minimální hodnota proměnné typu **dlouho**.|-2147483648|
|**LONG_MAX**|Maximální hodnota proměnné typu **dlouho**.|2147483647|
|**ULONG_MAX**|Maximální hodnota proměnné typu **nepodepsané dlouho**.|4294967295 (0xffffffff)|
|**LLONG_MIN**|Minimální hodnota proměnné typu **dlouho dlouho**|-9223372036854775808|
|**LLONG_MAX**|Maximální hodnota proměnné typu **dlouho dlouho**|9223372036854775807|
|**ULLONG_MAX**|Maximální hodnota proměnné typu **dlouho dlouho bez znaménka**|18446744073709551615 (0xffffffffffffffff)|

Pokud hodnota přesahuje reprezentace největší celé číslo, kompilátoru Microsoft generuje chybu.

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[Plovoucí omezení](../cpp/floating-limits.md)  
