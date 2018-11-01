---
title: _getdcwd_dbg, _wgetdcwd_dbg
ms.date: 11/04/2016
apiname:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
ms.openlocfilehash: 700cfe732dc390ca59a976694403bb3d91af5980
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547171"
---
# <a name="getdcwddbg-wgetdcwddbg"></a>_getdcwd_dbg, _wgetdcwd_dbg

Ladicí verze [_getdcwd – _wgetdcwd –](getdcwd-wgetdcwd.md) funkcí (k dispozici pouze při ladění).

## <a name="syntax"></a>Syntaxe

```C
char *_getdcwd_dbg(
   int drive,
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetdcwd_dbg(
   int drive,
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Jednotky*<br/>
Název disku.

*Vyrovnávací paměti*<br/>
Umístění úložiště pro danou cestu.

*MAXLEN*<br/>
Maximální délka cesty ve znacích: **char** pro **_getdcwd_dbg –** a **wchar_t** pro **_wgetdcwd_dbg –**.

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, ve kterém se požadovaná operace rozdělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na *vyrovnávací paměti*. A **NULL** vrátit hodnota označuje chybu, a **errno** je nastaven buď na **ENOMEM**, označující, že není dostatek paměti k přidělení *maxlen* bajtů (když **NULL** argument je zadána jako *vyrovnávací paměti*), nebo **ERANGE**, označující, že cesta je delší než *maxlen*  znaků. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Getdcwd_dbg –** a **_wgetdcwd_dbg –** funkce jsou stejné jako **_getdcwd –** a **_wgetdcwd –** s tím rozdílem, že když **_DEBUG** je definován, tyto funkce používají ladicí verze **malloc** a **_malloc_dbg** přidělení paměti, pokud **NULL** je předán jako *vyrovnávací paměti* parametru. Další informace najdete v tématu [_malloc_dbg](malloc-dbg.md).

Chcete-li explicitně volat tyto funkce ve většině případů nepotřebujete. Místo toho můžete definovat **_CRTDBG_MAP_ALLOC** příznak. Když **_CRTDBG_MAP_ALLOC** je definován, jsou volání **_getdcwd –** a **_wgetdcwd –** budou přemapovány na **_getdcwd_dbg –** a **_ wgetdcwd_dbg –**, se *blockType* nastavena na **_NORMAL_BLOCK**. Proto není potřeba explicitně volat tyto funkce, pokud chcete označit jako bloky haldy **_CLIENT_BLOCK**. Další informace najdete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
