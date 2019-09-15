---
title: _strdup_dbg, _wcsdup_dbg
ms.date: 11/04/2016
api_name:
- _strdup_dbg
- _wcsdup_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcsdup_dbg
- strdup_dbg
- _strdup_dbg
- wcsdup_dbg
helpviewer_keywords:
- _wcsdup_dbg function
- stdup_dbg function
- copying strings
- duplicating strings
- strings [C++], copying
- strings [C++], duplicating
- _strdup_dbg function
- wcsdup_dbg function
ms.assetid: 681db70c-d124-43ab-b83e-5eeea9035097
ms.openlocfilehash: 9f7d4fd8781269ee37f7515fdcab72e5195fdf00
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958191"
---
# <a name="_strdup_dbg-_wcsdup_dbg"></a>_strdup_dbg, _wcsdup_dbg

Verze [_strdup a _wcsdup](strdup-wcsdup-mbsdup.md) , které používají ladicí verzi **systému.**

## <a name="syntax"></a>Syntaxe

```C
char *_strdup_dbg(
   const char *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wcsdup_dbg(
   const wchar_t *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*strSource*<br/>
Zdrojový řetězec zakončený hodnotou null.

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval operaci přidělení, nebo **hodnota null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace přidělení, nebo **hodnota null**.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na umístění úložiště pro zkopírovaný řetězec nebo **hodnotu null** , pokud nelze přidělit úložiště.

## <a name="remarks"></a>Poznámky

Funkce **_strdup_dbg** a **_wcsdup_dbg** jsou stejné jako **_strdup** a **_wcsdup** s tím rozdílem, že při definování **_DEBUG** používají tyto funkce ladicí verzi typu, **_malloc_dbg** **, které**se mají přidělit. paměť pro duplicitní řetězec. Informace o funkcích ladění pro **_malloc_dbg**najdete v tématu [_malloc_dbg](malloc-dbg.md).

Tyto funkce není nutné volat explicitně ve většině případů. Místo toho můžete definovat příznak **_CRTDBG_MAP_ALLOC**. Pokud je definována **_CRTDBG_MAP_ALLOC** , volání **_strdup** a **_wcsdup** jsou přemapována na **_Strdup_dbg** a **_Wcsdup_dbg**v uvedeném pořadí s *blockType* nastavenou na **_NORMAL_BLOCK**. Proto nemusíte tyto funkce volat explicitně, pokud nechcete označit bloky haldy jako **_CLIENT_BLOCK**. Další informace o typech bloků naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup_dbg**|**_strdup_dbg**|**_mbsdup**|**_wcsdup_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strdup_dbg**, **_wcsdup_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny ladicí verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdup, _wcsdup, _mbsdup](strdup-wcsdup-mbsdup.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
