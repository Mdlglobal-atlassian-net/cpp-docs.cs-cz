---
title: _get_tzname – | Dokumentace společnosti Microsoft
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_tzname
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_tzname
- get_tzname
dev_langs:
- C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d773d5d98466963ef621cc3fa7bc5ab8b4acc40a
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990305"
---
# <a name="gettzname"></a>_get_tzname

Získá znak řetězec představující název časového pásma nebo název zóny (běžný čas) letního času (DST).

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
Délka řetězce *timeZoneName* včetně ukončovacího znaku null.

*timeZoneName*<br/>
Adresa znak řetězec pro reprezentaci název nebo název zóny (běžný čas) letního času (DST), v závislosti na *index*.

*sizeInBytes*<br/>
Velikost *timeZoneName* znakové řetězce v bajtech.

*index*<br/>
Index jeden z názvů dva časové pásmo pro načtení.

|*index*|Obsah *timeZoneName*|*timeZoneName* výchozí hodnota|
|-|-|-|
|0|Název časového pásma|"PST"|
|1|Název zóny pro letní čas (běžný čas)|"PDT"|
|< 0 nebo > 1|**errno** nastavena na **EINVAL**|Nezměněno|

Pokud není explicitně byly změněny hodnoty za běhu, výchozí hodnoty jsou "PST" a "PDT".

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, jinak **errno** zadejte hodnotu.

Pokud *timeZoneName* je **NULL**, nebo *sizeInBytes* je nula nebo menší než nula (ale ne oba), je vyvolána obslužnou rutinu neplatného parametru, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí **EINVAL**.

### <a name="error-conditions"></a>Chybové podmínky

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|Návratová hodnota|Obsah *timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|velikost TZ název|**HODNOTU NULL**|0|0 nebo 1|0|Nezměněno|
|velikost TZ název|Všechny|> 0|0 nebo 1|0|Název – TZ|
|Nezměněno|**HODNOTU NULL**|> 0|Všechny|**EINVAL**|Nezměněno|
|Nezměněno|Všechny|nula|Všechny|**EINVAL**|Nezměněno|
|Nezměněno|Všechny|> 0|> 1|**EINVAL**|Nezměněno|

## <a name="remarks"></a>Poznámky

**_Get_tzname –** funkce načte znak řetězcová reprezentace aktuální časové pásmo název nebo název zóny (běžný čas) letního času (DST) do adresu *timeZoneName* v závislosti na tom hodnota, spolu s velikost řetězce v indexu *pReturnValue*. Pokud *timeZoneName* je **NULL** a *sizeInBytes* je nula, velikost řetězce potřebných k uložení zadané časové pásmo a vrátí se v ukončujícíhoznakunullvbajtech*pReturnValue*. Index hodnoty musí být buď 0 pro zónu (běžný čas) nebo 1 pro standardního časového pásma letního času; všechny ostatní hodnoty *index* mají neurčeném výsledky.

## <a name="example"></a>Příklad

Tato ukázka volá **_get_tzname –** získat velikost požadované vyrovnávací paměti k zobrazení aktuálního letního času (běžný čas) název zóny, přidělí vyrovnávací paměť o velikosti, volání **_get_tzname –** znovu pro načtení názvu v Uložit do vyrovnávací paměti, který se vypíše do konzoly.

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
|**_get_tzname**|\<Time.h >|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
