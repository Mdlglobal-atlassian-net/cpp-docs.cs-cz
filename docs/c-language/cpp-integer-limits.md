---
title: Omezení celého čísla C a C++
ms.date: 10/21/2019
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: 6940f36e37ec58ca8fe23c9062928cbf90b125bd
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778379"
---
# <a name="c-and-c-integer-limits"></a>Omezení celého čísla C a C++

**Specifické pro Microsoft**

Omezení pro celočíselné typy v jazyce C a C++ jsou uvedena v následující tabulce. Tato omezení jsou definována v souboru `<limits.h>`hlaviček Standard C. Hlavička `<limits>` standardní knihovny jazyka C++ obsahuje `<climits>`, který zahrnuje `<limits.h>`.

Microsoft C také umožňuje deklaraci velikosti celočíselných proměnných, což jsou celočíselné typy s velikostí 8-, 16, 32 nebo 64-bitů. Další informace o velikosti celých čísel v jazyce C naleznete v tématu [velikosti celočíselných typů](../c-language/c-sized-integer-types.md).

## <a name="limits-on-integer-constants"></a>Omezení pro celočíselné konstanty

|**Trvalé**|Význam|Hodnota|
|------------------|-------------|-----------|
|**CHAR_BIT**|Počet bitů v nejmenší proměnné, která není bitového pole.|8|
|**SCHAR_MIN**|Minimální hodnota pro proměnnou typu **signed char**.|-128|
|**SCHAR_MAX**|Maximální hodnota pro proměnnou typu **signed char**.|127|
|**UCHAR_MAX**|Maximální hodnota pro proměnnou typu **char bez znaménka**.|255 (0xFF)|
|**CHAR_MIN**|Minimální hodnota proměnné typu **char**|-128; 0, pokud se používá možnost/J|
|**CHAR_MAX**|Maximální hodnota proměnné typu **char**.|127; 255, pokud se používá možnost/J|
|**MB_LEN_MAX**|Maximální počet bajtů v konstantě s více znaky.|5|
|**SHRT_MIN**|Minimální hodnota pro proměnnou typu **short**|-32768|
|**SHRT_MAX**|Maximální hodnota pro proměnnou typu **short**|32767|
|**USHRT_MAX**|Maximální hodnota pro proměnnou typu **short bez znaménka**.|65535 (0xFFFF)|
|**INT_MIN**|Minimální hodnota proměnné typu **int**|-2147483647-1|
|**INT_MAX**|Maximální hodnota proměnné typu **int**.|2147483647|
|**UINT_MAX**|Maximální hodnota pro proměnnou typu **int bez znaménka**.|4294967295 (0xFFFFFFFF)|
|**LONG_MIN**|Minimální hodnota proměnné typu **Long**.|-2147483647-1|
|**LONG_MAX**|Maximální hodnota proměnné typu **Long**.|2147483647|
|**ULONG_MAX**|Maximální hodnota pro proměnnou typu **bez znaménka Long**.|4294967295 (0xFFFFFFFF)|
|**LLONG_MIN**|Minimální hodnota proměnné typu **Long Long**.|-9 223 372 036 854 775 807-1|
|**LLONG_MAX**|Maximální hodnota proměnné typu **Long Long**.|9 223 372 036 854 775 807|
|**ULLONG_MAX**|Maximální hodnota proměnné typu **bez znaménka Long Long**.|18446744073709551615 (0xffffffffffffffff)|

Pokud hodnota přesáhne největší reprezentace celého čísla, kompilátor společnosti Microsoft vygeneruje chybu.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Konstanty typu Integer jazyka C](../c-language/c-integer-constants.md)
