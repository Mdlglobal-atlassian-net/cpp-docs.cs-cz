---
title: _ecvt
ms.date: 4/2/2020
api_name:
- _ecvt
- _o__ecvt
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
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 5e1760d5c68e650f6fbf44866d4e368b9d6233b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348027"
---
# <a name="_ecvt"></a>_ecvt

Převede **dvojité** číslo na řetězec. K dispozici je bezpečnější verze této funkce. viz [_ecvt_s](ecvt-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_ecvt(
   double value,
   int count,
   int *dec,
   int *sign
);
```

### <a name="parameters"></a>Parametry

*Hodnotu*<br/>
Číslo, které má být převedeno.

*Počet*<br/>
Počet uložených číslic.

*dec*<br/>
Uložená pozice desetinných bodů.

*Znamení*<br/>
Znaménko převedeného čísla.

## <a name="return-value"></a>Návratová hodnota

**_ecvt** vrátí ukazatel na řetězec číslic; **Null,** pokud došlo k chybě.

## <a name="remarks"></a>Poznámky

Funkce **_ecvt** převede číslo s plovoucí desetinnou tácem na řetězec znaků. Parametr *value* je číslo s plovoucí desetinnou tázkem, které má být převedeno. Tato funkce ukládá až *do počtu* číslic *hodnoty* jako řetězec a připojí prázdný znak (\0'). Pokud počet číslic v *hodnotě* překročí *počet*, je číslice nižšího řádu zaokrouhlena. Pokud je méně než *počet* číslic, řetězec je doplněn nulami.

Celkový počet číslic vrácených **_ecvt** nepřesáhne **_CVTBUFSIZE**.

V řetězci jsou uloženy pouze číslice. Pozice desetinné čárky a znaménko *hodnoty* lze získat z *dec* a *podepsat* po volání. Parametr *dec* odkazuje na celou hodnotu, která udává pozici desetinné čárky vzhledem k začátku řetězce. Hodnota 0 nebo záporné celé číslo označuje, že desetinná čárka leží nalevo od první číslice. Parametr *znaménko* odkazuje na celé číslo, které označuje znaménko převedeného čísla. Pokud je celá hodnota 0, číslo je kladné. V opačném případě je číslo záporné.

Rozdíl mezi **_ecvt** a **_fcvt** je v interpretaci parametru *count.* **_ecvt** interpretuje *počet* jako celkový počet číslic ve výstupním řetězci, zatímco **_fcvt** interpretuje *počet* číslic za desetinnou čárkou.

**_ecvt** a **_fcvt** pro převod použít jednu staticky přidělenou vyrovnávací paměť. Každé volání jedné z těchto rutin zničí výsledek předchozího volání.

Tato funkce ověřuje její parametry. Pokud *dec* nebo *sign* je **NULL**nebo *počet* je 0, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, **errno** je nastavena na **EINVAL** a **null** je vrácena.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_ecvt.c
// compile with: /W3
// This program uses _ecvt to convert a
// floating-point number to a character string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int     decimal,   sign;
   char    *buffer;
   int     precision = 10;
   double  source = 3.1415926535;

   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996
   // Note: _ecvt is deprecated; consider using _ecvt_s instead
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",
           source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
