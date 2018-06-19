---
title: memchr, wmemchr – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- memchr
- wmemchr
dev_langs:
- C++
helpviewer_keywords:
- memchr function
- wmemchr function
ms.assetid: 5a348581-28f1-4256-8434-687245f7fc9f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c2ba300275f0154e84f7d2ced21b0893bbe3d85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401682"
---
# <a name="memchr-wmemchr"></a>memchr, wmemchr

Najít znaků do vyrovnávací paměti.

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
Znak, který má hledat.

*Počet*<br/>
Počet znaků ke kontrole.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí ukazatel na první umístění *c* v *vyrovnávací paměti*. V opačném případě vrátí **NULL**.

## <a name="remarks"></a>Poznámky

**memchr** a **wmemchr –** vyhledejte první výskyt *c* v prvním *počet* bajtů *vyrovnávací paměti*. Zastaví, pokud najde *c* nebo když byl zkontrolován první *počet* bajtů.

V jazyce C, proveďte tyto funkce ** const ** pro první argument ukazatel. V jazyce C++ jsou k dispozici dva přetížení. Přetížení trvá ukazatel na ** const ** vrací ukazatel na **const **; na verzi, která přebírá ukazatel na jinou hodnotu než**const ** vrací ukazatel na jinou hodnotu než**const **. Makro _CRT_CONST_CORRECT_OVERLOADS je definována, pokud obě **const ** a jiných-** const ** verze tyto funkce jsou k dispozici. Pokud budete potřebovat jinou hodnotu než**const ** chování pro obě overloadsin C++, C++, definovat symbol _CONST_RETURN.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**memchr**|\<Memory.h > nebo \<string.h >|
|**wmemchr**|\<wchar.h>|

Další informace o kompatibilitě najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
