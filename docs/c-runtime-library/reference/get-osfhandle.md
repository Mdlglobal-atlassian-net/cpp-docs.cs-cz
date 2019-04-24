---
title: _get_osfhandle
ms.date: 05/29/2018
apiname:
- _get_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: beab4e4308bc7bcde287366b78671f61a89f8827
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332205"
---
# <a name="getosfhandle"></a>_get_osfhandle

Načte popisovač souboru operačního systému, který je spojen s popisovačem zadaného souboru.

## <a name="syntax"></a>Syntaxe

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Parametry

*fd*<br/>
Existující popisovač souboru.

## <a name="return-value"></a>Návratová hodnota

Vrátí popisovač souboru operačního systému, pokud *fd* je platný. V opačném případě je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrací **INVALID_HANDLE_VALUE** (-1) a nastaví **errno** k **EBADF**, určující neplatný popisovač souboru. Aby se zabránilo upozornění kompilátoru při použití vráceného výsledku v rutin, které očekávají popisovač souboru Win32, přetypujte ji na **zpracování** typu.

## <a name="remarks"></a>Poznámky

Zavřete soubor, jehož popisovač souboru operačního systému (OS) se získá **_get_osfhandle –**, volání [_Zavřít](close.md) na popisovač souboru *fd*. Nevolejte **CloseHandle** na návratový typ této funkce. Vlastní podkladové popisovač souboru operačního systému *fd* popisovač souboru a je uzavřen, když [_Zavřít](close.md) je volán na *fd*. Pokud popisovač souboru je vlastněna `FILE *` datový proud a následným voláním [fclose –](fclose-fcloseall.md) zabývat `FILE *` datový proud se zavře popisovače souborů a podkladové popisovač souboru operačního systému. V takovém případě Nevolejte [_Zavřít](close.md) na popisovač souboru.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
