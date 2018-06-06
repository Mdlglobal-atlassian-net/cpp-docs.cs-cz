---
title: _get_osfhandle – | Microsoft Docs
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15bddcf3d94935f56fa2e23b6ebd0398ed379c54
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569846"
---
# <a name="getosfhandle"></a>_get_osfhandle

Načte popisovač souboru operačního systému, který je přidružen popisovač zadaný soubor.

## <a name="syntax"></a>Syntaxe

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Existující popisovače souborů.

## <a name="return-value"></a>Návratová hodnota

Vrátí popisovač souboru operačního systému, pokud *fd* je platný. Jinak se obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu **INVALID_HANDLE_VALUE** (-1) a nastaví **errno** k **ebadf –**, označující neplatný popisovač souboru. Abyste se vyhnuli upozornění kompilátoru při výsledek se používá v rutiny, které očekávají popisovač souboru Win32, vysílat **zpracování** typu.

## <a name="remarks"></a>Poznámky

Zavřete soubor, jehož popisovač souboru operačního systému (OS) se získávají pomocí **_get_osfhandle –**, volání [_close –](close.md) na popisovače souborů *fd*. Nevolejte **funkce CloseHandle** na návratovou hodnotu této funkce. Je vlastníkem základní popisovač souboru *fd* popisovače souborů a při zavření [_close –](close.md) se volá na *fd*. Pokud je vlastníkem popisovače souborů **souboru \***  datového proudu, pak volání [fclose –](fclose-fcloseall.md) na který **soubor \***  datový proud se zavře popisovač souboru a základní popisovač souboru operačního systému. V takovém případě Nevolejte [_close –](close.md) na popisovače souborů.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_osfhandle**|\<IO.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
