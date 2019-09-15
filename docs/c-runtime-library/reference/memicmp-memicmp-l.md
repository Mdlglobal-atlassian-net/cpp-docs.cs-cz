---
title: _memicmp, _memicmp_l
ms.date: 11/04/2016
api_name:
- _memicmp_l
- _memicmp
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _memicmp
- memicmp_l
- _memicmp_l
helpviewer_keywords:
- memicmp function
- _memicmp function
- memicmp_l function
- _memicmp_l function
ms.assetid: 0a6eb945-4077-4f84-935d-1aaebe8db8cb
ms.openlocfilehash: a463b9c79a76879311bb811b38e4aabcfd6e7226
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951840"
---
# <a name="_memicmp-_memicmp_l"></a>_memicmp, _memicmp_l

Porovná znaky ve dvou bufferech (bez rozlišení velkých a malých písmen).

## <a name="syntax"></a>Syntaxe

```C
int _memicmp(
   const void *buffer1,
   const void *buffer2,
   size_t count
);
int _memicmp_l(
   const void *buffer1,
   const void *buffer2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*buffer1*<br/>
První vyrovnávací paměť.

*buffer2*<br/>
Druhá vyrovnávací paměť.

*výpočtu*<br/>
Počet znaků.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota označuje vztah mezi vyrovnávacími pamětmi.

|Návratová hodnota|Relace prvních počtů bajtů buf1 a buf2|
|------------------|--------------------------------------------------------|
|< 0|*buffer1* menší než *buffer2*.|
|0|*buffer1* se shodují s *buffer2*.|
|> 0|*buffer1* větší než *buffer2*.|
|**_NLSCMPERROR**|Došlo k chybě.|

## <a name="remarks"></a>Poznámky

Funkce **_memicmp** porovná první *počet* znaků dvou vyrovnávacích pamětí *buffer1* a *buffer2* bajt po bajtu. Porovnávání nerozlišuje velká a malá písmena.

Pokud je *buffer1* nebo *buffer2* ukazatel s hodnotou null, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí **_NLSCMPERROR** a nastaví **errno** na **EINVAL**.

**_memicmp** používá aktuální národní prostředí pro chování závislé na národním prostředí; **_memicmp_l** je totožný s tím rozdílem, že místo toho používá národní prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_memicmp**|\<Memory. h > nebo \<String. h >|
|**_memicmp_l**|\<Memory. h > nebo \<String. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_memicmp.c
// This program uses _memicmp to compare
// the first 29 letters of the strings named first and
// second without regard to the case of the letters.

#include <memory.h>
#include <stdio.h>
#include <string.h>

int main( void )
{
   int result;
   char first[] = "Those Who Will Not Learn from History";
   char second[] = "THOSE WHO WILL NOT LEARN FROM their mistakes";
   // Note that the 29th character is right here ^

   printf( "Compare '%.29s' to '%.29s'\n", first, second );
   result = _memicmp( first, second, 29 );
   if( result < 0 )
      printf( "First is less than second.\n" );
   else if( result == 0 )
      printf( "First is equal to second.\n" );
   else if( result > 0 )
      printf( "First is greater than second.\n" );
}
```

```Output
Compare 'Those Who Will Not Learn from' to 'THOSE WHO WILL NOT LEARN FROM'
First is equal to second.
```

## <a name="see-also"></a>Viz také:

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
