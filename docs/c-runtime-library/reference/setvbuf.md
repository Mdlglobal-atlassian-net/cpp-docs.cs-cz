---
title: setvbuf
ms.date: 4/2/2020
api_name:
- setvbuf
- _o_setvbuf
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
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: 203265a8dd85854bcedd737359b856fdc4cce04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316265"
---
# <a name="setvbuf"></a>setvbuf

Řídí ukládání do vyrovnávací paměti datového proudu a velikost vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```C
int setvbuf(
   FILE *stream,
   char *buffer,
   int mode,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

*Vyrovnávací paměti*<br/>
Uživatelem přidělená vyrovnávací paměť.

*Režimu*<br/>
Režim ukládání do vyrovnávací paměti.

*Velikost*<br/>
Velikost vyrovnávací paměti v bajtů. Povolený rozsah: 2 <= *velikost* <= INT_MAX (2147483647). Interně je hodnota dodaná pro *velikost* zaokrouhlena dolů na nejbližší násobek 2.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je úspěšná.

Pokud *je datový proud* **NULL**nebo pokud *režim* nebo *velikost* není v rámci platné změny, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, vrátí tato funkce -1 a nastaví **errno** na **EINVAL**.

Informace o těchto a dalších kódech chyb naleznete [v tématu _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **setvbuf** umožňuje programu řídit jak ukládání do vyrovnávací paměti, tak velikost vyrovnávací paměti pro *datový proud*. *datový proud* musí odkazovat na otevřený soubor, který od otevření neprošel vstupně-vstupně-va. Pole, na které se ve *vyrovnávací paměti ukazuje,* se používá jako vyrovnávací paměť, pokud není **null**, v takovém případě **setvbuf** používá automaticky přidělenou vyrovnávací paměť *o velikosti*délky /2 \* 2 bajty.

Režim musí být **_IOFBF**, **_IOLBF**nebo **_IONBF**. Pokud je *režim* **_IOFBF** nebo **_IOLBF**, pak *velikost* se používá jako velikost vyrovnávací paměti. Pokud je *režim* **_IONBF**, datový proud je bez vyrovnávací paměti a *velikost* a *vyrovnávací paměť* jsou ignorovány. Hodnoty *pro režim* a jejich význam jsou:

|hodnota *režimu*|Význam|
|-|-|
| **_IOFBF** | Úplné ukládání do vyrovnávací paměti; to znamená, *že vyrovnávací paměť* se používá jako vyrovnávací paměť a *velikost* se používá jako velikost vyrovnávací paměti. Pokud je *vyrovnávací paměť* **null**, automaticky přidělené *velikosti* vyrovnávací paměti bajtů dlouho se používá. |
| **_IOLBF** | U některých systémů to poskytuje vyrovnávací paměť linky. Však pro Win32 chování je stejný jako **_IOFBF** - úplné ukládání do vyrovnávací paměti. |
| **_IONBF** | Bez ohledu na vyrovnávací *paměť* nebo *velikost*se nepoužívá žádná vyrovnávací paměť . |

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_setvbuf.c
// This program opens two streams: stream1
// and stream2. It then uses setvbuf to give stream1 a
// user-defined buffer of 1024 bytes and stream2 no buffer.
//

#include <stdio.h>

int main( void )
{
   char buf[1024];
   FILE *stream1, *stream2;

   if( fopen_s( &stream1, "data1", "a" ) == 0 &&
       fopen_s( &stream2, "data2", "w" ) == 0 )
   {
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )
         printf( "Incorrect type or size of buffer for stream1\n" );
      else
         printf( "'stream1' now has a buffer of 1024 bytes\n" );
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )
         printf( "Incorrect type or size of buffer for stream2\n" );
      else
         printf( "'stream2' now has no buffer\n" );
      _fcloseall();
   }
}
```

```Output
'stream1' now has a buffer of 1024 bytes
'stream2' now has no buffer
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
