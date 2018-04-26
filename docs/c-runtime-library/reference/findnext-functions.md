---
title: _findnext –, _findnext32 –, _findnext32i64 –, _findnext64 –, _findnext64i32 –, _findnexti64 –, _wfindnext –, _wfindnext32 –, _wfindnext32i64 –, _wfindnext64 –, _wfindnext64i32 –, _wfindnexti64 – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65947ef5d8c1cb70e587ae739a7301cbed453448
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="findnext-findnext32-findnext32i64-findnext64-findnext64i32-findnexti64-wfindnext-wfindnext32-wfindnext32i64-wfindnext64-wfindnext64i32-wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

Najít další název, pokud existuje, který odpovídá *specifikace souboru* argument v předchozích volání [_findfirst –](findfirst-functions.md)a poté změňte *fileinfo* struktury obsah odpovídajícím způsobem.

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
Popisovač hledání vrácené z předchozího volání **_findfirst –**.

*FileInfo*<br/>
Vyrovnávací paměť informace o souboru.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0. Jinak vrátí hodnotu -1 a nastaví **errno** na hodnotu, která určuje podstatu tohoto selhání. V následující tabulce jsou uvedeny možné chybové kódy.

|errno – hodnota|Podmínka|
|-|-|
**EINVAL –**|Neplatný parametr: *fileinfo* byla **NULL**. Nebo operační systém vrátil neočekávanou chybu.
**ENOENT –**|Nebyly nalezeny žádné odpovídající soubory.
**ENOMEM –**|Nedostatek paměti nebo překročena délka názvu souboru **hodnotou MAX_PATH**.

Pokud není předán neplatný parametr v těchto funkcí vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

Je třeba volat [_findclose –](findclose.md) po skončení buď pomocí **_findfirst –** nebo **_findnext –** funkci (nebo všechny varianty). Uvolní prostředky využívané třídou tyto funkce ve vaší aplikaci.

Variace tyto funkce s **w** předponu široká charakterová verze; jinak, jsou shodné s odpovídající funkce jednobajtové.

Variace tyto funkce podporují 32bitovou nebo 64bitovou čas typy a velikosti souborů 32bitové nebo 64bitové verze. První číselná přípona (**32** nebo **64**) označuje velikost času typu používaného; druhý přípona buď **i32** nebo **i64**, označující, zda velikost souboru je reprezentována jako 32bitové nebo 64bitové celé číslo. Další informace o tom, které podporují verze 32bitové a 64bitové verze čas typy a velikosti souborů najdete v následující tabulce. Varianty, které používají typu time 64-bit povolit vytváření souborů data, která se vyjádřit až do 23:59:59, 31. prosince 3000, UTC. zatímco ty pomocí jenom pro typy 32-bit čas představují datům až 23:59:59 18 leden 2038 UTC. Půlnoc, 1. ledna 1970, je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.

Pokud nemáte konkrétní důvod používat verze, které explicitně zadat čas velikost, použijte **_findnext –** nebo **_wfindnext –** nebo, pokud potřebujete podporovat velikost souboru je větší než 3 GB, použijte **_ findnexti64 –** nebo **_wfindnexti64 –**. Všechny tyto funkce použijte typ 64-bit času. V předchozích verzích se tyto funkce používají typu time 32-bit. Pokud je to narušující změně pro aplikaci, můžete třeba definovat **_USE_32BIT_TIME_T** staré chování. Pokud **_USE_32BIT_TIME_T** je definován **_findnext –**, **_finnexti64** a jejich odpovídající verze Unicode používají 32bitové čas.

### <a name="time-type-and-file-length-type-variations-of-findnext"></a>Typ času a soubor délka typu Variant _findnext –

|Funkce|**_USE_32BIT_TIME_T** definované?|Typ času|Typ délku souboru|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext –**, **_wfindnext –**|Nejsou definována.|64bitových|32bitová|
|**_findnext –**, **_wfindnext –**|Definované|32bitová|32bitová|
|**_findnext32 –**, **_wfindnext32 –**|Není vliv na definici – makro|32bitová|32bitová|
|**_findnext64 –**, **_wfindnext64 –**|Není vliv na definici – makro|64bitových|64bitových|
|**_findnexti64 –**, **_wfindnexti64 –**|Nejsou definována.|64bitových|64bitových|
|**_findnexti64 –**, **_wfindnexti64 –**|Definované|32bitová|64bitových|
|**_findnext32i64 –**, **_wfindnext32i64 –**|Není vliv na definici – makro|32bitová|64bitových|
|**_findnext64i32 –**, **_wfindnext64i32 –**|Není vliv na definici – makro|64bitových|32bitová|

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

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Systémová volání](../../c-runtime-library/system-calls.md)<br/>
[Funkce hledání názvů souborů](../../c-runtime-library/filename-search-functions.md)<br/>
