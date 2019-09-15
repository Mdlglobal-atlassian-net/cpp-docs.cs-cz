---
title: _gcvt
ms.date: 04/05/2018
api_name:
- _gcvt
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3618f5571275783131c74c89f29218f89023f70e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956106"
---
# <a name="_gcvt"></a>_gcvt

Převede hodnotu s plovoucí desetinnou čárkou na řetězec, který je uložen ve vyrovnávací paměti. K dispozici je bezpečnější verze této funkce; viz [_gcvt_s](gcvt-s.md).

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
Hodnota, která má být převedena.

*znak*<br/>
Počet uložených platných číslic.

*vyrovnávací paměti*<br/>
Umístění úložiště pro výsledek.

## <a name="return-value"></a>Návratová hodnota

**_gcvt** vrací ukazatel na řetězec číslic.

## <a name="remarks"></a>Poznámky

Funkce **_gcvt** převede *hodnotu* s plovoucí desetinnou čárkou na řetězec znaků (který obsahuje desetinnou čárku a možné znak pro podepsání) a uloží řetězec do *vyrovnávací paměti*. *Vyrovnávací paměť* by měla být dostatečně velká, aby odpovídala převedené hodnotě, a ukončujícímu znaku null, který je automaticky připojen. Pokud je použita velikost vyrovnávací *paměti + 1* , funkce přepíše konec vyrovnávací paměti. Důvodem je, že převedený řetězec obsahuje desetinnou čárku a může obsahovat informace o znaménku a exponentu. Neexistuje žádné zajištění pro přetečení. **_gcvt** se pokusí *vydávat číslice číslic v* desítkovém formátu. Pokud to nemůže *, vytvoří číslice číslice v* exponenciálním formátu. Koncové nuly lze v převodu potlačit.

*Vyrovnávací paměť* s délkou **_CVTBUFSIZE** je dostačující pro všechny hodnoty s plovoucí desetinnou čárkou.

Tato funkce ověří své parametry. Pokud má *vyrovnávací paměť* **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **hodnotu null**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_gcvt**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
