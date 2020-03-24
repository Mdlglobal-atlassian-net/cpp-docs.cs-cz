---
title: Omezení typu Integer
ms.date: 01/29/2018
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
ms.openlocfilehash: 75cd05e73aba2d2e82e8077e0a289d8b0fae7ec4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178221"
---
# <a name="integer-limits"></a>Omezení typu Integer

**Specifické pro společnost Microsoft**

Omezení pro celočíselné typy jsou uvedena v následující tabulce. Tato omezení jsou také definována v souboru hlaviček Standard \<Limits. h >.

## <a name="limits-on-integer-constants"></a>Omezení pro celočíselné konstanty

|Trvalé|Význam|Hodnota|
|--------------|-------------|-----------|
|CHAR_BIT|Počet bitů v nejmenší proměnné, která není bitového pole.|8|
|SCHAR_MIN|Minimální hodnota pro proměnnou typu **signed char**.|-128|
|SCHAR_MAX|Maximální hodnota pro proměnnou typu **signed char**.|127|
|UCHAR_MAX|Maximální hodnota pro proměnnou typu **char bez znaménka**.|255 (0xff)|
|CHAR_MIN|Minimální hodnota proměnné typu **char**|-128; 0, pokud se používá možnost/J|
|CHAR_MAX|Maximální hodnota proměnné typu **char**.|127; 255, pokud se používá možnost/J|
|MB_LEN_MAX|Maximální počet bajtů v konstantě s více znaky.|5|
|SHRT_MIN|Minimální hodnota pro proměnnou typu **short**|-32768|
|SHRT_MAX|Maximální hodnota pro proměnnou typu **short**|32767|
|USHRT_MAX|Maximální hodnota pro proměnnou typu **short bez znaménka**.|65535 (0xffff)|
|INT_MIN|Minimální hodnota proměnné typu **int**|-2147483648|
|INT_MAX|Maximální hodnota proměnné typu **int**.|2147483647|
|UINT_MAX|Maximální hodnota pro proměnnou typu **int bez znaménka**.|4294967295 (0xffffffff)|
|LONG_MIN|Minimální hodnota proměnné typu **Long**.|-2147483648|
|LONG_MAX|Maximální hodnota proměnné typu **Long**.|2147483647|
|ULONG_MAX|Maximální hodnota pro proměnnou typu **bez znaménka Long**.|4294967295 (0xffffffff)|
|LLONG_MIN|Minimální hodnota pro proměnnou typu **Long Long**|-9223372036854775808|
|LLONG_MAX|Maximální hodnota pro proměnnou typu **Long Long**|9223372036854775807|
|ULLONG_MAX|Maximální hodnota pro proměnnou typu **bez znaménka Long Long**|18446744073709551615 (0xffffffffffffffff)|

Pokud hodnota přesáhne největší reprezentace celého čísla, kompilátor společnosti Microsoft vygeneruje chybu.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Plovoucí omezení](../cpp/floating-limits.md)
