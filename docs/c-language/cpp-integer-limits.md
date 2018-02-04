---
title: "Omezení typu Integer v C++ | Microsoft Docs"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: df6bd92f38078b55280248e071193ecf7149a308
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2018
---
# <a name="c-integer-limits"></a>Omezení typu Integer v jazyce C++ 

**Microsoft Specific**

V následující tabulce jsou uvedené limity pro typy celého čísla. Tato omezení jsou definovány v hlavičce standardní souboru omezení. H. Microsoft C taky umožňuje deklarace proměnných integer s nastavenou velikostí, které jsou celočíselné typy o velikosti 8-, 16 – nebo 32 bitů. Další informace o velikosti celá čísla, najdete v části [typy Integer s nastavenou velikostí](../c-language/c-sized-integer-types.md).

## <a name="limits-on-integer-constants"></a>Omezení konstanty typu Integer

|**Konstantní**|Význam|Hodnota|
|------------------|-------------|-----------|
|**CHAR_BIT**|Počet bitů v nejmenší proměnné, která není pole verze.|8|
|**SCHAR_MIN**|Minimální hodnota proměnné typu **podepsané char**.|-128|
|**SCHAR_MAX**|Maximální hodnota proměnné typu **podepsané char**.|127|
|**UCHAR_MAX**|Maximální hodnota proměnné typu **nepodepsané char**.|255 (0xff)|
|**CHAR_MIN –**|Minimální hodnota proměnné typu **char**.|-128; 0, pokud /J možnost použít|
|**CHAR_MAX**|Maximální hodnota proměnné typu **char**.|127; Pokud se používá možnost /J 255|
|**MB_LEN_MAX**|Maximální počet bajtů v multicharacter konstanta.|5|
|**SHRT_MIN**|Minimální hodnota proměnné typu **krátké**.|-32768|
|**SHRT_MAX**|Maximální hodnota proměnné typu **krátké**.|32767|
|**USHRT_MAX**|Maximální hodnota proměnné typu **nepodepsané prostě**.|65535 (0xffff)|
|**INT_MIN**|Minimální hodnota proměnné typu **int**.|-2147483647 - 1|
|**INT_MAX**|Maximální hodnota proměnné typu **int**.|2147483647|
|**UINT_MAX**|Maximální hodnota proměnné typu **nepodepsané int**.|4294967295 (0xffffffff)|
|**LONG_MIN**|Minimální hodnota proměnné typu **dlouho**.|-2147483647 - 1|
|**LONG_MAX**|Maximální hodnota proměnné typu **dlouho**.|2147483647|
|**ULONG_MAX**|Maximální hodnota proměnné typu **nepodepsané dlouho**.|4294967295 (0xffffffff)|

Pokud hodnota přesahuje reprezentace největší celé číslo, kompilátoru Microsoft generuje chybu.

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[Konstanty typu Integer jazyka C](../c-language/c-integer-constants.md)  
