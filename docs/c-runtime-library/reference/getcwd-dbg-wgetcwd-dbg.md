---
title: _getcwd_dbg, _wgetcwd_dbg
ms.date: 11/04/2016
apiname:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 9616c5f7e29b4f003d3943ba058d1f1a1d5adb5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521135"
---
# <a name="getcwddbg-wgetcwddbg"></a>_getcwd_dbg, _wgetcwd_dbg

Ladicí verze [_getcwd _wgetcwd –](getcwd-wgetcwd.md) funkcí (k dispozici pouze při ladění).

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

*Vyrovnávací paměti*<br/>
Umístění úložiště pro danou cestu.

*MAXLEN*<br/>
Maximální délka cesty ve znacích: **char** pro **_getcwd_dbg** a **wchar_t** pro **_wgetcwd_dbg**.

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, ve kterém se požadovaná operace rozdělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na *vyrovnávací paměti*. A **NULL** vrátit hodnota označuje chybu, a **errno** je nastaven buď na **ENOMEM**, označující, že není dostatek paměti k přidělení *maxlen* bajtů (když **NULL** argument je zadána jako *vyrovnávací paměti*), nebo **ERANGE**, označující, že cesta je delší než *maxlen*  znaků.

Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Getcwd_dbg** a **_wgetcwd_dbg** funkce jsou stejné jako **_getcwd** a **_wgetcwd –** s tím rozdílem, že když **_ LADĚNÍ** je definován, tyto funkce používají ladicí verze **malloc** a **_malloc_dbg** přidělení paměti, pokud **NULL** je předán jako první parametr. Další informace najdete v tématu [_malloc_dbg](malloc-dbg.md).

Chcete-li explicitně volat tyto funkce ve většině případů nepotřebujete. Místo toho můžete definovat **_CRTDBG_MAP_ALLOC** příznak. Když **_CRTDBG_MAP_ALLOC** je definován, jsou volání **_getcwd** a **_wgetcwd –** budou přemapovány na **_getcwd_dbg** a **_ wgetcwd_dbg –**, se *blockType* nastavena na **_NORMAL_BLOCK**. Proto není potřeba explicitně volat tyto funkce, pokud chcete označit jako bloky haldy **_CLIENT_BLOCK**. Další informace najdete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

## <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd_dbg**|**_getcwd_dbg**|**_getcwd_dbg**|**_wgetcwd_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getcwd_dbg**|\<crtdbg.h>|
|**_wgetcwd_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
