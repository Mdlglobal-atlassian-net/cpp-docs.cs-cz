---
title: ferror
ms.date: 4/2/2020
api_name:
- ferror
- _o_ferror
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
- ferror
helpviewer_keywords:
- ferror function
- streams, testing for errors
- errors [C++], testing for stream
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
ms.openlocfilehash: 8a5e0bfac2069ed016253de4276e772ea7912605
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920156"
---
# <a name="ferror"></a>ferror

Testuje chybu v datovém proudu.

## <a name="syntax"></a>Syntaxe

```C
int ferror(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

Pokud u *streamu*nedošlo k žádné **chybě, potom** vrátí ' 0 '. V opačném případě vrátí nenulovou hodnotu. Pokud má datový proud **hodnotu null**, vyvolá **odvození** neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí hodnotu 0.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Rutina **doporučující** (implementovaná jako funkce a jako makro) testuje chybu čtení nebo zápisu v souboru přidruženém ke *streamu*. Pokud došlo k chybě, indikátor chyb pro datový proud zůstane nastavený, dokud datový proud není uzavřený nebo předaný, nebo dokud na něj **clearerr** nevolá.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**ferror**|\<stdio. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [feof](feof.md).

## <a name="see-also"></a>Viz také

[Zpracování chyb](../../c-runtime-library/error-handling-crt.md)<br/>
[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
