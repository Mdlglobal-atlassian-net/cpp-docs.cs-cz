---
title: memchr, wmemchr
ms.date: 03/31/2019
api_name:
- wmemchr
- memchr
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- memchr
- wmemchr
helpviewer_keywords:
- memchr function
- wmemchr function
ms.assetid: 5a348581-28f1-4256-8434-687245f7fc9f
ms.openlocfilehash: c951716d623d900f975e9d6f8a1c762a155b1a7a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951948"
---
# <a name="memchr-wmemchr"></a>memchr, wmemchr

Hledání znaků ve vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```C
void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C only
void *memchr(
   void *buffer,
   int c,
   size_t count
); // C++ only
const void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C++ only
wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C only
wchar_t *wmemchr(
   wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
const wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Ukazatel na vyrovnávací paměť.

*c*<br/>
Znak, který chcete vyhledat.

*výpočtu*<br/>
Počet znaků, které mají být zkontrolovány.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí ukazatel na první umístění *c* ve *vyrovnávací paměti*. V opačném případě vrátí hodnotu NULL.

## <a name="remarks"></a>Poznámky

`memchr`a `wmemchr` vyhledejte první výskyt *c* v prvním *počtu* znaků *vyrovnávací paměti*. Zastaví se, když najde *c* nebo při zkontrolování prvního *počtu* znaků.

V jazyce C tyto funkce přebírají ukazatel **const** pro první argument. V C++jsou k dispozici dvě přetížení. Přetížení přebírající ukazatel na **konstantu** vrací ukazatel na **const**; verze, která přebírá ukazatel na jiný typ než**const** , vrací ukazatel na**nekonstantní**hodnotu. Je- \_li\_k\_dispozici verze **const** i non-**const** , je definováno správné\_přetížení makra v CRT. Pokud vyžadujete**nekonstantní** chování pro C++ přetížení C++v, definujte symbol \_const\_Return.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`memchr`|\<Memory. h > nebo \<String. h >|
|`wmemchr`|\<wchar.h>|

Další informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_memchr.c

#include <memory.h>
#include <stdio.h>

int  ch = 'r';
char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int result;
   printf( "String to be searched:\n             %s\n", string );
   printf( "             %s\n             %s\n\n", fmt1, fmt2 );

   printf( "Search char: %c\n", ch );
   pdest = memchr( string, ch, sizeof( string ) );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "Result:      %c found at position %d\n", ch, result );
   else
      printf( "Result:      %c not found\n" );
}
```

### <a name="output"></a>Výstup

```Output
String to be searched:
             The quick brown dog jumps over the lazy fox
                      1         2         3         4         5
             12345678901234567890123456789012345678901234567890

Search char: r
Result:      r found at position 12
```

## <a name="see-also"></a>Viz také:

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
