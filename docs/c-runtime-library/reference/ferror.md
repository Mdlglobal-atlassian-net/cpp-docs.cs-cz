---
title: ferror
ms.date: 11/04/2016
apiname:
- ferror
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
- ferror
helpviewer_keywords:
- ferror function
- streams, testing for errors
- errors [C++], testing for stream
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
ms.openlocfilehash: 2be90ffe8a135b4108abd9504099bd2f6c28f249
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587886"
---
# <a name="ferror"></a>ferror

Testy pro chybu na datový proud.

## <a name="syntax"></a>Syntaxe

```C
int ferror(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

Pokud nedojde k žádné chybě na *stream*, **ferror** vrátí hodnotu 0. V opačném případě vrací nenulovou hodnotu. Pokud je datový proud **NULL**, **ferror** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí hodnotu 0.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších chybových kódech.

## <a name="remarks"></a>Poznámky

**Ferror** rutinní (implementovány jako funkce i makra) test pro čtení nebo zápis chyby v souboru přidruženého k *stream*. Pokud došlo k chybě, indikátor chyby pro datový proud zůstane nastavený, dokud datový proud je uzavřen nebo převinuta, nebo dokud **clearerr –** je volána před ním.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**ferror**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [feof](feof.md).

## <a name="see-also"></a>Viz také:

[Zpracování chyb](../../c-runtime-library/error-handling-crt.md)<br/>
[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
