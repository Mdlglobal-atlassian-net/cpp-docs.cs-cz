---
title: _fcvt – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fefe9bbfc1904847af5594a4d663b1eb8299fc9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fcvt"></a>_fcvt

Převede dvě desetinná čísla na řetězec. Bezpečnější verze této funkce je k dispozici. v tématu [_fcvt_s –](fcvt-s.md).

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
Ukazatel na uložené pozici desetinné čárky.

*sign*<br/>
Ukazatel na uložené přihlašovací indikátoru.

## <a name="return-value"></a>Návratová hodnota

**_fcvt –** vrací ukazatel na řetězec číslic, NULL v případě chyby.

## <a name="remarks"></a>Poznámky

**_Fcvt –** funkce převede dvě desetinná čísla na řetězec znaků ukončený hodnotou null. *Hodnotu* parametr je číslo s plovoucí desetinnou čárkou má být převeden. **_fcvt –** ukládá číslice z *hodnotu* jako řetězec a připojí znak hodnoty null ('\0'). *Počet* parametr určuje počet číslic ukládaly za desetinnou čárkou. Jsou nadbytečné číslic zaokrouhlen *počet* umístí. Pokud máte méně než *počet* platných číslic, řetězec je doplněno nulami.

Celkový počet číslic vrácený **_fcvt –** nesmí překročit **_CVTBUFSIZE**.

Pouze číslice jsou uloženy v řetězci. Pozice desetinné čárky a znaménko *hodnotu* lze získat z *dec* a přihlásit po volání. *Dec* parametr odkazuje na celočíselnou hodnotu; uvádí tato hodnota celé číslo pozice od desetinné čárky s ohledem na začátku řetězce. Nula nebo záporná celočíselná hodnota označuje, zda desetinné čárky je nalevo od první číslice. Parametr *přihlašovací* odkazuje na celé číslo udávající znaménko *hodnotu*. Celé číslo nastavena na 0, pokud *hodnotu* kladné a je nastavená na nenulové číslo Pokud *hodnota* je záporná.

Rozdíl mezi **_ecvt –** a **_fcvt –** je při interpretaci *počet* parametr. **_ecvt –** interpretuje *počet* jako celkový počet číslic do výstupního řetězce, zatímco **_fcvt –** interpretuje *počet* jako počet číslic za desetinné čárky.

**_ecvt –** a **_fcvt –** ke konverzi použijte jeden staticky přidělené vyrovnávací paměti. Každé volání na jednu z těchto rutin zničí výsledky z předchozího volání.

Tato funkce ověří jeho parametry. Pokud *dec* nebo *přihlašovací* má hodnotu NULL, nebo *počet* je 0, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a vrátí se hodnota NULL.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
