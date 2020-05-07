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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 40f23db88abf9733eada9e775aacda83cba5829a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910334"
---
# <a name="setbuf"></a>setbuf

Řídí ukládání datových proudů do vyrovnávací paměti. Tato funkce je zastaralá. místo toho použijte [setvbuf –](setvbuf.md) .

## <a name="syntax"></a>Syntaxe

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Ukazatel na strukturu **souborů** .

*vyrovnávací paměti*<br/>
Vyrovnávací paměť přidělená uživatelem

## <a name="remarks"></a>Poznámky

Funkce **setbuf** řídí ukládání do vyrovnávací paměti pro *Stream*. Argument *Stream* musí odkazovat na otevřený soubor, který se nečetl nebo nezapsal. Pokud má argument *buffer* **hodnotu null**, datový proud je neuložený do vyrovnávací paměti. V takovém případě musí vyrovnávací paměť ukazovat na pole znaků s délkou **BUFSIZ**, kde **BUFSIZ** je velikost vyrovnávací paměti, jak je definováno v stdio. Y. Pro vstupně-výstupní ukládání do vyrovnávací paměti se používá uživatelem zadaná vyrovnávací paměť namísto výchozí systémem přidělené vyrovnávací paměti pro daný datový proud. Datový proud **stderr** ve výchozím nastavení není uložen do vyrovnávací paměti, ale můžete použít **setbuf** k přiřazení vyrovnávacích pamětí do **stderr**.

**setbuf** byl nahrazen [setvbuf –](setvbuf.md), což je upřednostňovaná rutina pro nový kód. Na rozdíl od **setvbuf –** nemá **setbuf** žádný způsob, jak hlásit chyby. **setvbuf –** také umožňuje řídit režim ukládání do vyrovnávací paměti i velikost vyrovnávací paměti. **setbuf** existuje pro kompatibilitu s existujícím kódem.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setbuf**|\<stdio. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
