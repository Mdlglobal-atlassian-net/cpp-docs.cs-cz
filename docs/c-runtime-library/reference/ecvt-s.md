---
title: _ecvt_s
ms.date: 4/2/2020
api_name:
- _ecvt_s
- _o__ecvt_s
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
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: e33840e772de770e0f05ae45d2c2d4bec7e09939
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348050"
---
# <a name="_ecvt_s"></a>_ecvt_s

Převede **dvojité** číslo na řetězec. Toto je verze [_ecvt](ecvt.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Vyplněno ukazatelem na řetězec číslic, výsledek převodu.

*_SizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtů.

*_Value*<br/>
Číslo, které má být převedeno.

*_Count*<br/>
Počet uložených číslic.

*_Dec*<br/>
Uložená pozice desetinných bodů.

*_Sign*<br/>
Znaménko převedeného čísla.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud došlo k chybě. Kódy chyb jsou definovány v souboru Errno.h. Další informace naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

V případě neplatného parametru uvedeného v následující tabulce tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **Funkce EINVAL**.

### <a name="error-conditions"></a>Chybové stavy

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|Návratová hodnota|Hodnota ve *vyrovnávací paměti*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**Null**|jakékoli|jakékoli|jakékoli|jakékoli|jakékoli|**EINVAL**|Není změněno.|
|Není **null** (odkazuje na platnou paměť)|<=0|jakékoli|jakékoli|jakékoli|jakékoli|**EINVAL**|Není změněno.|
|jakékoli|jakékoli|jakékoli|jakékoli|**Null**|jakékoli|**EINVAL**|Není změněno.|
|jakékoli|jakékoli|jakékoli|jakékoli|jakékoli|**Null**|**EINVAL**|Není změněno.|

## <a name="security-issues"></a>Problémy se zabezpečením

**_ecvt_s** může způsobit narušení přístupu, pokud *vyrovnávací paměť* neukazuje na platnou paměť a není **null**.

## <a name="remarks"></a>Poznámky

Funkce **_ecvt_s** převede číslo s plovoucí desetinnou tácem na řetězec znaků. Parametr *_Value* je číslo s plovoucí desetinnou stranou, které má být převedeno. Tato funkce ukládá až *počet* číslic *_Value* jako řetězec a připojí prázdný znak (\0). Pokud počet číslic v *_Value* překročí *_Count*, je číslice nižšího řádu zaokrouhlena. Pokud je méně než *počet* číslic, řetězec je doplněn nulami.

V řetězci jsou uloženy pouze číslice. Umístění desetinné čárky a znaménko *_Value* lze získat z *_Dec* a *_Sign* po volání. Parametr *_Dec* odkazuje na hodnotu celého čísla udávající pozici desetinné čárky vzhledem k začátku řetězce. Hodnota 0 nebo záporné celé číslo označuje, že desetinná čárka leží nalevo od první číslice. Parametr *_Sign* odkazuje na celé číslo, které označuje znaménko převedeného čísla. Pokud je celá hodnota 0, číslo je kladné. V opačném případě je číslo záporné.

Vyrovnávací paměť délky **_CVTBUFSIZE** je dostatečná pro všechny hodnoty s plovoucí desetinnou desetinnou hodnotou.

Rozdíl mezi **_ecvt_s** a **_fcvt_s** je ve výkladu *parametru _Count.* **_ecvt_s** interpretuje *_Count* jako celkový počet číslic ve výstupním řetězci, zatímco **_fcvt_s** interpretuje *_Count* jako počet číslic za desetinnou čárkou.

V jazyce C++ je použití této funkce zjednodušeno přetížením šablony; přetížení může odvodit délku vyrovnávací paměti automaticky, což eliminuje potřebu zadat argument velikosti. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelná hlavička|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
