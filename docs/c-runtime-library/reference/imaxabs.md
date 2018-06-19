---
title: imaxabs – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- imaxabs
apilocation:
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
apitype: DLLExport
f1_keywords:
- imaxabs
dev_langs:
- C++
helpviewer_keywords:
- imaxabs function
ms.assetid: de2566a3-1415-4e9a-91b5-7ac3a49ebf5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9476db108a4296811e1c88e820d12ddd24b1386
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400486"
---
# <a name="imaxabs"></a>imaxabs

Vypočítá absolutní hodnotu celé jakékoli velikosti.

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

**Imaxabs –** funkce vrátí absolutní hodnotu argumentu. Neexistuje žádný návratový chyby.

> [!NOTE]
> Protože rozsahu záporné celých čísel, které může být reprezentovaný pomocí **intmax_t** je větší než je rozsah kladná celá čísla, které může být reprezentován, je možné poskytnout argumentu **imaxabs –** který nelze převést. Pokud se absolutní hodnota argumentu nemůže být reprezentovaná návratový typ, chování **imaxabs –** není definován.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**imaxabs**|\<inttypes.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
