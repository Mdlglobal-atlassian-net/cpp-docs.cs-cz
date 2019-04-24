---
title: _gcvt
ms.date: 04/05/2018
apiname:
- _gcvt
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _gcvt
helpviewer_keywords:
- _gcvt function
- _CVTBUFSIZE
- gcvt function
- floating-point functions, converting number to string
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 5761411e-c06b-409a-912f-810fe7f4bcb5
ms.openlocfilehash: 9cf966b455af601d09b4444a5c590e305a6681c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332246"
---
# <a name="gcvt"></a>_gcvt

Převede hodnotu s plovoucí desetinnou čárkou na řetězec, který je uložený ve vyrovnávací paměti. Bezpečnější verze této funkce je k dispozici. Zobrazit [_gcvt_s –](gcvt-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_gcvt(
   double value,
   int digits,
   char *buffer
);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Hodnota k převedení.

*číslice*<br/>
Počet platných číslic, které jsou uložené.

*Vyrovnávací paměti*<br/>
Umístění úložiště pro výsledek.

## <a name="return-value"></a>Návratová hodnota

**_gcvt –** vrací ukazatel na řetězec číslic.

## <a name="remarks"></a>Poznámky

**_Gcvt –** funkce převede plovoucí desetinné čárky *hodnotu* na řetězec znaků (která zahrnuje desetinné čárky a možné podepsat bajtů) a uloží řetězec v *vyrovnávací paměti*. *Vyrovnávací paměti* by měl být dostatečně velký, aby odpovídala převedená hodnota plus ukončujícího znaku null, která se automaticky připojí. Pokud vyrovnávací paměť o velikosti *číslic* + 1 se používá, funkce přepíše konce vyrovnávací paměti. Je to proto převedený řetězec obsahuje desetinnou čárkou a může obsahovat znak a exponentu informace. Neexistuje žádné ustanovení přetečení. **_gcvt –** pokusí vytvořit *číslic* číslic ve formátu desetinného čísla. V případě nedostupnosti vznikne *číslic* číslic v exponenciálním formátu. Během převodu může potlačit koncovými nulami.

A *vyrovnávací paměti* délky **_CVTBUFSIZE** je dostatečná pro všechny plovoucí desetinnou čárkou.

Tato funkce ověřuje své parametry. Pokud *vyrovnávací paměti* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí **NULL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_gcvt**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_gcvt.c
// compile with: /W3
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int main( void )
{
   char buffer[_CVTBUFSIZE];
   double value = -1234567890.123;
   printf( "The following numbers were converted by _gcvt(value,12,buffer):\n" );
   _gcvt( value, 12, buffer ); // C4996
   // Note: _gcvt is deprecated; consider using _gcvt_s instead
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value *= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value *= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value *= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );

   printf( "\n" );
   value = -12.34567890123;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value /= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value /= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value /= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
}
```

```Output
The following numbers were converted by _gcvt(value,12,buffer):
buffer: '-1234567890.12' (14 chars)
buffer: '-12345678901.2' (14 chars)
buffer: '-123456789012' (13 chars)
buffer: '-1.23456789012e+012' (19 chars)

buffer: '-12.3456789012' (14 chars)
buffer: '-1.23456789012' (14 chars)
buffer: '-0.123456789012' (15 chars)
buffer: '-1.23456789012e-002' (19 chars)
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
