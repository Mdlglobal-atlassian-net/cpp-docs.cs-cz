---
title: _strdup_dbg, _wcsdup_dbg
ms.date: 11/04/2016
apiname:
- _strdup_dbg
- _wcsdup_dbg
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
apitype: DLLExport
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
ms.openlocfilehash: 3092c27df1e39c7b719f6e7037efa202d29c9e81
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353875"
---
# <a name="strdupdbg-wcsdupdbg"></a>_strdup_dbg, _wcsdup_dbg

Verze [_strdup – a _wcsdup –](strdup-wcsdup-mbsdup.md) , které používají ladicí verze **malloc**.

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
Řetězec zakončený hodnotou Null zdroje.

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*linenumber*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace přidělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na umístění úložiště pro kopírované řetězec nebo **NULL** pokud nejde přidělit úložiště.

## <a name="remarks"></a>Poznámky

**_Strdup_dbg –** a **_wcsdup_dbg –** funkce jsou stejné jako **_strdup –** a **_wcsdup –** s tím rozdílem, že když **_ LADĚNÍ** je definován, tyto funkce používají ladicí verze **malloc**, **_malloc_dbg**, přidělení paměti pro duplicitní řetězce. Informace o ladění funkcí **_malloc_dbg**, naleznete v tématu [_malloc_dbg](malloc-dbg.md).

Chcete-li explicitně volat tyto funkce ve většině případů nepotřebujete. Místo toho můžete definovat příznak **_CRTDBG_MAP_ALLOC**. Když **_CRTDBG_MAP_ALLOC** je definován, jsou volání **_strdup –** a **_wcsdup –** budou přemapovány na **_strdup_dbg –** a **_ wcsdup_dbg –**, se *blockType* nastavena na **_NORMAL_BLOCK**. Proto není potřeba explicitně volat tyto funkce, pokud chcete označit jako bloky haldy **_CLIENT_BLOCK**. Další informace o typech bloku, naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup_dbg**|**_strdup_dbg**|**_mbsdup**|**_wcsdup_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strdup_dbg**, **_wcsdup_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze ladění knihoven [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdup, _wcsdup, _mbsdup](strdup-wcsdup-mbsdup.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
