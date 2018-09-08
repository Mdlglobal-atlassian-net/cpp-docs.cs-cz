---
title: setbuf – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- setbuf
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
- setbuf
dev_langs:
- C++
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea1c979b261b81f80d95e4219f948dd2a3f5849e
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100350"
---
# <a name="setbuf"></a>setbuf

Ovládací prvky datového proudu do vyrovnávací paměti. Tato funkce je zastaralá; použít [setvbuf –](setvbuf.md) místo.

## <a name="syntax"></a>Syntaxe

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Ukazatel na **souboru** struktury.

*Vyrovnávací paměti*<br/>
Uživatel přidělené vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

**Setbuf –** ovládacích prvků do vyrovnávací paměti pro funkci *stream*. *Stream* argument musí odkazovat na otevřený soubor, který nebyl číst nebo zapisovat. Pokud *vyrovnávací paměti* argument je **NULL**, je ve špatném vyrovnávací paměti datového proudu. Pokud ne, vyrovnávací paměti musí odkazovat na pole znaků o délce **BUFSIZ**, kde **BUFSIZ** je velikost vyrovnávací paměti, jak jsou definovány v STDIO. H. Uživatel zadal vyrovnávací paměť, místo výchozí systému přidělené vyrovnávací paměti pro daný datový proud, se používá pro vstupně-výstupní operace ukládání do vyrovnávací paměti. **Stderr** zrušení ve vyrovnávací paměti ve výchozím nastavení je ale můžete použít **setbuf –** přiřadit vyrovnávací paměti do **stderr**.

**setbuf –** nahradila ji [setvbuf –](setvbuf.md), což je upřednostňovaný rutiny pro nový kód. **setbuf –** je zachován z důvodu kompatibility s existujícím kódem.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_setbuf.c
// compile with: /W3
// This program first opens files named DATA1 and
// DATA2. Then it uses setbuf to give DATA1 a user-assigned
// buffer and to change DATA2 so that it has no buffer.

#include <stdio.h>

int main( void )
{
   char buf[BUFSIZ];
   FILE *stream1, *stream2;

   fopen_s( &stream1, "data1", "a" );
   fopen_s( &stream2, "data2", "w" );

   if( (stream1 != NULL) && (stream2 != NULL) )
   {
      // "stream1" uses user-assigned buffer:
      setbuf( stream1, buf ); // C4996
      // Note: setbuf is deprecated; consider using setvbuf instead
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );

      // "stream2" is unbuffered
      setbuf( stream2, NULL ); // C4996
      printf( "stream2 buffering disabled\n" );
      _fcloseall();
   }
}
```

```Output
stream1 set to user-defined buffer at: 0012FCDC
stream2 buffering disabled
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
