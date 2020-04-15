---
title: _get_tzname
ms.date: 4/2/2020
api_name:
- _get_tzname
- _o__get_tzname
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_tzname
- get_tzname
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: 50f1f6e4320e3ef905b4eda67ba1d458a5b1df08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344878"
---
# <a name="_get_tzname"></a>_get_tzname

Načte reprezentaci řetězce znaku názvu časového pásma nebo názvu standardního časového pásma (DST).

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_tzname(
    size_t* pReturnValue,
    char* timeZoneName,
    size_t sizeInBytes,
    int index
);
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Délka řetězce *timeZoneName* včetně zakončení null.

*timeZoneName*<br/>
Adresa znakového řetězce pro reprezentaci názvu časového pásma nebo názvu letního standardního časového pásma (DST) v závislosti na *indexu*.

*sizeInBytes*<br/>
Velikost řetězce znaků *timeZoneName* v bajtech.

*Index*<br/>
Index jednoho ze dvou názvů časových pásem načíst.

|*Index*|Obsah *timeZoneName*|výchozí hodnota *timeZoneName*|
|-|-|-|
|0|Název časového pásma|"PST"|
|1|Název letního standardního časového pásma|"PDT"|
|> 1 nebo < 0|**errno** nastaveno na **EINVAL**|nezměněno|

Pokud hodnoty nejsou explicitně změněny za běhu, výchozí hodnoty jsou "PST" a "PDT" v uvedeném pořadí.

## <a name="return-value"></a>Návratová hodnota

Nula, pokud je úspěšná, jinak hodnota typu **errno.**

Pokud je buď *timeZoneName* **null**nebo *sizeInBytes* je nula nebo menší než nula (ale ne obojí), je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **Funkce EINVAL**.

### <a name="error-conditions"></a>Chybové stavy

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*Index*|Návratová hodnota|Obsah *timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|velikost názvu TZ|**Null**|0|0 nebo 1|0|nezměněno|
|velikost názvu TZ|jakékoli|> 0|0 nebo 1|0|Název TZ|
|nezměněno|**Null**|> 0|jakékoli|**EINVAL**|nezměněno|
|nezměněno|jakékoli|nula|jakékoli|**EINVAL**|nezměněno|
|nezměněno|jakékoli|> 0|> 1|**EINVAL**|nezměněno|

## <a name="remarks"></a>Poznámky

Funkce **_get_tzname** načte reprezentaci řetězce znaku aktuálního názvu časového pásma nebo názvu letního pásma (DST) do adresy *timeZoneName* v závislosti na hodnotě indexu spolu s velikostí řetězce v *pReturnValue*. Pokud *timeZoneName* je **NULL** a *sizeInBytes* je nula, velikost řetězce potřebné pro uložení zadaného časového pásma a ukončující null v bajtů je vrácena v *pReturnValue*. Hodnoty indexu musí být buď 0 pro standardní časové pásmo, nebo 1 pro standardní letní časové pásmo; všechny ostatní hodnoty *indexu* mají neurčené výsledky.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="example"></a>Příklad

Tato ukázka volá **_get_tzname** získat požadovanou velikost vyrovnávací paměti pro zobrazení aktuálního názvu standardního časového pásma letního času, přiděluje vyrovnávací paměť této velikosti, znovu volá **_get_tzname** načíst název do vyrovnávací paměti a vytiskne jej do konzoly.

```C
// crt_get_tzname.c
// Compile by using: cl /W4 crt_get_tzname.c
#include <stdio.h>
#include <time.h>
#include <malloc.h>

enum TZINDEX {
    STD,
    DST
};

int main()
{
    size_t tznameSize = 0;
    char * tznameBuffer = NULL;

    // Get the size of buffer required to hold DST time zone name
    if (_get_tzname(&tznameSize, NULL, 0, DST))
        return 1;    // Return an error value if it failed

    // Allocate a buffer for the name
    if (NULL == (tznameBuffer = (char *)(malloc(tznameSize))))
        return 2;    // Return an error value if it failed

    // Load the name in the buffer
    if (_get_tzname(&tznameSize, tznameBuffer, tznameSize, DST))
        return 3;    // Return an error value if it failed

    printf_s("The current Daylight standard time zone name is %s.\n", tznameBuffer);
    return 0;
}
```

### <a name="output"></a>Výstup

```Output
The current Daylight standard time zone name is PDT.
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

Další informace naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
