---
title: Omezení typu Integer | Dokumentace Microsoftu
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
ms.openlocfilehash: 6f49e224520751e08ba6aa7e37932314e11ef8a5
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315183"
---
# <a name="integer-limits"></a>Omezení typu Integer

**Specifické pro Microsoft**

Limity pro celočíselné typy jsou uvedeny v následující tabulce. Tato omezení jsou také definovány v souboru standardní hlavičku \<limits.h >.

## <a name="limits-on-integer-constants"></a>Omezení na konstanty typu Integer

|Konstanta|Význam|Hodnota|
|--------------|-------------|-----------|
|CHAR_BIT|Počet bitů v proměnné nejmenší, který není bitového pole.|8|
|SCHAR_MIN|Minimální hodnota pro proměnnou typu **podepsané char**.|-128|
|SCHAR_MAX|Maximální hodnota pro proměnnou typu **podepsané char**.|127|
|UCHAR_MAX|Maximální hodnota pro proměnnou typu **unsigned char**.|255 (0xff)|
|CHAR_MIN|Minimální hodnota pro proměnnou typu **char**.|-128; 0, pokud používá j.|
|CHAR_MAX|Maximální hodnota pro proměnnou typu **char**.|127; je-li použita možnost /J 255|
|MB_LEN_MAX|Maximální počet bajtů v víceznaková konstanta.|5|
|SHRT_MIN|Minimální hodnota pro proměnnou typu **krátký**.|-32768|
|SHRT_MAX|Maximální hodnota pro proměnnou typu **krátký**.|32767|
|USHRT_MAX|Maximální hodnota pro proměnnou typu **unsigned short**.|65535 (0xffff)|
|INT_MIN|Minimální hodnota pro proměnnou typu **int**.|-2147483648|
|INT_MAX|Maximální hodnota pro proměnnou typu **int**.|2147483647|
|UINT_MAX|Maximální hodnota pro proměnnou typu **unsigned int**.|4294967295 (0xffffffff)|
|LONG_MIN|Minimální hodnota pro proměnnou typu **dlouhé**.|-2147483648|
|LONG_MAX|Maximální hodnota pro proměnnou typu **dlouhé**.|2147483647|
|ULONG_MAX|Maximální hodnota pro proměnnou typu **unsigned long**.|4294967295 (0xffffffff)|
|LLONG_MIN|Minimální hodnota pro proměnnou typu **long long**|-9223372036854775808|
|LLONG_MAX|Maximální hodnota pro proměnnou typu **long long**|9223372036854775807|
|ULLONG_MAX|Maximální hodnota pro proměnnou typu **unsigned long long.**|18446744073709551615 (0xffffffffffffffff)|

Pokud hodnota přesahuje reprezentace největší celé číslo, Microsoft kompilátor vygeneruje chybu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Plovoucí omezení](../cpp/floating-limits.md)