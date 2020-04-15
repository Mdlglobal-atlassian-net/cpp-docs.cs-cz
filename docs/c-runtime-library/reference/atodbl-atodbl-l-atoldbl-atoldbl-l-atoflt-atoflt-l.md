---
title: _atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l
ms.date: 4/2/2020
api_name:
- _atoldbl
- _atoldbl_l
- _atodbl
- _atoflt
- _atoflt_l
- _atodbl_l
- _o__atodbl
- _o__atodbl_l
- _o__atoflt
- _o__atoflt_l
- _o__atoldbl
- _o__atoldbl_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _atoflt
- _atoflt_l
- atodbl_l
- atoflt_l
- _atoldbl
- _atoldbl_l
- atodbl
- _atodbl_l
- atoldbl
- atoflt
- atoldbl_l
- _atodbl
helpviewer_keywords:
- _atodbl function
- _atoldbl_l function
- atoflt function
- atoflt_l function
- atoldbl function
- _atoldbl function
- atodbl_l function
- _atoflt_l function
- atoldbl_l function
- atodbl function
- string conversion, to floating point values
- _atoflt function
- _atodbl_l function
ms.assetid: 2d2530f4-4bd4-42e3-8083-f2d2fbc8432a
ms.openlocfilehash: 5f304fd163c2ba1c57a4daee8c2a3307d8ba870a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348954"
---
# <a name="_atodbl-_atodbl_l-_atoldbl-_atoldbl_l-_atoflt-_atoflt_l"></a>_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l

Převede řetězec na double (**_atodbl**), long double (**_atoldbl**) nebo float (**_atoflt**).

## <a name="syntax"></a>Syntaxe

```C
int _atodbl( _CRT_DOUBLE * value, char * str );
int _atodbl_l ( _CRT_DOUBLE * value, char * str, locale_t locale );
int _atoldbl( _LDOUBLE * value, char * str );
int _atoldbl_l ( _LDOUBLE * value, char * str, locale_t locale );
int _atoflt( _CRT_FLOAT * value, const char * str );
int _atoflt_l( _CRT_FLOAT * value, const char * str, locale_t locale );
```

### <a name="parameters"></a>Parametry

*Hodnotu*<br/>
Double, long double nebo float hodnota, která je vytvořena převodem řetězce na hodnotu s plovoucí desetinnou tálicí. Tyto hodnoty jsou zabaleny do struktury.

*Str*<br/>
Řetězec, který má být analyzován převést na hodnotu s plovoucí desetinnou tálicí.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je úspěšná. Možné kódy chyb jsou **_UNDERFLOW** nebo **_OVERFLOW** \<, které jsou definovány v souboru záhlaví math.h>.

## <a name="remarks"></a>Poznámky

Tyto funkce převést řetězec na hodnotu s plovoucí desetinnou hodnotou. Rozdíl mezi tyto funkce a **atof** rodiny funkcí je, že tyto funkce negenerují kód s plovoucí desetinnou čárkou a nezpůsobují výjimky hardwaru. Místo toho jsou chybové stavy hlášeny jako kódy chyb.

Pokud řetězec nemá platný výklad jako hodnotu s plovoucí desetinnou hodnotou, *hodnota* je nastavena na nulu a vrácená hodnota je nula.

Verze těchto funkcí, které mají **_l** příponu jsou identické verze, které nemají příponu, s tím rozdílem, že používají parametr *národního prostředí,* který je předán v namísto aktuálního národního prostředí vlákna.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutiny|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_atodbl** **_atoldbl** **_atoflt**<br /><br /> **_atodbl_l**, **_atoldbl_l** **_atoflt_l**|\<stdlib.h>|

## <a name="example"></a>Příklad

```C
// crt_atodbl.c
// Uses _atodbl to convert a string to a double precision
// floating point value.

#include <stdlib.h>
#include <stdio.h>

int main()
{
   char str1[256] = "3.141592654";
   char abc[256] = "abc";
   char oflow[256] = "1.0E+5000";
   _CRT_DOUBLE dblval;
   _CRT_FLOAT fltval;
   int retval;

   retval = _atodbl(&dblval, str1);

   printf("Double value: %lf\n", dblval.x);
   printf("Return value: %d\n\n", retval);

   retval = _atoflt(&fltval, str1);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   // A non-floating point value: returns 0.
   retval = _atoflt(&fltval, abc);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   // Overflow.
   retval = _atoflt(&fltval, oflow);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   return 0;
}
```

```Output
Double value: 3.141593
Return value: 0

Float value: 3.141593
Return value: 0

Float value: 0.000000
Return value: 0

Float value: inf
Return value: 3
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
