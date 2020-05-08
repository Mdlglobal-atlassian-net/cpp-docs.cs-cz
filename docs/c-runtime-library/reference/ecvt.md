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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 9e02be690b257842c49166e18cf551c540190388
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915097"
---
# <a name="_ecvt"></a>_ecvt

Převede **dvojité** číslo na řetězec. K dispozici je bezpečnější verze této funkce; viz [_ecvt_s](ecvt-s.md).

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

*osa*<br/>
Číslo, které má být převedeno.

*výpočtu*<br/>
Počet uložených číslic.

*dec*<br/>
Pozice uloženého desetinného místa.

*osobě*<br/>
Znaménko převedeného čísla.

## <a name="return-value"></a>Návratová hodnota

**_ecvt** vrací ukazatel na řetězec číslic; **Hodnota null** , pokud došlo k chybě.

## <a name="remarks"></a>Poznámky

Funkce **_ecvt** převede číslo s plovoucí desetinnou čárkou na řetězec znaků. Parametr *Value* je číslo s plovoucí desetinnou čárkou, které má být převedeno. Tato funkce ukládá až do *počtu* číslic *hodnoty* jako řetězec a připojí znak null (' \ 0 '). Je-li počet číslic v *hodnotě* větší než *počet*, zaokrouhlí se číslice s nižším pořadím. Pokud jsou k dispozici méně než číslice *Count* , je řetězec doplněn nulami.

Celkový počet číslic vrácených **_ecvt** nebude přesáhnout **_CVTBUFSIZE**.

V řetězci jsou uloženy pouze číslice. Pozice desetinné čárky a znaménko *hodnoty* lze získat z *dec* a *podepsat* po volání. Parametr *dec* odkazuje na celočíselnou hodnotu, která dává pozici desetinné čárky s ohledem na začátek řetězce. Hodnota 0 nebo záporné celé číslo označuje, že desetinná čárka leží vlevo od první číslice. Parametr *Sign* odkazuje na celé číslo, které označuje znaménko převedené číslo. Pokud je celočíselná hodnota 0, je číslo kladné. V opačném případě je číslo záporné.

Rozdíl mezi **_ecvt** a **_fcvt** je ve výkladu parametru *Count* . **_ecvt** interpretuje *počítání* jako celkový počet číslic ve výstupním řetězci, zatímco **_fcvt** interpretuje *počet číslic* za desetinnou čárkou.

**_ecvt** a **_fcvt** použít jednu staticky přidělenou vyrovnávací paměť pro převod. Každé volání jedné z těchto rutin zničí výsledek předchozího volání.

Tato funkce ověří své parametry. Pokud má parametr *dec* nebo *Sign* **hodnotu null**nebo je *počet* 0, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a vrátí **hodnotu null** .

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_ecvt**|\<Stdlib. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
