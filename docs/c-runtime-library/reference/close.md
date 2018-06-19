---
title: _close – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _close
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
- _close
dev_langs:
- C++
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eabf084d2e4dd7e280c0ff730d1ec34d86f1ed98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394194"
---
# <a name="close"></a>_close

Zavře soubor.

## <a name="syntax"></a>Syntaxe

```C
int _close(
   int fd
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Popisovače souborů na otevření souboru.

## <a name="return-value"></a>Návratová hodnota

**_close –** vrátí hodnotu 0, pokud soubor se zavřel úspěšně. Vrácená hodnota -1 označuje chybu.

## <a name="remarks"></a>Poznámky

**_Close –** funkce zavře soubor přidružený k *fd*.

Jsou uzavřeny popisovače souborů a základní popisovač souboru. Proto není nutné volat **funkce CloseHandle** Pokud soubor byl původně otevřít pomocí funkce Win32 **CreateFile** a převést na popisovač souboru pomocí **_open_osfhandle –**.

Tato funkce ověří jeho parametry. Pokud *fd* popisovač chybného souboru, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a **errno** je nastaven na **ebadf –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_close**|\<IO.h >|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_Otevřít](open-wopen.md).

## <a name="see-also"></a>Viz také

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
