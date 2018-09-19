---
title: Omezení typu Integer jazyka C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02a4194d69bf07d27777ad30cf9ed0e5794c04c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136280"
---
# <a name="c-integer-limits"></a>Omezení typu Integer v jazyce C++ 

**Specifické pro Microsoft**

Limity pro celočíselné typy jsou uvedeny v následující tabulce. Tato omezení jsou definovány v hlavičce standardní limity. H. Microsoft C umožňuje také deklaraci proměnných integer s nastavenou velikostí, které jsou integrální typy o velikosti 8, 16 a 32 bity. Další informace o celočíselných najdete v tématu [celočíselné typy s velikostí](../c-language/c-sized-integer-types.md).

## <a name="limits-on-integer-constants"></a>Omezení na konstanty typu Integer

|**Konstanty**|Význam|Hodnota|
|------------------|-------------|-----------|
|**CHAR_BIT**|Počet bitů v proměnné nejmenší, který není bitového pole.|8|
|**SCHAR_MIN**|Minimální hodnota pro proměnnou typu **podepsané char**.|-128|
|**SCHAR_MAX**|Maximální hodnota pro proměnnou typu **podepsané char**.|127|
|**UCHAR_MAX**|Maximální hodnota pro proměnnou typu **unsigned char**.|255 (0xff)|
|**CHAR_MIN**|Minimální hodnota pro proměnnou typu **char**.|-128; 0, pokud používá j.|
|**CHAR_MAX**|Maximální hodnota pro proměnnou typu **char**.|127; je-li použita možnost /J 255|
|**MB_LEN_MAX**|Maximální počet bajtů v víceznaková konstanta.|5|
|**SHRT_MIN**|Minimální hodnota pro proměnnou typu **krátký**.|-32768|
|**SHRT_MAX**|Maximální hodnota pro proměnnou typu **krátký**.|32767|
|**USHRT_MAX**|Maximální hodnota pro proměnnou typu **unsigned short**.|65535 (0xffff)|
|**INT_MIN**|Minimální hodnota pro proměnnou typu **int**.|-2147483647 - 1|
|**INT_MAX**|Maximální hodnota pro proměnnou typu **int**.|2147483647|
|**UINT_MAX**|Maximální hodnota pro proměnnou typu **unsigned int**.|4294967295 (0xffffffff)|
|**LONG_MIN**|Minimální hodnota pro proměnnou typu **dlouhé**.|-2147483647 - 1|
|**LONG_MAX**|Maximální hodnota pro proměnnou typu **dlouhé**.|2147483647|
|**ULONG_MAX**|Maximální hodnota pro proměnnou typu **unsigned long**.|4294967295 (0xffffffff)|

Pokud hodnota přesahuje reprezentace největší celé číslo, Microsoft kompilátor vygeneruje chybu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Konstanty typu Integer jazyka C](../c-language/c-integer-constants.md)
