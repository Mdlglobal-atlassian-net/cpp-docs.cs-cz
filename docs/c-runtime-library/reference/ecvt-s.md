---
title: _ecvt_s – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ecvt_s
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
- ecvt_s
- _ecvt_s
dev_langs:
- C++
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 623d12bb515794a1d57b5a18e0e93e70d50a6812
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404357"
---
# <a name="ecvts"></a>_ecvt_s

Převede **dvojité** čísel na řetězec. Toto je verze [_ecvt –](ecvt.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _ecvt_s(
   char * _Buffer,
   size_t _SizeInBytes,
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
);
template <size_t size>
errno_t _ecvt_s(
   char (&_Buffer)[size],
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
); // C++ only
```

### <a name="parameters"></a>Parametry

*_Buffer*<br/>
Naplní se má ukazatel na řetězec číslic, výsledek převodu.

*_SizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtech.

*_Value*<br/>
Číslo, které má být převeden.

*_Count*<br/>
Počet číslic, které jsou uložené.

*_Dec*<br/>
Uložené pozice desetinné čárky.

*_Sign*<br/>
Znak převedený číslo.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v Errno.h. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

V případě neplatný parametr, jak je uvedeno v následující tabulce, tato funkce volá neplatný parametr obslužnou rutinu, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **einval –**.

### <a name="error-conditions"></a>Chybové stavy

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|Návratová hodnota|Hodnota v *vyrovnávací paměti*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**HODNOTU NULL**|všechny|všechny|všechny|všechny|všechny|**EINVAL –**|Nedojde ke změně.|
|Není **NULL** (odkazuje na platný paměti)|<=0|všechny|všechny|všechny|všechny|**EINVAL –**|Nedojde ke změně.|
|všechny|všechny|všechny|všechny|**HODNOTU NULL**|všechny|**EINVAL –**|Nedojde ke změně.|
|všechny|všechny|všechny|všechny|všechny|**HODNOTU NULL**|**EINVAL –**|Nedojde ke změně.|

## <a name="security-issues"></a>Problémy se zabezpečením

**_ecvt_s –** může generovat narušení přístupu, pokud *vyrovnávací paměti* neodkazuje na platný paměti a není **NULL**.

## <a name="remarks"></a>Poznámky

**_Ecvt_s –** funkce převede na řetězec znaků číslo s plovoucí desetinnou čárkou. *_Value* parametr je číslo s plovoucí desetinnou čárkou má být převeden. Tato funkce ukládá až *počet* číslice *_Value* jako řetězec a připojí znak hodnoty null ('\0'). Pokud počet číslic v *_Value* překračuje *_Count*, se zaokrouhlí na nejnižší číslici. Pokud máte méně než *počet* číslic, řetězec je doplněno nulami.

Pouze číslice jsou uloženy v řetězci. Pozice desetinné čárky a znaménko *_Value* lze získat z *_Dec* a *_Sign* po volání. *_Dec* parametr odkazuje na celočíselnou hodnotu poskytnutí pozici od desetinné čárky s ohledem na začátku řetězce. Hodnota 0 nebo záporné celé číslo označuje, zda desetinné čárky je nalevo od první číslice. *_Sign* parametr odkazuje na celé číslo, které označuje znak převedený číslo. Pokud je hodnota celé číslo 0, je kladné číslo. Jinak je číslo záporné.

Vyrovnávací paměť délky **_CVTBUFSIZE** je dostatečná pro všechny hodnoty s plovoucí desetinnou čárkou.

Rozdíl mezi **_ecvt_s –** a **_fcvt_s –** je při interpretaci *_Count* parametr. **_ecvt_s –** interpretuje *_Count* jako celkový počet číslic do výstupního řetězce, zatímco **_fcvt_s –** interpretuje *_Count* jako počet číslic po desetinné čárky.

V jazyce C++ pomocí této funkce se zjednodušilo díky šabloně přetížení; přetížení lze odvodit délka vyrovnávací paměti automaticky, takže není nutné zadat argument velikost. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve doplní vyrovnávací paměti s 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// ecvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( )
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_ecvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 12000
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
