---
title: _fcvt
ms.date: 4/2/2020
api_name:
- _fcvt
- _o__fcvt
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
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: a017ed58b962520793d5b10b088793dbc9b8a83d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347419"
---
# <a name="_fcvt"></a>_fcvt

Převede číslo s plovoucí desetinnou tácem na řetězec. K dispozici je bezpečnější verze této funkce. viz [_fcvt_s](fcvt-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_fcvt(
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
Počet číslic za desetinnou čárkou.

*dec*<br/>
Ukazatel na uloženou pozici desetinné čárky.

*Znamení*<br/>
Ukazatel na indikátor uloženého znaku.

## <a name="return-value"></a>Návratová hodnota

**_fcvt** vrátí ukazatel na řetězec číslic, **NULL** na chybu.

## <a name="remarks"></a>Poznámky

Funkce **_fcvt** převede číslo s plovoucí desetinnou hodnotou na řetězec znaků ukončený nulou. Parametr *value* je číslo s plovoucí desetinnou tázkem, které má být převedeno. **_fcvt** uloží číslice *hodnoty* jako řetězec a připojí nulový znak (\0). Parametr *count* určuje počet číslic, které mají být uloženy za desetinnou čárkou. Přebytečné číslice jsou zaokrouhleny tak, aby *počítaly* místa. Pokud je méně než *počet* číslic přesnosti, řetězec je doplněn nulami.

Celkový počet číslic vrácených **_fcvt** nepřesáhne **_CVTBUFSIZE**.

V řetězci jsou uloženy pouze číslice. Pozice desetinné čárky a znaménko *hodnoty* lze získat z *dec* a podepsat po volání. Parametr *dec* odkazuje na hodnotu celéčíslo; tato celá hodnota udává pozici desetinné čárky vzhledem k začátku řetězce. Hodnota nula nebo záporné celé číslo označuje, že desetinná čárka leží nalevo od první číslice. *Znaménko* parametru odkazuje na celé číslo označující znaménko *hodnoty*. Celé číslo je nastaveno na *hodnotu* 0, pokud je hodnota kladná, a pokud je *hodnota* záporná, je nastaveno na nenulové číslo.

Rozdíl mezi **_ecvt** a **_fcvt** je v interpretaci parametru *count.* **_ecvt** interpretuje *počet* jako celkový počet číslic ve výstupním řetězci, zatímco **_fcvt** interpretuje *počet* číslic za desetinnou čárkou.

**_ecvt** a **_fcvt** pro převod použít jednu staticky přidělenou vyrovnávací paměť. Každé volání jedné z těchto rutin zničí výsledky předchozího volání.

Tato funkce ověřuje její parametry. Pokud *dec* nebo *sign* je **NULL**nebo *počet* je 0, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, **errno** je nastavena na **EINVAL** a **null** je vrácena.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fcvt.c
// compile with: /W3
// This program converts the constant
// 3.1415926535 to a string and sets the pointer
// buffer to point to that string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int  decimal, sign;
   char *buffer;
   double source = 3.1415926535;

   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996
   // Note: _fcvt is deprecated; consider using _fcvt_s instead
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",
            source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
