---
title: _close
ms.date: 11/04/2016
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
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
ms.openlocfilehash: faea008903136e8abdc39297672b31800ada796d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528021"
---
# <a name="close"></a>_close

Soubor se zavře.

## <a name="syntax"></a>Syntaxe

```C
int _close(
   int fd
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Popisovač souboru odkazující na otevřený soubor.

## <a name="return-value"></a>Návratová hodnota

**_Zavřít** vrátí hodnotu 0, pokud soubor byl úspěšně uzavřen. Návratová hodnota-1 označuje chybu.

## <a name="remarks"></a>Poznámky

**_Zavřít** funkce zavře soubor přidružený k *fd*.

Popisovače souborů a podkladové popisovač souboru operačního systému jsou zavřené. Proto není nutné volat **CloseHandle** Pokud soubor byl původně otevřen použitím funkce Win32 **CreateFile** a převedeny na popisovač souboru pomocí **_open_osfhandle –**.

Tato funkce ověřuje své parametry. Pokud *fd* je popisovače souborů, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a **errno** je nastavena na **EBADF**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_close**|\<IO.h >|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_Otevřít](open-wopen.md).

## <a name="see-also"></a>Viz také:

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
