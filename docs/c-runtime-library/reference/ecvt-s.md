---
title: _ecvt_s
ms.date: 04/05/2018
api_name:
- _ecvt_s
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
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: c50200d16a5e542c247d1c85f8c104381af4a883
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937718"
---
# <a name="_ecvt_s"></a>_ecvt_s

Převede **dvojité** číslo na řetězec. Jedná se o verzi [_ecvt](ecvt.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Vyplněný ukazatelem na řetězec číslic, výsledek převodu.

*_SizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtech.

*_Value*<br/>
Číslo, které má být převedeno.

*_Count*<br/>
Počet uložených číslic.

*_Dec*<br/>
Pozice uloženého desetinného místa.

*_Sign*<br/>
Znaménko převedeného čísla.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Návratová hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v errno. h. Další informace najdete v tématech [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

V případě neplatného parametru, jak je uvedeno v následující tabulce, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

### <a name="error-conditions"></a>Chybové stavy

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|Návratová hodnota|Hodnota v *bufferu*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**NULL**|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|**EINVAL**|Nezměněno.|
|Není **null** (ukazuje na platnou paměť)|<=0|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|**EINVAL**|Nezměněno.|
|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|**NULL**|Jakýmikoli|**EINVAL**|Nezměněno.|
|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|**NULL**|**EINVAL**|Nezměněno.|

## <a name="security-issues"></a>Problémy se zabezpečením

**_ecvt_s** může vygenerovat porušení přístupu, pokud *vyrovnávací paměť* neukazuje na platnou paměť a není **null**.

## <a name="remarks"></a>Poznámky

Funkce **_ecvt_s** převede číslo s plovoucí desetinnou čárkou na řetězec znaků. Parametr *_Value* je číslo s plovoucí desetinnou čárkou, které má být převedeno. Tato funkce ukládá až do *počtu* číslic *_Value* jako řetězec a připojí znak null (' \ 0 '). Pokud počet číslic v *_Value* překračuje *_Count*, je číslice dolního řádu zaokrouhlena. Pokud jsou k dispozici méně než číslice *Count* , je řetězec doplněn nulami.

V řetězci jsou uloženy pouze číslice. Pozice desetinné čárky a znaménko *_Value* lze získat z *_Dec* a *_Sign* po volání. Parametr *_Dec* odkazuje na celočíselnou hodnotu, která dává pozici desetinné čárky s ohledem na začátek řetězce. Hodnota 0 nebo záporné celé číslo označuje, že desetinná čárka leží vlevo od první číslice. Parametr *_Sign* odkazuje na celé číslo, které označuje znaménko převedeného čísla. Pokud je celočíselná hodnota 0, je číslo kladné. V opačném případě je číslo záporné.

Vyrovnávací paměť s délkou **_CVTBUFSIZE** je dostačující pro libovolnou hodnotu s plovoucí desetinnou čárkou.

Rozdíl mezi **_ecvt_s** a **_fcvt_s** je ve výkladu parametru *_Count* . **_ecvt_s** interpretuje *_Count* jako celkový počet číslic ve výstupním řetězci, zatímco **_fcvt_s** interpretuje *_Count* jako počet číslic za desetinnou čárkou.

V C++systému je použití této funkce zjednodušené přetížením šablony; přetížení může odvodit délku vyrovnávací paměti automaticky a eliminuje nutnost zadat argument Size. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve vyplní vyrovnávací paměť pomocí 0xFD. Pokud chcete toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
