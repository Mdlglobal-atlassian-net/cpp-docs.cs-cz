---
title: setvbuf
ms.date: 11/04/2016
apiname:
- setvbuf
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
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: d4336c6cc478a035fcc0b9b059a7161d58bc4442
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328094"
---
# <a name="setvbuf"></a>setvbuf

Ovládací prvky datového proudu do vyrovnávací paměti a velikost vyrovnávací paměti.

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
Ukazatel na **souboru** struktury.

*Vyrovnávací paměti*<br/>
Uživatel přidělené vyrovnávací paměti.

*Režim*<br/>
Režim ukládání do vyrovnávací paměti.

*Velikost*<br/>
Velikost vyrovnávací paměti v bajtech. Povolený rozsah: 2 < = *velikost* < = INT_MAX (2147483647). Interně, hodnota zadaná pro *velikost* se zaokrouhlí směrem dolů na nejbližší násobek 2.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0.

Pokud *datového proudu* je **NULL**, nebo pokud *režimu* nebo *velikost* je mimo platný změnu, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce vrátí hodnotu -1 a nastaví **errno** k **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Setvbuf –** funkce umožňuje program, který řídí, jak ukládání do vyrovnávací paměti a velikost pro vyrovnávací paměti *stream*. *datový proud* musí odkazovat na otevřený soubor, který nebylo podrobeno vstupně-výstupní operace, protože byl otevřen. Pole odkazované *vyrovnávací paměti* slouží jako vyrovnávací paměť, pokud se nejedná **NULL**v takovém případě **setvbuf –** používá automaticky přidělené vyrovnávací paměti o délce  *velikost*/2 \* 2 bajty.

Musí být v režimu **_IOFBF**, **_IOLBF**, nebo **_IONBF**. Pokud *režimu* je **_IOFBF** nebo **_IOLBF**, pak *velikost* se používá jako velikost vyrovnávací paměti. Pokud *režimu* je **_IONBF**, je datový proud bez vyrovnávací paměti a *velikost* a *vyrovnávací paměti* jsou ignorovány. Hodnoty pro *režimu* a jejich význam:

|*režim* hodnota|Význam|
|-|-|
| **_IOFBF** | Úplné ukládání do vyrovnávací paměti; To znamená *vyrovnávací paměti* slouží jako vyrovnávací paměť a *velikost* se používá jako velikost vyrovnávací paměti. Pokud *vyrovnávací paměti* je **NULL**, automaticky přidělené vyrovnávací paměti *velikost* bajty se používá. |
| **_IOLBF** | U některých systémů získáte řádku ukládání do vyrovnávací paměti. Ale pro Win32, chování je stejné jako **_IOFBF** – úplné ukládání do vyrovnávací paměti. |
| **_IONBF** | Žádné vyrovnávací paměť je použit, bez ohledu na to *vyrovnávací paměti* nebo *velikost*. |

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
