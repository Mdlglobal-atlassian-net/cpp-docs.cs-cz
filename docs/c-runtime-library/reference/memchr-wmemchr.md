---
title: memchr, wmemchr
ms.date: 03/31/2019
apiname:
- wmemchr
- memchr
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- memchr
- wmemchr
helpviewer_keywords:
- memchr function
- wmemchr function
ms.assetid: 5a348581-28f1-4256-8434-687245f7fc9f
ms.openlocfilehash: 00a1f0d12047cc388b56074a657ffd739e986827
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285258"
---
# <a name="memchr-wmemchr"></a>memchr, wmemchr

Vyhledání znaků ve vyrovnávací paměti.

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

*Vyrovnávací paměti*<br/>
Ukazatel do vyrovnávací paměti.

*c*<br/>
Znak k vyhledání.

*Počet*<br/>
Počet znaků ke kontrole.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ukazatel na první umístění *c* v *vyrovnávací paměti*. V opačném případě vrátí hodnotu NULL.

## <a name="remarks"></a>Poznámky

`memchr` a `wmemchr` vyhledá první výskyt *c* v prvním *počet* znaků *vyrovnávací paměti*. Zastaví najde *c* nebo kdy se má ohlásilo první *počet* znaků.

V jazyce C, tyto funkce přijímají **const** ukazatele pro první argument. V jazyce C++ jsou k dispozici dvě přetížení. Přetížení přijímající ukazatel na **const** vrací ukazatel na **const**; verze, která přijímá ukazatel na jinou hodnotu než**const** vrací ukazatel na jinou hodnotu než**const** . Makro \_CRT\_CONST\_OPRAVTE\_PŘETÍŽENÍ je definováno, pokud **const** a jiných-**const** verze těchto funkcí jsou k dispozici. Pokud budete potřebovat non -**const** chování pro obě přetížení C++ v jazyce C++, definujte symbol \_CONST\_vrátit.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`memchr`|\<Memory.h > nebo \<string.h >|
|`wmemchr`|\<wchar.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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
