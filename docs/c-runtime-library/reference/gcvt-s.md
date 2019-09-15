---
title: _gcvt_s
ms.date: 04/05/2018
api_name:
- _gcvt_s
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
- _gcvt_s
- gcvt_s
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
ms.openlocfilehash: 7ecb6fe105d8a976979f91d38c9e536b10989310
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956109"
---
# <a name="_gcvt_s"></a>_gcvt_s

Převede hodnotu s plovoucí desetinnou čárkou na řetězec. Jedná se o verzi [_gcvt](gcvt.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _gcvt_s(
   char *buffer,
   size_t sizeInBytes,
   double value,
   int digits
);
template <size_t cchStr>
errno_t _gcvt_s(
   char (&buffer)[cchStr],
   double value,
   int digits
); // C++ only
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Vyrovnávací paměť pro uložení výsledku převodu

*sizeInBytes*<br/>
Velikost vyrovnávací paměti.

*value*<br/>
Hodnota, která má být převedena.

*znak*<br/>
Počet uložených platných číslic.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Pokud dojde k chybě z důvodu neplatného parametru (viz následující tabulka s neplatnými hodnotami), je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí se kód chyby. Kódy chyb jsou definovány v errno. h. Seznam těchto chyb naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|*vyrovnávací paměti*|*sizeInBytes*|*value*|*znak*|vrátit|Hodnota v *bufferu*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**NULL**|Jakýmikoli|Jakýmikoli|Jakýmikoli|**EINVAL**|Nezměněno.|
|Není **null** (ukazuje na platnou paměť)|nula|Jakýmikoli|Jakýmikoli|**EINVAL**|Nezměněno.|
|Není **null** (ukazuje na platnou paměť)|Jakýmikoli|Jakýmikoli|>= *sizeInBytes*|**EINVAL**|Nezměněno.|

**Problémy se zabezpečením**

**_gcvt_s** může vygenerovat porušení přístupu, pokud *vyrovnávací paměť* neukazuje na platnou paměť a není **null**.

## <a name="remarks"></a>Poznámky

Funkce **_gcvt_s** převede *hodnotu* s plovoucí desetinnou čárkou na řetězec znaků (který obsahuje desetinnou čárku a možné znak pro podepsání) a uloží řetězec do *vyrovnávací paměti*. *vyrovnávací paměť* by měla být dostatečně velká, aby odpovídala převedené hodnotě, a ukončujícímu znaku null, který je automaticky připojen. Vyrovnávací paměť s délkou **_CVTBUFSIZE** je dostačující pro všechny hodnoty s plovoucí desetinnou čárkou. Pokud se použije velikost vyrovnávací *paměti + 1* , funkce nepřepíše konec vyrovnávací paměti, takže nezapomeňte pro tuto operaci dodat dostatečnou vyrovnávací paměť. **_gcvt_s** se pokusí *vydávat číslice číslic v* desítkovém formátu. Pokud to nemůže *, vytvoří číslice číslice v* exponenciálním formátu. Koncové nuly lze v převodu potlačit.

V C++systému je použití této funkce zjednodušené přetížením šablony; přetížení může odvodit délku vyrovnávací paměti automaticky a eliminuje nutnost zadat argument Size. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve vyplní vyrovnávací paměť pomocí 0xFD. Pokud chcete toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_gcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char buf[_CVTBUFSIZE];
    int decimal;
    int sign;
    int err;

    err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);

    if (err != 0)
    {
        printf("_gcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 1.2
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
