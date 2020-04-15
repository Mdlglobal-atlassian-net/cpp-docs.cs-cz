---
title: _findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64
ms.date: 4/2/2020
api_name:
- _findfirst
- _wfindfirst
- _findfirst32
- _wfindfirst32
- _findfirst32i64
- _wfindfirst32i64
- _findfirst64
- _wfindfirst64
- _findfirst64i32
- _wfindfirst64i32
- _findfirsti64
- _wfindfirsti64
- _o__findfirst32
- _o__findfirst32i64
- _o__findfirst64
- _o__findfirst64i32
- _o__wfindfirst32
- _o__wfindfirst32i64
- _o__wfindfirst64
- _o__wfindfirst64i32
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- findfirst32i64
- wfindfirst32i64
- tfindfirst64
- _findfirst64i32
- _wfindfirst32i64
- _wfindfirsti64
- wfindfirst
- _tfindfirsti64
- findfirst32
- _tfindfirst32
- _findfirsti64
- findfirst
- wfindfirst64
- wfindfirst32
- tfindfirst32
- _wfindfirst64i32
- findfirst64i32
- tfindfirst64i32
- _wfindfirst
- findfirsti64
- _findfirst32i64
- wfindfirst64i32
- _wfindfirst32
- _findfirst32
- _tfindfirst32i64
- tfindfirst
- _tfindfirst64i32
- findfirst64
- _tfindfirst
- _findfirst64
- _tfindfirst64
- tfindfirst32i64
- _findfirst
- _wfindfirst64
helpviewer_keywords:
- _tfindfirst64 function
- _wfindfirst64i32 function
- _wfindfirst32i64 function
- wfindfirst32 function
- _findfirst function
- wfindfirst64 function
- _wfindfirst function
- _findfirst64i32 function
- wfindfirst function
- _findfirst64 function
- tfindfirst32 function
- _tfindfirst64i32 function
- findfirst function
- findfirst32i64 function
- tfindfirst64 function
- _tfindfirst32 function
- tfindfirst32i64 function
- tfindfirst64i32 function
- _wfindfirsti64 function
- _findfirst32i64 function
- findfirst32 function
- findfirsti64 function
- findfirst64i32 function
- tfindfirsti64 function
- tfindfirst function
- _wfindfirst32 function
- wfindfirsti64 function
- _tfindfirsti64 function
- _tfindfirst function
- _tfindfirst32i64 function
- findfirst64 function
- _findfirst32 function
- _findfirsti64 function
- wfindfirst32i64 function
- wfindfirst64i32 function
- _wfindfirst64 function
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
ms.openlocfilehash: d83cc0913584618897cbc4aec45cb137388674b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346814"
---
# <a name="_findfirst-_findfirst32-_findfirst32i64-_findfirst64-_findfirst64i32-_findfirsti64-_wfindfirst-_wfindfirst32-_wfindfirst32i64-_wfindfirst64-_wfindfirst64i32-_wfindfirsti64"></a>_findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64

Zadejte informace o první instanci názvu souboru, který odpovídá souboru zadanému v argumentu *filespec.*

## <a name="syntax"></a>Syntaxe

```C
intptr_t _findfirst(
   const char *filespec,
   struct _finddata_t *fileinfo
);
intptr_t _findfirst32(
   const char *filespec,
   struct _finddata32_t *fileinfo
);
intptr_t _findfirst64(
   const char *filespec,
   struct _finddata64_t *fileinfo
);
intptr_t _findfirsti64(
   const char *filespec,
   struct _finddatai64_t *fileinfo
);
intptr_t _findfirst32i64(
   const char *filespec,
   struct _finddata32i64_t *fileinfo
);
intptr_t _findfirst64i32(
   const char *filespec,
   struct _finddata64i32_t *fileinfo
);
intptr_t _wfindfirst(
   const wchar_t *filespec,
   struct _wfinddata_t *fileinfo
);
intptr_t _wfindfirst32(
   const wchar_t *filespec,
   struct _wfinddata32_t *fileinfo
);
intptr_t _wfindfirst64(
   const wchar_t *filespec,
   struct _wfinddata64_t *fileinfo
);
intptr_t _wfindfirsti64(
   const wchar_t *filespec,
   struct _wfinddatai64_t *fileinfo
);
intptr_t _wfindfirst32i64(
   const wchar_t *filespec,
   struct _wfinddata32i64_t *fileinfo
);
intptr_t _wfindfirst64i32(
   const wchar_t *filespec,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>Parametry

*Filespec*<br/>
Specifikace cílového souboru (může obsahovat zástupné znaky).

*Fileinfo*<br/>
Vyrovnávací paměť informací o souboru.

## <a name="return-value"></a>Návratová hodnota

Pokud **_findfirst** úspěšný, vrátí jedinečný popisovač hledání identifikující soubor nebo skupinu souborů, které odpovídají specifikaci *filespec,* které lze použít při následném volání [_findnext](findnext-functions.md) nebo [_findclose](findclose.md). V opačném případě **vrátí _findfirst** hodnotu -1 a nastaví **chybně** na jednu z následujících hodnot.

| hodnota errno | Podmínka |
|-|-|
| **EINVAL** | Neplatný parametr: *filespec* nebo *fileinfo* byl **NULL**. Nebo operační systém vrátil neočekávanou chybu. |
| **ENOENT** | Specifikace souboru, která nemohla být spárována. |
| **ENOMEM** | Nedostatek paměti. |
| **EINVAL** | Neplatná specifikace názvu souboru nebo zadaný název souboru byl větší než **MAX_PATH**. |

Další informace o těchto a dalších návratových kódech naleznete [v tématech _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pokud je předán neplatný parametr, tyto funkce vyvolat neplatný parametr obslužné rutiny, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

Po dokončení **funkce _findfirst** nebo [_findnext](findnext-functions.md) (nebo varianty) musíte zavolat [_findclose.](findclose.md) To uvolní prostředky používané těmito funkcemi v aplikaci.

Varianty těchto funkcí, které mají předponu **w,** jsou verze s širokými znaky; v opačném případě jsou shodné s odpovídající jednobajtové funkce.

Varianty těchto funkcí podporují 32bitové nebo 64bitové časové typy a 32bitové nebo 64bitové velikosti souborů. První číselná přípona (**32** nebo **64**) označuje velikost typu času; Druhá přípona je **buď i32** nebo **i64**a označuje, zda je velikost souboru reprezentována jako 32bitové nebo 64bitové celé číslo. Informace o tom, které verze podporují 32bitové a 64bitové časové typy a velikosti souborů, naleznete v následující tabulce. Přípona **i32** nebo **i64** je vynechána, pokud je stejná jako velikost typu času, takže **_findfirst64** také podporuje 64bitové délky souborů a **_findfirst32** podporuje pouze 32bitové délky souborů.

Tyto funkce používají různé formy **_finddata_t** struktury pro parametr *fileinfo.* Další informace o struktuře naleznete v tématu [Funkce hledání názvu souboru](../../c-runtime-library/filename-search-functions.md).

Varianty, které používají typ 64bitového času, umožňují vyjádřit data vytvoření souboru až do 23:59:59, 31. Ty, které používají 32bitové časové typy představují data pouze do 23:59:59 Leden 18, 2038, UTC. Půlnoc 1. ledna 1970 je dolní mez časového období pro všechny tyto funkce.

Pokud nemáte konkrétní důvod používat verze, které explicitně určují velikost času, použijte **_findfirst** nebo **_wfindfirst** nebo, pokud potřebujete podporovat velikosti souborů větší než 3 GB, použijte **_findfirsti64** nebo **_wfindfirsti64**. Všechny tyto funkce používají 64bitový typ času. V dřívějších verzích tyto funkce používaly typ 32bitového času. Pokud se jedná o narušující změnu pro aplikaci, můžete definovat **_USE_32BIT_TIME_T** vrátit ke starému chování. Pokud je **definován_USE_32BIT_TIME_T** **_findfirst**, **_finfirsti64**a jejich odpovídající verze Unicode používají 32bitový čas.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_findfirst"></a>Změny typu a délky souboru _findfirst

|Functions|**_USE_32BIT_TIME_T** definováno?|Typ času|Typ délky souboru|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst**, **_wfindfirst**|Nedefinováno|64bitová|32bitová|
|**_findfirst**, **_wfindfirst**|Definovány|32bitová|32bitová|
|**_findfirst32**, **_wfindfirst32**|Definice makra nemá vliv na|32bitová|32bitová|
|**_findfirst64**, **_wfindfirst64**|Definice makra nemá vliv na|64bitová|64bitová|
|**_findfirsti64**, **_wfindfirsti64**|Nedefinováno|64bitová|64bitová|
|**_findfirsti64**, **_wfindfirsti64**|Definovány|32bitová|64bitová|
|**_findfirst32i64**, **_wfindfirst32i64**|Definice makra nemá vliv na|32bitová|64bitová|
|**_findfirst64i32**, **_wfindfirst64i32**|Definice makra nemá vliv na|64bitová|32bitová|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindfirst**|**_findfirst**|**_findfirst**|**_wfindfirst**|
|**_tfindfirst32**|**_findfirst32**|**_findfirst32**|**_wfindfirst32**|
|**_tfindfirst64**|**_findfirst64**|**_findfirst64**|**_wfindfirst64**|
|**_tfindfirsti64**|**_findfirsti64**|**_findfirsti64**|**_wfindfirsti64**|
|**_tfindfirst32i64**|**_findfirst32i64**|**_findfirst32i64**|**_wfindfirst32i64**|
|**_tfindfirst64i32**|**_findfirst64i32**|**_findfirst64i32**|**_wfindfirst64i32**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_findfirst**|\<io.h>|
|**_findfirst32**|\<io.h>|
|**_findfirst64**|\<io.h>|
|**_findfirsti64**|\<io.h>|
|**_findfirst32i64**|\<io.h>|
|**_findfirst64i32**|\<io.h>|
|**_wfindfirst**|\<io.h> \<nebo wchar.h>|
|**_wfindfirst32**|\<io.h> \<nebo wchar.h>|
|**_wfindfirst64**|\<io.h> \<nebo wchar.h>|
|**_wfindfirsti64**|\<io.h> \<nebo wchar.h>|
|**_wfindfirst32i64**|\<io.h> \<nebo wchar.h>|
|**_wfindfirst64i32**|\<io.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Systémová volání](../../c-runtime-library/system-calls.md)<br/>
[Funkce hledání názvu souboru](../../c-runtime-library/filename-search-functions.md)<br/>
