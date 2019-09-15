---
title: _getcwd_dbg, _wgetcwd_dbg
ms.date: 11/04/2016
api_name:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
ms.openlocfilehash: 3eb318b9b2faa8716abdd26eafa926c8072b5614
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955284"
---
# <a name="_getcwd_dbg-_wgetcwd_dbg"></a>_getcwd_dbg, _wgetcwd_dbg

Ladicí verze funkcí [_getcwd, _wgetcwd](getcwd-wgetcwd.md) (k dispozici pouze během ladění).

## <a name="syntax"></a>Syntaxe

```C
char *_getcwd_dbg(
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetcwd_dbg(
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Umístění úložiště pro cestu

*maxlen*<br/>
Maximální délka cesty ve znacích: **char** pro **_getcwd_dbg** a **wchar_t** pro **_wgetcwd_dbg**.

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval operaci přidělení, nebo **hodnotu null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde byla požadována operace přidělení, nebo **hodnota null**.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na *vyrovnávací paměť*. Návratová hodnota **null** označuje chybu a **errno** je nastavená na **ENOMEM**, což značí, že není dostatek paměti k přidělení *MAXLEN* bajtů (když je jako *vyrovnávací paměť*uveden argument **null** ) nebo **ERANGE** , což značí, že cesta je delší než *MAXLEN* znaků.

Další informace najdete v tématech [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_getcwd_dbg** a **_wgetcwd_dbg** jsou stejné jako **_getcwd** a **_wgetcwd** s tím rozdílem, že při definování **_DEBUG** používají tyto funkce ladicí **verzi typu \** a **_malloc_dbg** pro Přidělte paměť, pokud je **hodnota null** předána jako první parametr. Další informace najdete v tématu [_malloc_dbg](malloc-dbg.md).

Tyto funkce není nutné volat explicitně ve většině případů. Místo toho můžete definovat příznak **_CRTDBG_MAP_ALLOC** . Pokud je definována **_CRTDBG_MAP_ALLOC** , volání **_getcwd** a **_wgetcwd** jsou přemapována na **_Getcwd_dbg** a **_Wgetcwd_dbg**v uvedeném pořadí s *blockType* nastavenou na **_NORMAL_BLOCK**. Proto nemusíte tyto funkce volat explicitně, pokud nechcete označit bloky haldy jako **_CLIENT_BLOCK**. Další informace naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

## <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd_dbg**|**_getcwd_dbg**|**_getcwd_dbg**|**_wgetcwd_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getcwd_dbg**|\<crtdbg.h>|
|**_wgetcwd_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
