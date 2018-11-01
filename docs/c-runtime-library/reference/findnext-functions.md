---
title: _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
ms.date: 11/04/2016
apiname:
- _wfindnext
- _findnext
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 32d21b310d8a7826fd1d95f806d470a1fb7e492e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518505"
---
# <a name="findnext-findnext32-findnext32i64-findnext64-findnext64i32-findnexti64-wfindnext-wfindnext32-wfindnext32i64-wfindnext64-wfindnext64i32-wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

Najít další název, pokud existuje, který odpovídá *nezačíná* argument v předchozím volání [_findfirst](findfirst-functions.md)a poté změňte *fileinfo* struktury obsah odpovídajícím způsobem.

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

*Popisovač*<br/>
Hledání popisovač vrácený voláním předchozí **_findfirst**.

*FileInfo*<br/>
Informace o vyrovnávací paměti souboru.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0. V opačném případě vrátí hodnotu -1 a nastaví **errno** na hodnotu, která podstatu tohoto selhání. Možné kódy chyb jsou uvedeny v následující tabulce.

|Hodnota errno|Podmínka|
|-|-|
**EINVAL**|Neplatný parametr: *fileinfo* byl **NULL**. Nebo operační systém vrátil neočekávanou chybu.
**ENOENT**|Nebyly nalezeny žádné odpovídající soubory.
**ENOMEM**|Nedostatek paměti nebo překročila se délka názvu souboru **MAX_PATH**.

Pokud je předán neplatný parametr, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

Je nutné volat [_findclose –](findclose.md) až budete hotovi, buď pomocí **_findfirst** nebo **_findnext** – funkce (nebo všechny varianty). Uvolní prostředky využívané třídou tyto funkce ve vaší aplikaci.

Změny těchto funkcí s **w** předpony jsou širokoznaké verze; v opačném případě jsou stejné pro odpovídající funkce jednobajtové.

Variace tyto funkce podporují 32bitové nebo 64bitové čas typech a velikostech 32bitová nebo 64bitová verze souboru. První číselná přípona (**32** nebo **64**) označuje velikost času používá typ; druhý přípony je buď **i32** nebo **i64**, označující, zda velikost souboru je reprezentován jako 32bitový nebo 64bitové celé číslo. Další informace o tom, které podporují verze 32bitové a 64bitové čas typy a velikosti souborů najdete v následující tabulce. Změny, které používají typ času 64-bit povolit data vytvoření souboru nahoru rozdíl lze vyjádřit pomocí 23:59:59, 31 prosince 3000 UTC. zatímco těm, kteří používají pouze typy 32-bit čas představuje data do 23:59:59 18. ledna 2038 UTC. Půlnoc 1. ledna 1970 je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.

Pokud nemáte konkrétní důvod používat verze, které explicitně zadat velikost v době, použijte **_findnext** nebo **_wfindnext –** nebo pokud potřebujete podporovat velikost souboru je větší než 3 GB, použijte **_ findnexti64 –** nebo **_wfindnexti64 –**. Všechny tyto funkce používají typ času 64-bit. V předchozích verzích tyto funkce použít typ času 32-bit. Pokud je to zásadní změny pro aplikaci, můžete třeba definovat **_USE_32BIT_TIME_T** staré chování. Pokud **_USE_32BIT_TIME_T** je definován, **_findnext**, **_finnexti64** a jejich odpovídající verze Unicode použít čas 32-bit.

### <a name="time-type-and-file-length-type-variations-of-findnext"></a>Typ času a soubor délka typ Variant _findnext

|Funkce|**_USE_32BIT_TIME_T** definované?|Typ času|Délka typu souboru|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext**, **_wfindnext –**|Nedefinovaná.|64bitových|32bitová|
|**_findnext**, **_wfindnext –**|Definice|32bitová|32bitová|
|**_findnext32 –**, **_wfindnext32 –**|Není ovlivněna definici makra|32bitová|32bitová|
|**_findnext64 –**, **_wfindnext64 –**|Není ovlivněna definici makra|64bitových|64bitových|
|**_findnexti64 –**, **_wfindnexti64 –**|Nedefinovaná.|64bitových|64bitových|
|**_findnexti64 –**, **_wfindnexti64 –**|Definice|32bitová|64bitových|
|**_findnext32i64 –**, **_wfindnext32i64 –**|Není ovlivněna definici makra|32bitová|64bitových|
|**_findnext64i32 –**, **_wfindnext64i32 –**|Není ovlivněna definici makra|64bitových|32bitová|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindnext –**|**_findnext**|**_findnext**|**_wfindnext**|
|**_tfindnext32 –**|**_findnext32**|**_findnext32**|**_wfindnext32**|
|**_tfindnext64 –**|**_findnext64**|**_findnext64**|**_wfindnext64**|
|**_tfindnexti64 –**|**_findnexti64**|**_findnexti64**|**_wfindnexti64**|
|**_tfindnext32i64 –**|**_findnext32i64**|**_findnext32i64**|**_wfindnext32i64**|
|**_tfindnext64i32 –**|**_findnext64i32**|**_findnext64i32**|**_wfindnext64i32**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_findnext**|\<IO.h >|
|**_findnext32**|\<IO.h >|
|**_findnext64**|\<IO.h >|
|**_findnexti64**|\<IO.h >|
|**_findnext32i64**|\<IO.h >|
|**_findnext64i32**|\<IO.h >|
|**_wfindnext**|\<IO.h > nebo \<wchar.h >|
|**_wfindnext32**|\<IO.h > nebo \<wchar.h >|
|**_wfindnext64**|\<IO.h > nebo \<wchar.h >|
|**_wfindnexti64**|\<IO.h > nebo \<wchar.h >|
|**_wfindnext32i64**|\<IO.h > nebo \<wchar.h >|
|**_wfindnext64i32**|\<IO.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Systémová volání](../../c-runtime-library/system-calls.md)<br/>
[Funkce hledání názvů souborů](../../c-runtime-library/filename-search-functions.md)<br/>
