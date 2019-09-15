---
title: _findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64
ms.date: 11/04/2016
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
ms.openlocfilehash: f84c70a6b2d9e6f7adf862bdb1622a603c1fdc4c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957193"
---
# <a name="_findfirst-_findfirst32-_findfirst32i64-_findfirst64-_findfirst64i32-_findfirsti64-_wfindfirst-_wfindfirst32-_wfindfirst32i64-_wfindfirst64-_wfindfirst64i32-_wfindfirsti64"></a>_findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64

Zadejte informace o první instanci názvu souboru, který se shoduje se souborem zadaným v argumentu *filespec* .

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

*filespec*<br/>
Specifikace cílového souboru (může obsahovat zástupné znaky).

*fileinfo*<br/>
Vyrovnávací paměť informací o souborech.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí **_findfirst** jedinečný vyhledávací popisovač identifikující soubor nebo skupinu souborů, které odpovídají specifikaci *filespec* , kterou lze použít v následném volání [_findnext](findnext-functions.md) nebo [_findclose](findclose.md). V opačném případě **_findfirst** vrátí hodnotu-1 a nastaví **errno** na jednu z následujících hodnot.

| hodnota errno | Podmínka |
|-|-|
| **EINVAL** | Neplatný parametr: parametr *filespec* nebo *FileInfo* měl **hodnotu null**. Nebo operační systém vrátil neočekávanou chybu. |
| **ENOENT** | Specifikace souboru, kterou nelze spárovat. |
| **ENOMEM** | Nedostatek paměti |
| **EINVAL** | Neplatná specifikace názvu souboru nebo je zadaný název souboru větší než **MAX_PATH**. |

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pokud je předán neplatný parametr, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

[_Findclose](findclose.md) je nutné volat po dokončení pomocí funkce **_findfirst** nebo [_findnext](findnext-functions.md) (nebo libovolné varianty). Tím se uvolní prostředky využívané těmito funkcemi ve vaší aplikaci.

Variace těchto funkcí, které mají předponu **w** , jsou verze s velkým znakem; v opačném případě jsou stejné jako odpovídající funkce s jedním bytem.

Variace těchto funkcí podporují 32 nebo 64 typů času a 32 64 bitů a velikost souborů. První číselná přípona (**32** nebo **64**) označuje velikost typu času; Druhá přípona je buď **i32** nebo **I64**, a označuje, zda je velikost souboru reprezentována jako 32 nebo 64 celé číslo. Informace o tom, které verze podporují 32 a 64 typy času a velikosti souborů, najdete v následující tabulce. Přípona **i32** nebo **I64** je vynechána, pokud je stejná jako velikost typu času, takže **_findfirst64** také podporuje 64 bitů souborů a **_findfirst32** podporuje pouze 32 bitů souborů.

Tyto funkce používají různé formy struktury **_finddata_t** pro parametr *FileInfo* . Další informace o struktuře najdete v tématu [funkce vyhledávání názvů souborů](../../c-runtime-library/filename-search-functions.md).

Variace, které používají 64 typ času, umožňují, aby data vytváření souborů byla vyjádřena až 23:59:59, 31. prosince, 3000, UTC. Ty, které používají 32 typy času, reprezentují data pouze do 23:59:59 15. ledna 2038, UTC. Půlnoc, 1. ledna 1970 je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.

Pokud nemáte konkrétní důvod pro použití verzí, které určují velikost času explicitně, použijte **_findfirst** nebo **_wfindfirst** , nebo pokud potřebujete podporovat velikosti souborů větší než 3 GB, použijte **_findfirsti64** nebo **_wfindfirsti64**. Všechny tyto funkce používají typ času 64. V dřívějších verzích tyto funkce používaly typ času 32. Pokud se jedná o zásadní změnu aplikace, můžete definovat **_USE_32BIT_TIME_T** , který se má vrátit k původnímu chování. Pokud je definována **_USE_32BIT_TIME_T** , **_findfirst**, **_Finfirsti64**a jejich odpovídající verze Unicode, používají 32 čas.

### <a name="time-type-and-file-length-type-variations-of-_findfirst"></a>Typ času a délka souboru – variace typu _findfirst

|Funkce|**_USE_32BIT_TIME_T** definovány?|Typ času|Typ délky souboru|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst**, **_wfindfirst**|Nedefinováno|64bitová|32bitová|
|**_findfirst**, **_wfindfirst**|definované|32bitová|32bitová|
|**_findfirst32**, **_wfindfirst32**|Není ovlivněno definicí makra.|32bitová|32bitová|
|**_findfirst64**, **_wfindfirst64**|Není ovlivněno definicí makra.|64bitová|64bitová|
|**_findfirsti64**, **_wfindfirsti64**|Nedefinováno|64bitová|64bitová|
|**_findfirsti64**, **_wfindfirsti64**|definované|32bitová|64bitová|
|**_findfirst32i64**, **_wfindfirst32i64**|Není ovlivněno definicí makra.|32bitová|64bitová|
|**_findfirst64i32**, **_wfindfirst64i32**|Není ovlivněno definicí makra.|64bitová|32bitová|

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
|**_wfindfirst**|\<IO. h > nebo \<WCHAR. h >|
|**_wfindfirst32**|\<IO. h > nebo \<WCHAR. h >|
|**_wfindfirst64**|\<IO. h > nebo \<WCHAR. h >|
|**_wfindfirsti64**|\<IO. h > nebo \<WCHAR. h >|
|**_wfindfirst32i64**|\<IO. h > nebo \<WCHAR. h >|
|**_wfindfirst64i32**|\<IO. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Systémová volání](../../c-runtime-library/system-calls.md)<br/>
[Funkce hledání názvů souborů](../../c-runtime-library/filename-search-functions.md)<br/>
