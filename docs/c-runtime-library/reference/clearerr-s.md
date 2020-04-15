---
title: clearerr_s
ms.date: 4/2/2020
api_name:
- clearerr_s
- _o_clearerr_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- clearerr_s
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
ms.openlocfilehash: a8f8978b9d46d8d903f8256424d47c84bec649ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350048"
---
# <a name="clearerr_s"></a>clearerr_s

Obnoví indikátor chyby pro datový proud. Toto je verze [jasnější](clearerr.md) s vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t clearerr_s(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Proudu*<br/>
Ukazatel na **strukturu SOUBOR**

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; **EINVAL,** pokud *je datový proud* **NULL**.

## <a name="remarks"></a>Poznámky

Funkce **clearerr_s** resetuje indikátor chyby a indikátor konce souboru pro *datový proud*. Indikátory chyb nejsou automaticky vymazány. po nastavení indikátoru chyby pro zadaný datový proud operace na tomto datovém proudu nadále vracet chybovou hodnotu, dokud **clearerr_s**, **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**, nebo [převinout zpět](rewind.md) je volána.

Pokud je *datový proud* **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v části [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **Funkce EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**clearerr_s**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_clearerr_s.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   errno_t err;

   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }
}
```

### <a name="input"></a>Vstup

```Input
n
```

### <a name="output"></a>Výstup

```Output
Write error: Bad file descriptor
Will input cause an error? n
```

## <a name="see-also"></a>Viz také

[Zpracování chyb](../../c-runtime-library/error-handling-crt.md)<br/>
[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
