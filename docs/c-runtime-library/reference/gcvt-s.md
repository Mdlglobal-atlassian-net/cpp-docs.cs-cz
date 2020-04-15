---
title: _gcvt_s
ms.date: 4/2/2020
api_name:
- _gcvt_s
- _o__gcvt_s
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
ms.openlocfilehash: 10d2b9af45b78a3f5ed673bde3d37894ccb00168
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345373"
---
# <a name="_gcvt_s"></a>_gcvt_s

Převede hodnotu s plovoucí desetinnou hodnotou na řetězec. Toto je verze [_gcvt](gcvt.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Vyrovnávací paměti*<br/>
Vyrovnávací paměť pro uložení výsledku převodu.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti.

*Hodnotu*<br/>
Hodnota, která má být převedena.

*číslice*<br/>
Počet uložených platných číslic.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Pokud dojde k selhání z důvodu neplatného parametru (v následující tabulce naleznete neplatné hodnoty), je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, je vrácen kód chyby. Kódy chyb jsou definovány v souboru Errno.h. Seznam těchto chyb naleznete v [tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|*Vyrovnávací paměti*|*sizeInBytes*|*Hodnotu*|*číslice*|Vrátit|Hodnota ve *vyrovnávací paměti*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**Null**|jakékoli|jakékoli|jakékoli|**EINVAL**|Není změněno.|
|Není **null** (odkazuje na platnou paměť)|nula|jakékoli|jakékoli|**EINVAL**|Není změněno.|
|Není **null** (odkazuje na platnou paměť)|jakékoli|jakékoli|>= *sizeInBytes*|**EINVAL**|Není změněno.|

**Problémy se zabezpečením**

**_gcvt_s** může generovat narušení přístupu, pokud *vyrovnávací paměť* neukazuje na platnou paměť a není **null**.

## <a name="remarks"></a>Poznámky

Funkce **_gcvt_s** převede *hodnotu* s plovoucí desetinnou čárkou na řetězec znaků (který obsahuje desetinnou čárku a možný bajt znaménku) a uloží řetězec do *vyrovnávací paměti*. *vyrovnávací paměť* by měla být dostatečně velká, aby se přizpůsobila převedené hodnotě plus ukončujícímu nulovému znaku, který je připojen automaticky. Vyrovnávací paměť délky **_CVTBUFSIZE** je dostatečná pro jakoukoli hodnotu s plovoucí desetinnou tácek. Pokud je použita velikost vyrovnávací paměti *číslic* + 1, funkce nebude přepsat konec vyrovnávací paměti, proto nezapomeňte zadat dostatečnou vyrovnávací paměť pro tuto operaci. **_gcvt_s** pokusí vytvořit *číslice* v desítkovém formátu. Pokud nemůže, vytvoří *číslice* číslic v exponenciálním formátu. Koncové nuly mohou být v převodu potlačeny.

V jazyce C++ je použití této funkce zjednodušeno přetížením šablony; přetížení může odvodit délku vyrovnávací paměti automaticky, což eliminuje potřebu zadat argument velikosti. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
