---
title: _findfirst, _findfirst32 –, _findfirst32i64 –, _findfirst64 –, _findfirst64i32 –, _findfirsti64 –, _wfindfirst –, _wfindfirst32 –, _wfindfirst32i64 –, _wfindfirst64 –, _wfindfirst64i32 –, _wfindfirsti64 –
ms.date: 11/04/2016
apiname:
- _findfirst
- _wfindfirst
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
ms.openlocfilehash: ceaa8fea4414bab4bbb035aa4525b415ca7ac0b8
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331435"
---
# <a name="findfirst-findfirst32-findfirst32i64-findfirst64-findfirst64i32-findfirsti64-wfindfirst-wfindfirst32-wfindfirst32i64-wfindfirst64-wfindfirst64i32-wfindfirsti64"></a>_findfirst, _findfirst32 –, _findfirst32i64 –, _findfirst64 –, _findfirst64i32 –, _findfirsti64 –, _wfindfirst –, _wfindfirst32 –, _wfindfirst32i64 –, _wfindfirst64 –, _wfindfirst64i32 –, _wfindfirsti64 –

Zadání informací o první výskyt název souboru, který odpovídá zadané v souboru *nezačíná* argument.

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

*určení souboru*<br/>
Specifikace souboru cíl (může obsahovat zástupné znaky).

*FileInfo*<br/>
Informace o vyrovnávací paměti souboru.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného ověření **_findfirst** vrátí popisovač jedinečný hledání souboru nebo skupiny souborů, které odpovídají *nezačíná* specifikace, které lze použít v následných volání [_ FindNext](findnext-functions.md) nebo [_findclose –](findclose.md). V opačném případě **_findfirst** vrátí hodnotu -1 a nastaví **errno** na jednu z následujících hodnot.

| Hodnota errno | Podmínka |
|-|-|
| **EINVAL** | Neplatný parametr: *nezačíná* nebo *fileinfo* byl **NULL**. Nebo operační systém vrátil neočekávanou chybu. |
| **ENOENT** | Specifikace souboru, který se neshoduje. |
| **ENOMEM** | Nedostatek paměti. |
| **EINVAL** | Neplatný soubor specifikace názvu nebo názvu souboru byla větší než **MAX_PATH**. |

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pokud je předán neplatný parametr, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

Je nutné volat [_findclose –](findclose.md) po dokončení buď **_findfirst** nebo [_findnext](findnext-functions.md) – funkce (nebo všechny varianty). Tím se uvolní prostředky využívané třídou tyto funkce ve vaší aplikaci.

Změny těchto funkcí, které mají **w** předpony jsou širokoznaké verze; v opačném případě jsou stejné pro odpovídající funkce jednobajtové.

Variace tyto funkce podporují 32bitové nebo 64bitové čas typech a velikostech 32bitová nebo 64bitová verze souboru. První číselnou příponou (**32** nebo **64**) označuje velikost typu time; druhý přípony je buď **i32** nebo **i64**a označuje Určuje, zda velikost souboru je reprezentován jako 32bitový nebo 64bitové celé číslo. Další informace o tom, které podporují verze 32bitové a 64bitové čas typy a velikosti souborů najdete v následující tabulce. **I32** nebo **i64** přípona je vynechána, pokud je stejná jako velikost typu čas, takže **_findfirst64 –** podporuje také 64bitová verze souboru délky a **_findfirst32 –**  podporuje pouze 32bitové souboru délky.

Tyto funkce používají různé formy **_finddata_t –** strukturu pro *fileinfo* parametru. Další informace o struktuře najdete v tématu [název souboru hledat funkce](../../c-runtime-library/filename-search-functions.md).

Změny, které používají typ času 64-bit povolit vytvoření souboru data vyjadřují až do 23:59:59, 31 prosince 3000 UTC. Ty, které používají typy 32-bit čas představuje data jenom do 23:59:59 18. ledna 2038 UTC. Půlnoc 1. ledna 1970 je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.

Pokud nemáte konkrétní důvod používat verze, které explicitně zadat velikost v době, použijte **_findfirst** nebo **_wfindfirst –** nebo pokud potřebujete podporovat máte soubory větší než 3 GB, použijte **_ findfirsti64 –** nebo **_wfindfirsti64 –**. Všechny tyto funkce používají typ času 64-bit. V dřívějších verzích tyto funkce použít typ času 32-bit. Pokud je to zásadní změny pro aplikaci, můžete třeba definovat **_USE_32BIT_TIME_T** vrátit zpět původní chování. Pokud **_USE_32BIT_TIME_T** je definován, **_findfirst**, **_finfirsti64**, a jejich odpovídající verze Unicode použít čas 32-bit.

### <a name="time-type-and-file-length-type-variations-of-findfirst"></a>Typ času a soubor délka typ Variant _findfirst

|Funkce|**_USE_32BIT_TIME_T** definované?|Typ času|Délka typu souboru|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst**, **_wfindfirst –**|Nedefinovaná.|64bitových|32bitová|
|**_findfirst**, **_wfindfirst –**|Definice|32bitová|32bitová|
|**_findfirst32 –**, **_wfindfirst32 –**|Není ovlivněna definici makra|32bitová|32bitová|
|**_findfirst64 –**, **_wfindfirst64 –**|Není ovlivněna definici makra|64bitových|64bitových|
|**_findfirsti64 –**, **_wfindfirsti64 –**|Nedefinovaná.|64bitových|64bitových|
|**_findfirsti64 –**, **_wfindfirsti64 –**|Definice|32bitová|64bitových|
|**_findfirst32i64 –**, **_wfindfirst32i64 –**|Není ovlivněna definici makra|32bitová|64bitových|
|**_findfirst64i32 –**, **_wfindfirst64i32 –**|Není ovlivněna definici makra|64bitových|32bitová|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindfirst –**|**_findfirst**|**_findfirst**|**_wfindfirst**|
|**_tfindfirst32 –**|**_findfirst32**|**_findfirst32**|**_wfindfirst32**|
|**_tfindfirst64 –**|**_findfirst64**|**_findfirst64**|**_wfindfirst64**|
|**_tfindfirsti64 –**|**_findfirsti64**|**_findfirsti64**|**_wfindfirsti64**|
|**_tfindfirst32i64 –**|**_findfirst32i64**|**_findfirst32i64**|**_wfindfirst32i64**|
|**_tfindfirst64i32 –**|**_findfirst64i32**|**_findfirst64i32**|**_wfindfirst64i32**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_findfirst**|\<IO.h >|
|**_findfirst32**|\<IO.h >|
|**_findfirst64**|\<IO.h >|
|**_findfirsti64**|\<IO.h >|
|**_findfirst32i64**|\<IO.h >|
|**_findfirst64i32**|\<IO.h >|
|**_wfindfirst**|\<IO.h > nebo \<wchar.h >|
|**_wfindfirst32**|\<IO.h > nebo \<wchar.h >|
|**_wfindfirst64**|\<IO.h > nebo \<wchar.h >|
|**_wfindfirsti64**|\<IO.h > nebo \<wchar.h >|
|**_wfindfirst32i64**|\<IO.h > nebo \<wchar.h >|
|**_wfindfirst64i32**|\<IO.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Systémová volání](../../c-runtime-library/system-calls.md)<br/>
[Funkce hledání názvů souborů](../../c-runtime-library/filename-search-functions.md)<br/>
