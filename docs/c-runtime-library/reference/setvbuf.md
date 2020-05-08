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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 907d02e94c79acf09dfa99a8b42e9f448d32dcfa
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915757"
---
# <a name="setvbuf"></a>setvbuf

Ovládá ukládání do vyrovnávací paměti streamování a velikost vyrovnávací paměti.

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

*Stream*<br/>
Ukazatel na strukturu **souborů** .

*vyrovnávací paměti*<br/>
Vyrovnávací paměť přidělená uživatelem

*Mode*<br/>
Režim ukládání do vyrovnávací paměti.

*hodnota*<br/>
Velikost vyrovnávací paměti v bajtech Povolený rozsah: 2 <= *velikost* <= INT_MAX (2147483647). Interně se hodnota zadaná pro *Velikost* zaokrouhluje dolů na nejbližší násobek 2.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0.

Pokud má *datový proud* **hodnotu null**nebo pokud *režim* nebo *Velikost* nejsou v rámci platné změny, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tato funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **setvbuf –** umožňuje programu řídit ukládání do vyrovnávací paměti a velikost vyrovnávací paměti pro *datový proud*. *datový proud* musí odkazovat na otevřený soubor, který po otevření neprošl operací I/O. Pole, na které se odkazuje pomocí *vyrovnávací paměti* , se používá jako vyrovnávací paměť, pokud není **null**. v takovém případě **setvbuf –** používá automaticky přidělenou vyrovnávací paměť s \* délkou *velikosti*/2 2 bajty.

Režim musí být **_IOFBF**, **_IOLBF**nebo **_IONBF**. Pokud *mode* je režim **_IOFBF** nebo **_IOLBF**, použije *se jako* velikost vyrovnávací paměti. Pokud *mode* je režim **_IONBF**, datový proud je neuložený do vyrovnávací paměti a *Velikost* a *vyrovnávací paměť* se ignorují. Hodnoty pro *režim* a jejich význam jsou:

|hodnota *režimu*|Význam|
|-|-|
| **_IOFBF** | Úplné ukládání do vyrovnávací paměti; To znamená, že *vyrovnávací paměť* se používá jako vyrovnávací paměť a *Velikost* se používá jako velikost vyrovnávací paměti. Pokud má *vyrovnávací paměť* **hodnotu null**, použije se automaticky přidělená *Velikost* vyrovnávací paměti. |
| **_IOLBF** | U některých systémů to poskytuje ukládání řádků do vyrovnávací paměti. Pro Win32 ale chování je stejné jako **_IOFBF** -Full Buffered. |
| **_IONBF** | Nepoužívá se žádná vyrovnávací paměť bez ohledu na velikost *vyrovnávací paměti* nebo *velikosti*. |

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setvbuf**|\<stdio. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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
