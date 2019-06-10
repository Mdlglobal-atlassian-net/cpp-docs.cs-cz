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
ms.openlocfilehash: cc3b50e3d3f65bee83b8df83aa0adb5c8694e35a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821658"
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

Vrátí popisovač souboru operačního systému, pokud *fd* je platný. V opačném případě je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí **INVALID_HANDLE_VALUE** (-1). Nastaví také **errno** k **EBADF**, která neplatný popisovač souboru. Abyste zabránili upozornění při použití vráceného výsledku jako popisovač souboru Win32, přetypujte ji na **zpracování** typu.

> [!NOTE]
> Když **stdin**, **stdout**, a **stderr** nejsou přidružené k stream (například v aplikaci Windows bez okna konzoly), hodnoty popisovače souboru Tyto datové proudy jsou vráceny z [_fileno](fileno.md) jako zvláštní hodnota -2. Podobně pokud použijete hodnotu 0, 1 nebo 2 jako parametr popisovače souboru místo výsledku volání **_fileno**, **_get_osfhandle –** také vrátí hodnotu zvláštní hodnota -2, pokud není popisovač souboru přidružen pomocí služby stream a nenastaví **errno**. Ale to není platný soubor popisovač hodnota a následná volání, které se pokoušejí jeho použití jsou pravděpodobně selže.

Další informace o **EBADF** a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Zavřete soubor, jehož popisovač souboru operačního systému (OS) se získá **_get_osfhandle –** , volání [_Zavřít](close.md) na popisovač souboru *fd*. Nikdy neměl volat **CloseHandle** na návratový typ této funkce. Vlastní podkladové popisovač souboru operačního systému *fd* popisovač souboru a je uzavřen, když [_Zavřít](close.md) je volán na *fd*. Pokud popisovač souboru je vlastněna `FILE *` datový proud a následným voláním [fclose –](fclose-fcloseall.md) zabývat `FILE *` datový proud se zavře popisovače souborů a podkladové popisovač souboru operačního systému. V takovém případě Nevolejte [_Zavřít](close.md) na popisovač souboru.

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
[\_open_osfhandle](open-osfhandle.md)
