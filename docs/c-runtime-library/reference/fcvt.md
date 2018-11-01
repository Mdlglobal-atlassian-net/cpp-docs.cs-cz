---
title: _fcvt
ms.date: 04/05/2018
apiname:
- _fcvt
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
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: ae9323e3bb629fd61b35a8c844b00bfcc73235bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662056"
---
# <a name="fcvt"></a>_fcvt

Převede číslo s plovoucí desetinnou čárkou na řetězec. Bezpečnější verze této funkce je k dispozici. Zobrazit [_fcvt_s –](fcvt-s.md).

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

*value*<br/>
Číslo, které má být převeden.

*Počet*<br/>
Počet číslic za desetinnou čárkou.

*DEC*<br/>
Ukazatel pozice uložené desetinné čárky.

*sign*<br/>
Ukazatel na ukazatel uložené přihlašování.

## <a name="return-value"></a>Návratová hodnota

**_fcvt –** vrací ukazatel na řetězec číslic, **NULL** při chybě.

## <a name="remarks"></a>Poznámky

**_Fcvt –** funkce převede číslo s plovoucí desetinnou čárkou na řetězec znaků zakončené znakem null. *Hodnotu* parametru je číslo s plovoucí desetinnou čárkou má být převeden. **_fcvt –** ukládá na číslice *hodnota* jako řetězec a připojí znak null ('\0'). *Počet* parametr určuje počet číslic, které mají být uloženy za desetinnou čárkou. Jsou nadbytečné číslic zaokrouhlena *počet* umístí. Pokud jsou kratší než *počet* číslicemi přesnosti, řetězec je doplněny nulami.

Celkový počet číslic vrácený **_fcvt –** nesmí překročit **_CVTBUFSIZE**.

Pouze číslice jsou uloženy v řetězci. Pozice desetinné čárky a znaménko *hodnotu* můžete získat *dec* a přihlašování po volání. *Dec* parametr odkazuje na celočíselnou hodnotu; poskytuje tuto hodnotu celého čísla pozici od desetinné čárky s ohledem na začátku řetězce. Nula nebo záporné celé číslo označuje, zda desetinné čárky je nalevo od první číslice. Parametr *přihlašování* odkazuje na celé číslo označující znaménko *hodnota*. Celé číslo je nastavena na 0, pokud *hodnotu* kladné a nastaven na nenulovou hodnotu, počet Pokud *hodnotu* je záporný.

Rozdíl mezi **_ecvt –** a **_fcvt –** probíhá vyhodnocení *počet* parametru. **_ecvt –** interpretuje *počet* jako celkový počet číslic ve výstupním řetězci, zatímco **_fcvt –** interpretuje *počet* jako počet číslic za desetinné čárky.

**_ecvt –** a **_fcvt –** pomocí jedné staticky přidělenou vyrovnávací paměti pro převod. Každé volání některé z těchto rutin zničí výsledků z předchozího volání.

Tato funkce ověřuje své parametry. Pokud *dec* nebo *přihlašování* je **NULL**, nebo *počet* je 0, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a **NULL** je vrácena.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
