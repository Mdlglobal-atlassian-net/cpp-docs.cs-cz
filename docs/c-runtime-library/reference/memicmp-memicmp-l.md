---
title: _memicmp, _memicmp_l
ms.date: 4/2/2020
api_name:
- _memicmp_l
- _memicmp
- _o__memicmp
- _o__memicmp_l
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 5ad22f2107695b14d4a8361d4532d6e250b5af6f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333226"
---
# <a name="_memicmp-_memicmp_l"></a>_memicmp, _memicmp_l

Porovná znaky ve dvou vyrovnávacích pamětnicích (bez malých a velkých písmen).

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

*vyrovnávací paměť1*<br/>
První vyrovnávací paměť.

*vyrovnávací paměť2*<br/>
Druhá vyrovnávací paměť.

*Počet*<br/>
Počet znaků.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota označuje vztah mezi vyrovnávacími pamětmi.

|Návratová hodnota|Vztah prvního počtu bajtů buf1 a buf2|
|------------------|--------------------------------------------------------|
|< 0|*buffer1* menší než *buffer2*.|
|0|*vyrovnávací paměť1* shodná s *vyrovnávací pamětí2*.|
|> 0|*buffer1* větší než *buffer2*.|
|**_NLSCMPERROR**|Došlo k chybě.|

## <a name="remarks"></a>Poznámky

Funkce **_memicmp** porovná znaky prvního *počtu* dvou vyrovnávacích pamětí *buffer1* a *buffer2* bajt byte. Porovnání není malá a velká písmena.

Pokud *je buď buffer1* nebo *buffer2* ukazatel null, tato funkce vyvolá neplatný obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí **_NLSCMPERROR** a nastaví **errno** na **EINVAL**.

**_memicmp** používá aktuální národní prostředí pro chování závislé na národním prostředí; **_memicmp_l** je totožný s tím rozdílem, že místo toho používá národní prostředí předané. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_memicmp**|\<memory.h> \<nebo string.h>|
|**_memicmp_l**|\<memory.h> \<nebo string.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Manipulace s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
