---
title: _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
ms.date: 4/2/2020
api_name:
- _findnext
- _findnext32
- _findnext32i64
- _findnext64
- _findnext64i32
- _findnexti64
- _wfindnext
- _wfindnext32
- _wfindnext32i64
- _wfindnext64
- _wfindnext64i32
- _wfindnexti64
- _o__findnext32
- _o__findnext32i64
- _o__findnext64
- _o__findnext64i32
- _o__wfindnext32
- _o__wfindnext32i64
- _o__wfindnext64
- _o__wfindnext64i32
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
- findnext
- _wfindnext32i64
- _tfindnext64i32
- findnext32
- findnext32i64
- wfindnext64i32
- _wfindnext
- tfindnext64
- findnexti64
- _findnexti64
- _tfindnexti64
- _findnext64i32
- tfindnexti64
- tfindnext32
- _wfindnext64i32
- findnext64i32
- _findnext
- _tfindnext32i64
- _wfindnext64
- wfindnext
- wfindnext32
- tfindnext32i64
- _findnext64
- _tfindnext64
- _wfindnext32
- findnext64
- _findnext32i64
- tfindnext
- wfindnexti64
- tfindnext64i32
- _tfindnext32
- wfindnext32i64
- wfindnext64
- _wfindnexti64
- _tfindnext
- _findnext32
helpviewer_keywords:
- _wfindnexti64 function
- _tfindnext32 function
- wfindnexti64 function
- _wfindnext32i64 function
- findnext32i64 function
- tfindnext64i32 function
- _tfindnext64i32 function
- _findnext function
- findnext64i32 function
- _tfindnext function
- findnext32 function
- tfindnext32 function
- _findnext32 function
- _tfindnext32i64 function
- _wfindnext function
- tfindnext function
- _findnext64 function
- findnext64 function
- _findnext64i32 function
- wfindnext32i64 function
- findnext function
- wfindnext32 function
- _wfindnext64i32 function
- findnexti64 function
- _wfindnext64 function
- _findnext32i64 function
- _findnexti64 function
- _tfindnext64 function
- wfindnext64i32 function
- tfindnexti64 function
- wfindnext64 function
- wfindnext function
- tfindnext64 function
- _wfindnext32 function
- tfindnext32i64 function
- _tfindnexti64 function
ms.assetid: 75d97188-5add-4698-a46c-4c492378f0f8
ms.openlocfilehash: 38243b48a97c038f36ada85e3ca2cda814f43fa8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346742"
---
# <a name="_findnext-_findnext32-_findnext32i64-_findnext64-_findnext64i32-_findnexti64-_wfindnext-_wfindnext32-_wfindnext32i64-_wfindnext64-_wfindnext64i32-_wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

Najděte další název, pokud existuje, který odpovídá argumentu *filespec* v předchozím volání [_findfirst](findfirst-functions.md)a odpovídajícím způsobem změňte obsah struktury *fileinfo.*

## <a name="syntax"></a>Syntaxe

```C
int _findnext(
   intptr_t handle,
   struct _finddata_t *fileinfo
);
int _findnext32(
   intptr_t handle,
   struct _finddata32_t *fileinfo
);
int _findnext64(
   intptr_t handle,
   struct __finddata64_t *fileinfo
);
int _findnexti64(
   intptr_t handle,
   struct __finddatai64_t *fileinfo
);
int _findnext32i64(
   intptr_t handle,
   struct _finddata32i64_t *fileinfo
);
int _findnext64i32(
   intptr_t handle,
   struct _finddata64i32_t *fileinfo
);
int _wfindnext(
   intptr_t handle,
   struct _wfinddata_t *fileinfo
);
int _wfindnext32(
   intptr_t handle,
   struct _wfinddata32_t *fileinfo
);
int _wfindnext64(
   intptr_t handle,
   struct _wfinddata64_t *fileinfo
);
int _wfindnexti64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext32i64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext64i32(
   intptr_t handle,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>Parametry

*Zpracování*<br/>
Popisovač hledání vrácený předchozím voláním **_findfirst**.

*Fileinfo*<br/>
Vyrovnávací paměť informací o souboru.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí hodnotu 0. V opačném případě vrátí -1 a nastaví **errno** na hodnotu označující povahu selhání. Možné kódy chyb jsou uvedeny v následující tabulce.

|hodnota errno|Podmínka|
|-|-|
| **EINVAL** | Neplatný parametr: *fileinfo* byl **NULL**. Nebo operační systém vrátil neočekávanou chybu. |
| **ENOENT** | Nebyly nalezeny žádné další odpovídající soubory. |
| **ENOMEM** | Nepřekročila MAX_PATH dostatek paměti nebo délka názvu **souboru**. |

Pokud je předán neplatný parametr, tyto funkce vyvolat neplatný parametr obslužné rutiny, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

Po dokončení funkce **_findfirst** nebo **_findnext** (nebo varianty) musíte volat [_findclose.](findclose.md) Tím se uvolní prostředky používané těmito funkcemi v aplikaci.

Varianty těchto funkcí s předponou **w** jsou verze s širokým znakem; v opačném případě jsou shodné s odpovídající jednobajtové funkce.

Varianty těchto funkcí podporují 32bitové nebo 64bitové časové typy a 32bitové nebo 64bitové velikosti souborů. První číselná přípona (**32** nebo **64**) označuje velikost použitého časového typu; Druhá přípona je **buď i32** nebo **i64**, označující, zda je velikost souboru reprezentována jako 32bitové nebo 64bitové celé číslo. Informace o tom, které verze podporují 32bitové a 64bitové časové typy a velikosti souborů, naleznete v následující tabulce. Varianty, které používají typ 64bitového času, umožňují vyjádřit data vytvoření souboru až do 23:59:59, 31. vzhledem k tomu, že ty, které používají 32bitové časové typy, představují pouze data do 23:59:59 leden 18, 2038, UTC. Půlnoc 1. ledna 1970 je dolní mez časového období pro všechny tyto funkce.

Pokud nemáte konkrétní důvod používat verze, které explicitně určují velikost času, použijte **_findnext** nebo **_wfindnext** nebo, pokud potřebujete podporovat velikosti souborů větší než 3 GB, použijte **_findnexti64** nebo **_wfindnexti64**. Všechny tyto funkce používají 64bitový typ času. V předchozích verzích tyto funkce používaly typ 32bitového času. Pokud se jedná o narušující změnu pro aplikaci, můžete definovat **_USE_32BIT_TIME_T** získat staré chování. Pokud je **definován_USE_32BIT_TIME_T** **_findnext** **_finnexti64** a jejich odpovídající verze unicode používají 32bitový čas.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_findnext"></a>Změny typu a délky souboru _findnext

|Functions|**_USE_32BIT_TIME_T** definováno?|Typ času|Typ délky souboru|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext**, **_wfindnext**|Nedefinováno|64bitová|32bitová|
|**_findnext**, **_wfindnext**|Definovány|32bitová|32bitová|
|**_findnext32** **, _wfindnext32**|Definice makra nemá vliv na|32bitová|32bitová|
|**_findnext64**, **_wfindnext64**|Definice makra nemá vliv na|64bitová|64bitová|
|**_findnexti64**, **_wfindnexti64**|Nedefinováno|64bitová|64bitová|
|**_findnexti64**, **_wfindnexti64**|Definovány|32bitová|64bitová|
|**_findnext32i64**, **_wfindnext32i64**|Definice makra nemá vliv na|32bitová|64bitová|
|**_findnext64i32**, **_wfindnext64i32**|Definice makra nemá vliv na|64bitová|32bitová|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindnext**|**_findnext**|**_findnext**|**_wfindnext**|
|**_tfindnext32**|**_findnext32**|**_findnext32**|**_wfindnext32**|
|**_tfindnext64**|**_findnext64**|**_findnext64**|**_wfindnext64**|
|**_tfindnexti64**|**_findnexti64**|**_findnexti64**|**_wfindnexti64**|
|**_tfindnext32i64**|**_findnext32i64**|**_findnext32i64**|**_wfindnext32i64**|
|**_tfindnext64i32**|**_findnext64i32**|**_findnext64i32**|**_wfindnext64i32**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_findnext**|\<io.h>|
|**_findnext32**|\<io.h>|
|**_findnext64**|\<io.h>|
|**_findnexti64**|\<io.h>|
|**_findnext32i64**|\<io.h>|
|**_findnext64i32**|\<io.h>|
|**_wfindnext**|\<io.h> \<nebo wchar.h>|
|**_wfindnext32**|\<io.h> \<nebo wchar.h>|
|**_wfindnext64**|\<io.h> \<nebo wchar.h>|
|**_wfindnexti64**|\<io.h> \<nebo wchar.h>|
|**_wfindnext32i64**|\<io.h> \<nebo wchar.h>|
|**_wfindnext64i32**|\<io.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Systémová volání](../../c-runtime-library/system-calls.md)<br/>
[Funkce hledání názvu souboru](../../c-runtime-library/filename-search-functions.md)<br/>
