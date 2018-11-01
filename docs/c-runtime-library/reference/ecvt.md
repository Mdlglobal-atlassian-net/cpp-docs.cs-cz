---
title: _ecvt
ms.date: 04/05/2018
apiname:
- _ecvt
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
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 36c9cb2e8cd9eb4dd67bb91e9e4dbd36d8d1fc8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605723"
---
# <a name="ecvt"></a>_ecvt

Převede **double** číslo na řetězec. Bezpečnější verze této funkce je k dispozici. Zobrazit [_ecvt_s –](ecvt-s.md).

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

*value*<br/>
Číslo, které má být převeden.

*Počet*<br/>
Počet číslic, které jsou uložené.

*DEC*<br/>
Pozice uložené desetinné čárky.

*sign*<br/>
Znak převedený čísla.

## <a name="return-value"></a>Návratová hodnota

**_ecvt –** vrací ukazatel na řetězec číslic; **NULL** Pokud došlo k chybě.

## <a name="remarks"></a>Poznámky

**_Ecvt –** funkce převede číslo s plovoucí desetinnou čárkou na řetězec znaků. *Hodnotu* parametru je číslo s plovoucí desetinnou čárkou má být převeden. Tato funkce ukládá až *počet* číslic *hodnota* jako řetězec a připojí znak null ('\0'). Pokud počet číslic v *hodnotu* překračuje *počet*, poloměr zaoblení číslice nižšího řádu. Pokud jsou kratší než *počet* číslic, řetězec je doplněny nulami.

Celkový počet číslic vrácený **_ecvt –** nesmí překročit **_CVTBUFSIZE**.

Pouze číslice jsou uloženy v řetězci. Pozice desetinné čárky a znaménko *hodnotu* můžete získat *dec* a *přihlašování* po volání. *Dec* parametr odkazuje na celočíselnou hodnotu poskytuje pozici od desetinné čárky s ohledem na začátku řetězce. Hodnota 0 nebo záporné celé číslo označuje, že desetinné čárky je nalevo od první číslice. *Přihlašování* parametr odkazuje na celé číslo označující znaménko převedený číslo. Pokud je hodnota celého čísla 0, je kladné číslo. V opačném případě je číslo záporné.

Rozdíl mezi **_ecvt –** a **_fcvt –** probíhá vyhodnocení *počet* parametru. **_ecvt –** interpretuje *počet* jako celkový počet číslic ve výstupním řetězci, zatímco **_fcvt –** interpretuje *počet* jako počet číslic za desetinné čárky.

**_ecvt –** a **_fcvt –** pomocí jedné staticky přidělenou vyrovnávací paměti pro převod. Každé volání některé z těchto rutin ničí výsledek předchozího volání.

Tato funkce ověřuje své parametry. Pokud *dec* nebo *přihlašování* je **NULL**, nebo *počet* je 0, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a **NULL** je vrácena.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
