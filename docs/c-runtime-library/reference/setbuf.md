---
title: setbuf
ms.date: 4/2/2020
api_name:
- setbuf
- _o_setbuf
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
- setbuf
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
ms.openlocfilehash: f96cffb8770cda78ebff8d873b441ddc288bc41f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332080"
---
# <a name="setbuf"></a>setbuf

Řídí ukládání do vyrovnávací paměti datového proudu. Tato funkce je zastaralá; místo toho použijte [setvbuf.](setvbuf.md)

## <a name="syntax"></a>Syntaxe

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>Parametry

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

*Vyrovnávací paměti*<br/>
Uživatelem přidělená vyrovnávací paměť.

## <a name="remarks"></a>Poznámky

Funkce **setbuf** řídí ukládání do vyrovnávací paměti pro *datový proud*. Argument *datového proudu* musí odkazovat na otevřený soubor, který nebyl přečten nebo zapsán. Pokud je argument *vyrovnávací paměti* **NULL**, datový proud není ve vyrovnávací paměti. Pokud tomu tak není, vyrovnávací paměť musí ukazovat na pole znaků délky **BUFSIZ**, kde **BUFSIZ** je velikost vyrovnávací paměti, jak je definována v STDIO. H. Uživatelem zadaná vyrovnávací paměť namísto výchozí vyrovnávací paměti přidělené systémem pro daný datový proud se používá pro ukládání do vyrovnávací paměti vstupně-v. **Stderr** stream je ve výchozím nastavení bez vyrovnávací paměti, ale můžete použít **setbuf** přiřadit vyrovnávací paměti **stderr**.

**setbuf** byl nahrazen [setvbuf](setvbuf.md), což je upřednostňovaná rutina pro nový kód. Na rozdíl od **setvbuf**, **setbuf** nemá žádný způsob, jak hlášení chyb. **setvbuf** také umožňuje řídit režim ukládání do vyrovnávací paměti i velikost vyrovnávací paměti. **setbuf** existuje pro kompatibilitu s existujícím kódem.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
