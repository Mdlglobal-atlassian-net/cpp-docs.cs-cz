---
title: _get_tzname
ms.date: 10/22/2018
api_name:
- _get_tzname
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
ms.openlocfilehash: 9f86a4997c328e86597e3bad8a7f7a3a5f5f50b6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955616"
---
# <a name="_get_tzname"></a>_get_tzname

Načte řetězcovou reprezentaci názvu časového pásma nebo standardního standardního názvu časového pásma (DST) pro letní čas.

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
Délka řetězce *časového pásma* , včetně ukončovacího znaku null.

*timeZoneName*<br/>
Adresa řetězce znaků pro reprezentaci názvu časového pásma nebo standardního standardního časového pásma (letního času) v závislosti na *indexu*.

*sizeInBytes*<br/>
Velikost řetězce znaků *timezone* v bajtech

*index*<br/>
Index jednoho ze dvou názvů časových pásem, které mají být načteny.

|*index*|Obsah *časového pásma*|Výchozí hodnota *časového pásma*|
|-|-|-|
|0|Název časového pásma|VYTVOŘENÉ|
|1|Název letního standardního času v časovém pásmu|PDT|
|> 1 nebo < 0|**errno** nastavené na **EINVAL**|Neupraveno|

Pokud se hodnoty explicitně nezmění během běhu, výchozí hodnoty jsou "PST" a "PDT".

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, jinak hodnota typu **errno** .

Pokud buď má parametr TimeZone **hodnotu null**, nebo je *sizeInBytes* nula nebo menší než nula (ale ne obojí), je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

### <a name="error-conditions"></a>Chybové stavy

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|Návratová hodnota|Obsah *časového pásma*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|velikost názvu TZ|**NULL**|0|0 nebo 1|0|Neupraveno|
|velikost názvu TZ|Jakýmikoli|> 0|0 nebo 1|0|Název TZ|
|Neupraveno|**NULL**|> 0|Jakýmikoli|**EINVAL**|Neupraveno|
|Neupraveno|Jakýmikoli|nula|Jakýmikoli|**EINVAL**|Neupraveno|
|Neupraveno|Jakýmikoli|> 0|> 1|**EINVAL**|Neupraveno|

## <a name="remarks"></a>Poznámky

Funkce **_get_tzname** načítá řetězcovou reprezentaci názvu aktuálního časového pásma nebo standardního standardního časového pásma (DST) na adresu *časového* pásma v závislosti na hodnotě indexu, spolu s velikostí řetězce v *pReturnValue*. Pokud má parametr TimeZone **hodnotu null** a *sizeInBytes* je nula, velikost řetězce požadovaného pro uchování zadaného časového pásma a ukončující hodnoty null v bajtech se vrátí v *pReturnValue*. Hodnoty indexu musí být pro standardní časové pásmo buď 0, nebo 1 pro letní standardní časové pásmo; všechny ostatní hodnoty *indexu* mají neurčené výsledky.

## <a name="example"></a>Příklad

Tato ukázka volá **_get_tzname** , aby získala požadovanou velikost vyrovnávací paměti pro zobrazení aktuálního letního názvu časového pásma, přidělí vyrovnávací paměť této velikosti, zavolá **_get_tzname** znovu pro načtení názvu do vyrovnávací paměti a vytiskne ho do konzoly.

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

Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
