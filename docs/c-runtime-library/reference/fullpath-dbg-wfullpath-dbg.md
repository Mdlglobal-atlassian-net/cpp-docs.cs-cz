---
title: _fullpath_dbg, _wfullpath_dbg
ms.date: 11/04/2016
apiname:
- _wfullpath_dbg
- _fullpath_dbg
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
ms.openlocfilehash: b84c5b77d0a9bfb298d4c597e372cd39a92441f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488007"
---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg, _wfullpath_dbg

Verze [_fullpath – _wfullpath –](fullpath-wfullpath.md) , které používají ladicí verze **malloc** přidělení paměti.

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
Ukazatel do vyrovnávací paměti obsahující název absolutní nebo úplnou cestu nebo **NULL**.

*relPath*<br/>
Relativní cesta.

*maxLength*<br/>
Maximální délka vyrovnávací paměti název absolutní cesta (*absPath*). Se délka v bajtech pro **_fullpath –** , ale v široké znaky (**wchar_t**) pro **_wfullpath –**.

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, ve kterém se požadovaná operace rozdělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí ukazatel do vyrovnávací paměti, který obsahuje absolutní cesta (*absPath*). Pokud dojde k chybě (například, pokud hodnota předaná v *relPath* obsahuje písmeno jednotky, který není platný nebo se nedá najít, nebo pokud délka názvu vytvořená absolutní cesta (*absPath*) je větší než *maxLength*) funkce vrátí **NULL**.

## <a name="remarks"></a>Poznámky

**_Fullpath_dbg –** a **_wfullpath_dbg –** funkce jsou stejné jako **_fullpath –** a **_wfullpath –** s tím rozdílem, že když **_DEBUG** je definován, tyto funkce používají ladicí verze **malloc**, **_malloc_dbg**, přidělení paměti, pokud **NULL** je předán jako první parametr. Informace o ladění funkcí **_malloc_dbg**, naleznete v tématu [_malloc_dbg](malloc-dbg.md).

Chcete-li explicitně volat tyto funkce ve většině případů nepotřebujete. Místo toho můžete definovat **_CRTDBG_MAP_ALLOC** příznak. Když **_CRTDBG_MAP_ALLOC** je definován, jsou volání **_fullpath –** a **_wfullpath –** budou přemapovány na **_fullpath_dbg –** a **_wfullpath_dbg –**, se *blockType* nastavena na **_NORMAL_BLOCK**. Proto není potřeba explicitně volat tyto funkce, pokud chcete označit jako bloky haldy **_CLIENT_BLOCK**. Další informace najdete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath_dbg**|**_fullpath_dbg**|**_fullpath_dbg**|**_wfullpath_dbg**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fullpath_dbg**|\<crtdbg.h>|
|**_wfullpath_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
