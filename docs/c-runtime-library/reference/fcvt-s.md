---
title: _fcvt_s
ms.date: 4/2/2020
api_name:
- _fcvt_s
- _o__fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: 80f02467e160e3196982c10576ad55f5487e5fc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347446"
---
# <a name="_fcvt_s"></a>_fcvt_s

Převede číslo s plovoucí desetinnou tácem na řetězec. Toto je verze [_fcvt](fcvt.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _fcvt_s(
   char* buffer,
   size_t sizeInBytes,
   double value,
   int count,
   int *dec,
   int *sign
);
template <size_t size>
errno_t _fcvt_s(
   char (&buffer)[size],
   double value,
   int count,
   int *dec,
   int *sign
); // C++ only
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Dodaná vyrovnávací paměť, která bude obsahovat výsledek převodu.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtů.

*Hodnotu*<br/>
Číslo, které má být převedeno.

*Počet*<br/>
Počet číslic za desetinnou čárkou.

*dec*<br/>
Ukazatel na uloženou pozici desetinné čárky.

*Znamení*<br/>
Ukazatel na indikátor uloženého znaku.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud došlo k chybě. Kódy chyb jsou definovány v souboru Errno.h. Seznam těchto chyb naleznete v [tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

V případě neplatného parametru uvedeného v následující tabulce tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **Funkce EINVAL**.

### <a name="error-conditions"></a>Chybové stavy

|*Vyrovnávací paměti*|*sizeInBytes*|value|count|dec|znak|Vrátit|Hodnota ve *vyrovnávací paměti*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**Null**|jakékoli|jakékoli|jakékoli|jakékoli|jakékoli|**EINVAL**|Není změněno.|
|Není **null** (odkazuje na platnou paměť)|<=0|jakékoli|jakékoli|jakékoli|jakékoli|**EINVAL**|Není změněno.|
|jakékoli|jakékoli|jakékoli|jakékoli|**Null**|jakékoli|**EINVAL**|Není změněno.|
|jakékoli|jakékoli|jakékoli|jakékoli|jakékoli|**Null**|**EINVAL**|Není změněno.|

## <a name="security-issues"></a>Problémy se zabezpečením

**_fcvt_s** může způsobit narušení přístupu, pokud *vyrovnávací paměť* neukazuje na platnou paměť a není **null**.

## <a name="remarks"></a>Poznámky

Funkce **_fcvt_s** převede číslo s plovoucí desetinnou hodnotou na řetězec znaků ukončený nulou. Parametr *value* je číslo s plovoucí desetinnou tázkem, které má být převedeno. **_fcvt_s** uloží číslice *hodnoty* jako řetězec a připojí nulový znak (\0). Parametr *count* určuje počet číslic, které mají být uloženy za desetinnou čárkou. Přebytečné číslice jsou zaokrouhleny tak, aby *počítaly* místa. Pokud je méně než *počet* číslic přesnosti, řetězec je doplněn nulami.

V řetězci jsou uloženy pouze číslice. Pozice desetinné čárky a znaménko *hodnoty* lze získat z *dec* a *podepsat* po volání. Parametr *dec* odkazuje na hodnotu celéčíslo; tato celá hodnota udává pozici desetinné čárky vzhledem k začátku řetězce. Hodnota nula nebo záporné celé číslo označuje, že desetinná čárka leží nalevo od první číslice. *Znaménko* parametru odkazuje na celé číslo označující znaménko *hodnoty*. Celé číslo je nastaveno na *hodnotu* 0, pokud je hodnota kladná, a pokud je *hodnota* záporná, je nastaveno na nenulové číslo.

Vyrovnávací paměť délky **_CVTBUFSIZE** je dostatečná pro jakoukoli hodnotu s plovoucí desetinnou tácek.

Rozdíl mezi **_ecvt_s** a **_fcvt_s** je v interpretaci parametru *count.* **_ecvt_s** interpretuje *počet* jako celkový počet číslic ve výstupním řetězci a **_fcvt_s** interpretuje *počet* číslic jako počet číslic za desetinnou čárkou.

V jazyce C++ je použití této funkce zjednodušeno přetížením šablony; přetížení může odvodit délku vyrovnávací paměti automaticky, což eliminuje potřebu zadat argument velikosti. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelná hlavička|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovny:** Všechny verze [funkcí knihovny CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// fcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_fcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 120000
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
