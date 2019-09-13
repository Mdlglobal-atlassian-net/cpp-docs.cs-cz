---
title: _fcvt
ms.date: 04/05/2018
api_name:
- _fcvt
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
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: a90f8510e734c8459867d323eccccc75e94983d1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941317"
---
# <a name="_fcvt"></a>_fcvt

Převede číslo s plovoucí desetinnou čárkou na řetězec. K dispozici je bezpečnější verze této funkce; viz [_fcvt_s](fcvt-s.md).

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
Číslo, které má být převedeno.

*výpočtu*<br/>
Počet číslic za desetinnou čárkou.

*18.12*<br/>
Ukazatel na uloženou pozici desetinných míst.

*sign*<br/>
Ukazatel na uložený indikátor znaménka.

## <a name="return-value"></a>Návratová hodnota

**_fcvt** vrací ukazatel na řetězec číslic a **hodnotu null** při chybě.

## <a name="remarks"></a>Poznámky

Funkce **_fcvt** převede číslo s plovoucí desetinnou čárkou na řetězec znaků zakončený hodnotou null. Parametr *Value* je číslo s plovoucí desetinnou čárkou, které má být převedeno. **_fcvt** ukládá číslice *hodnoty* jako řetězec a připojí znak null (' \ 0 '). Parametr *Count* určuje počet číslic, které mají být uloženy za desetinnou čárkou. Nadbytečné číslice se zaokrouhlují na *počty* míst. Pokud je k dispozici *méně než číslice* typu přesnosti, je řetězec doplněn nulami.

Celkový počet číslic vrácených funkcí **_fcvt** nebude přesáhnout **_CVTBUFSIZE**.

V řetězci jsou uloženy pouze číslice. Pozice desetinné čárky a znaménko *hodnoty* lze získat z *dec* a podepsat po volání. Parametr *dec* odkazuje na celočíselnou hodnotu; Tato celočíselná hodnota udává pozici desetinné čárky vůči začátku řetězce. Nula nebo záporná celočíselná hodnota značí, že desetinná čárka leží vlevo od první číslice. *Symbol* parametru odkazuje na celé číslo označující znaménko *hodnoty*. Celé číslo je nastavené na 0, pokud je *hodnota* kladná a je nastavená na nenulové číslo, pokud je *hodnota* záporná.

Rozdíl mezi **_ecvt** a **_fcvt** je ve výkladu parametru *Count* . **_ecvt** interpretuje *čítač* jako celkový počet číslic ve výstupním řetězci, zatímco **_fcvt** interpretuje *počet číslic* za desetinnou čárkou.

**_ecvt** a **_fcvt** používají pro převod jednu staticky přidělenou vyrovnávací paměť. Každé volání jedné z těchto rutin zničí výsledky předchozího volání.

Tato funkce ověří své parametry. Pokud má parametr *dec* nebo *Sign* **hodnotu null**nebo je *počet* 0, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a vrátí **hodnotu null** .

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
