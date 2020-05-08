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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: acb680db3b07b0f600b758401f1270deccf03da7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911664"
---
# <a name="_findnext-_findnext32-_findnext32i64-_findnext64-_findnext64i32-_findnexti64-_wfindnext-_wfindnext32-_wfindnext32i64-_wfindnext64-_wfindnext64i32-_wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

Najde další název, pokud existuje, který odpovídá argumentu *filespec* v předchozím volání metody [_findfirst](findfirst-functions.md)a následně změní obsah struktury *FileInfo* odpovídajícím způsobem.

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

*popisovač*<br/>
Popisovač vyhledávání vrácený předchozím voláním **_findfirst**.

*FileInfo*<br/>
Vyrovnávací paměť informací o souborech.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0. V opačném případě vrátí hodnotu-1 a nastaví **errno** na hodnotu, která označuje povahu selhání. Možné kódy chyb jsou uvedeny v následující tabulce.

|hodnota errno|Podmínka|
|-|-|
| **EINVAL** | Neplatný parametr: hodnota *FileInfo* měla **hodnotu null**. Nebo operační systém vrátil neočekávanou chybu. |
| **ENOENT** | Nenašly se žádné další vyhovující soubory. |
| **ENOMEM** | Nedostatek paměti nebo se **MAX_PATH**překročila délka názvu souboru. |

Pokud je předán neplatný parametr, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

Po dokončení používání funkce **_findfirst** nebo **_findnext** (nebo libovolné varianty) musíte volat [_findclose](findclose.md) . Tím se uvolní prostředky používané těmito funkcemi ve vaší aplikaci.

Variace těchto funkcí s předponou **w** jsou verze s velkým znakem; v opačném případě jsou stejné jako odpovídající funkce s jedním bytem.

Variace těchto funkcí podporují 32 nebo 64 typů času a 32 64 bitů a velikost souborů. První číselná přípona (**32** nebo **64**) označuje velikost použitého typu času; Druhá přípona je buď **i32** , nebo **I64**, která označuje, jestli je velikost souboru reprezentována jako 32 nebo 64 celočíselného bitu. Informace o tom, které verze podporují 32 a 64 typy času a velikosti souborů, najdete v následující tabulce. Variace, které používají 64 typ času, umožňují, aby data vytváření souborů byla vyjádřena až 23:59:59, 31. prosince, 3000, UTC; zatímco ty, které používají 32 typy časových časů, reprezentují jenom data do 23:59:59 15. ledna 2038, UTC. Půlnoc, 1. ledna 1970 je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.

Pokud nemáte konkrétní důvod pro použití verzí, které určují časovou velikost explicitně, použijte **_findnext** nebo **_wfindnext** nebo, pokud potřebujete podporovat velikosti souborů větší než 3 GB, použijte **_findnexti64** nebo **_wfindnexti64**. Všechny tyto funkce používají typ času 64. V předchozích verzích tyto funkce používaly typ času 32. Pokud se jedná o zásadní změnu aplikace, můžete definovat **_USE_32BIT_TIME_T** pro získání starého chování. Je-li definována **_USE_32BIT_TIME_T** , **_findnext**, **_Finnexti64** a jejich odpovídající verze Unicode, používají 32-bit času.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_findnext"></a>Typ času a délka souboru – variace _findnext

|Functions|**_USE_32BIT_TIME_T** definováno?|Typ času|Typ délky souboru|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext** **_wfindnext**|Nedefinováno|64bitová|32bitová|
|**_findnext** **_wfindnext**|Definované|32bitová|32bitová|
|**_findnext32** **_wfindnext32**|Není ovlivněno definicí makra.|32bitová|32bitová|
|**_findnext64** **_wfindnext64**|Není ovlivněno definicí makra.|64bitová|64bitová|
|**_findnexti64** **_wfindnexti64**|Nedefinováno|64bitová|64bitová|
|**_findnexti64** **_wfindnexti64**|Definované|32bitová|64bitová|
|**_findnext32i64** **_wfindnext32i64**|Není ovlivněno definicí makra.|32bitová|64bitová|
|**_findnext64i32** **_wfindnext64i32**|Není ovlivněno definicí makra.|64bitová|32bitová|

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
|**_findnext**|\<IO. h>|
|**_findnext32**|\<IO. h>|
|**_findnext64**|\<IO. h>|
|**_findnexti64**|\<IO. h>|
|**_findnext32i64**|\<IO. h>|
|**_findnext64i32**|\<IO. h>|
|**_wfindnext**|\<IO. h> nebo \<WCHAR. h>|
|**_wfindnext32**|\<IO. h> nebo \<WCHAR. h>|
|**_wfindnext64**|\<IO. h> nebo \<WCHAR. h>|
|**_wfindnexti64**|\<IO. h> nebo \<WCHAR. h>|
|**_wfindnext32i64**|\<IO. h> nebo \<WCHAR. h>|
|**_wfindnext64i32**|\<IO. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Systémová volání](../../c-runtime-library/system-calls.md)<br/>
[Funkce vyhledávání názvů souborů](../../c-runtime-library/filename-search-functions.md)<br/>
