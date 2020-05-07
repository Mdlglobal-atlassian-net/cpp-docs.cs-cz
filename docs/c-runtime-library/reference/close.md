---
title: _close
ms.date: 4/2/2020
api_name:
- _close
- _o__close
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _close
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
ms.openlocfilehash: c642820bf1bc2e2afbd14e17832fb3fdb6f865b8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919845"
---
# <a name="_close"></a>_close

Zavře soubor.

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

**_close** vrátí hodnotu 0, pokud byl soubor úspěšně uzavřen. Návratová hodnota-1 označuje chybu.

## <a name="remarks"></a>Poznámky

Funkce **_close** zavře soubor přidružený k *FD*.

Popisovač souboru a podkladový popisovač souboru operačního systému jsou zavřené. Proto není nutné volat **CloseHandle** , pokud byl soubor původně otevřen pomocí funkce Win32 **CreateFile** a převeden na popisovač souboru pomocí **_open_osfhandle**.

Tato funkce ověří své parametry. Pokud je *FD* Chybný popisovač souboru, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí hodnotu-1 a **errno** je nastavena na **EBADF**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_close**|\<IO. h>|\<errno. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad [_open](open-wopen.md).

## <a name="see-also"></a>Viz také

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
