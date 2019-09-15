---
title: _fullpath_dbg, _wfullpath_dbg
ms.date: 11/04/2016
api_name:
- _wfullpath_dbg
- _fullpath_dbg
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
- wfullpath_dbg
- _wfullpath_dbg
- _fullpath_dbg
- fullpath_dbg
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
ms.openlocfilehash: 9271e26bcf4a78ff8d2e4fcf108f1e483c22c1d7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956316"
---
# <a name="_fullpath_dbg-_wfullpath_dbg"></a>_fullpath_dbg, _wfullpath_dbg

Verze [_fullpath, _wfullpath](fullpath-wfullpath.md) , které používají ladicí verzi systému \ **k přidělení** paměti.

## <a name="syntax"></a>Syntaxe

```C
char *_fullpath_dbg(
   char *absPath,
   const char *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wfullpath_dbg(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*absPath*<br/>
Ukazatel na vyrovnávací paměť obsahující absolutní nebo úplný název cesty nebo **hodnotu null**.

*relPath*<br/>
Název relativní cesty

*maxLength*<br/>
Maximální délka vyrovnávací paměti názvu absolutní cesty (*absPath*). Tato délka je v bajtech pro **_fullpath** , ale v různých znacích (**wchar_t**) pro **_wfullpath**.

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval operaci přidělení, nebo **hodnotu null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace přidělení, nebo **hodnota null**.

## <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí ukazatel na vyrovnávací paměť obsahující absolutní název cesty (*absPath*). Pokud se vyskytne chyba (například pokud hodnota předaná v *relPath* zahrnuje písmeno jednotky, které není platné nebo se nedá najít, nebo pokud je délka vytvořeného absolutního názvu cesty (*absPath*) větší než hodnota *MaxLength*, vrátí funkce hodnotu  **Hodnota NULL**.

## <a name="remarks"></a>Poznámky

Funkce **_fullpath_dbg** a **_wfullpath_dbg** jsou stejné jako **_fullpath** a **_wfullpath** s tím rozdílem, že pokud je definována **_DEBUG** , používají tyto funkce ladicí verzi, **_malloc_dbg**, pro přidělení paměti, pokud je **hodnota null** předána jako první parametr. Informace o funkcích ladění pro **_malloc_dbg**najdete v tématu [_malloc_dbg](malloc-dbg.md).

Tyto funkce není nutné volat explicitně ve většině případů. Místo toho můžete definovat příznak **_CRTDBG_MAP_ALLOC** . Pokud je definována **_CRTDBG_MAP_ALLOC** , volání **_fullpath** a **_wfullpath** jsou přemapována na **_Fullpath_dbg** a **_Wfullpath_dbg**v uvedeném pořadí s *blockType* nastavenou na **_NORMAL_BLOCK**. Proto nemusíte tyto funkce volat explicitně, pokud nechcete označit bloky haldy jako **_CLIENT_BLOCK**. Další informace naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath_dbg**|**_fullpath_dbg**|**_fullpath_dbg**|**_wfullpath_dbg**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fullpath_dbg**|\<crtdbg.h>|
|**_wfullpath_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
