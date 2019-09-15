---
title: imaxabs
ms.date: 04/05/2018
api_name:
- imaxabs
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- imaxabs
helpviewer_keywords:
- imaxabs function
ms.assetid: de2566a3-1415-4e9a-91b5-7ac3a49ebf5e
ms.openlocfilehash: c1f20c4de2ff9070bae3bfaeb8ba2d97d87d2d4d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954681"
---
# <a name="imaxabs"></a>imaxabs

Vypočítá absolutní hodnotu celého čísla libovolné velikosti.

## <a name="syntax"></a>Syntaxe

```C
intmax_t imaxabs(
   intmax_t n
);
```

### <a name="parameters"></a>Parametry

*n*<br/>
Celočíselná hodnota.

## <a name="return-value"></a>Návratová hodnota

Funkce **imaxabs** vrací absolutní hodnotu argumentu. Nevrátila se žádná chybová zpráva.

> [!NOTE]
> Vzhledem k tomu, že rozsah záporných celých čísel, která lze znázornit pomocí **intmax_t** , je větší než rozsah kladných celých čísel, která lze reprezentovat, je možné dodat argument pro **imaxabs** , který nelze převést. Pokud absolutní hodnota argumentu nemůže být reprezentována návratovým typem, chování **imaxabs** není definováno.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**imaxabs**|\<inttypes.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_imaxabs.c
// Build using: cl /W3 /Tc crt_imaxabs.c
// This example calls imaxabs to compute an
// absolute value, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x = LLONG_MIN + 2;

   printf("The absolute value of %lld is %lld\n", x, imaxabs(x));
}
```

```Output
The absolute value of -9223372036854775806 is 9223372036854775806
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
