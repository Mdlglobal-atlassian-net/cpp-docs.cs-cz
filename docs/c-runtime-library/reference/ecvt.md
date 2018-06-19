---
title: _ecvt – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63514db5abe0a7cd531590dd419aa4b5931e7729
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450960"
---
# <a name="ecvt"></a>_ecvt

Převede **dvojité** čísel na řetězec. Bezpečnější verze této funkce je k dispozici. v tématu [_ecvt_s –](ecvt-s.md).

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
Uložené pozice desetinné čárky.

*sign*<br/>
Znak převedený číslo.

## <a name="return-value"></a>Návratová hodnota

**_ecvt –** vrací ukazatel na řetězec číslic; **NULL** Pokud došlo k chybě.

## <a name="remarks"></a>Poznámky

**_Ecvt –** funkce převede na řetězec znaků číslo s plovoucí desetinnou čárkou. *Hodnotu* parametr je číslo s plovoucí desetinnou čárkou má být převeden. Tato funkce ukládá až *počet* číslice *hodnotu* jako řetězec a připojí znak hodnoty null ('\0'). Pokud počet číslic v *hodnotu* překračuje *počet*, se zaokrouhlí na nejnižší číslici. Pokud máte méně než *počet* číslic, řetězec je doplněno nulami.

Celkový počet číslic vrácený **_ecvt –** nesmí překročit **_CVTBUFSIZE**.

Pouze číslice jsou uloženy v řetězci. Pozice desetinné čárky a znaménko *hodnotu* lze získat z *dec* a *přihlašovací* po volání. *Dec* parametr odkazuje na celočíselnou hodnotu poskytnutí pozici od desetinné čárky s ohledem na začátku řetězce. Hodnota 0 nebo záporné celé číslo označuje, zda desetinné čárky je nalevo od první číslice. *Přihlašovací* parametr odkazuje na celé číslo, které označuje znak převedený číslo. Pokud je hodnota celé číslo 0, je kladné číslo. Jinak je číslo záporné.

Rozdíl mezi **_ecvt –** a **_fcvt –** je při interpretaci *počet* parametr. **_ecvt –** interpretuje *počet* jako celkový počet číslic do výstupního řetězce, zatímco **_fcvt –** interpretuje *počet* jako počet číslic za desetinné čárky.

**_ecvt –** a **_fcvt –** ke konverzi použijte jeden staticky přidělené vyrovnávací paměti. Každé volání na jednu z těchto rutin zničí výsledek předchozí volání.

Tato funkce ověří jeho parametry. Pokud *dec* nebo *přihlašovací* je **NULL**, nebo *počet* je 0, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a **NULL** je vrácen.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
