---
title: _lfind
ms.date: 11/04/2016
api_name:
- _lfind
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lfind
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 8fd2141caf8311844a90a6d12226bb7797ac4734
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953389"
---
# <a name="_lfind"></a>_lfind

Provede lineární hledání zadaného klíče. K dispozici je bezpečnější verze této funkce; viz [_lfind_s](lfind-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *_lfind(
   const void *key,
   const void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základ dat hledání.

*Automatické*<br/>
Počet prvků pole.

*Šířka*<br/>
Šířka prvků pole.

*compare*<br/>
Ukazatel na srovnávací rutinu. První parametr je ukazatel na klíč pro hledání. Druhý parametr je ukazatel na prvek pole, který má být porovnán s klíčem.

## <a name="return-value"></a>Návratová hodnota

Pokud je klíč nalezen, vrátí **_lfind** ukazatel na element pole na *bázi Base* , který odpovídá *klíči*. Pokud klíč není nalezen, vrátí **_Lfind** **hodnotu null**.

## <a name="remarks"></a>Poznámky

Funkce **_lfind** provede lineární hledání *klíč* hodnoty v poli *číselných* prvků, přičemž každý z nich má *šířku* . Na rozdíl od **bSearch**, **_lfind** nevyžaduje řazení pole. *Základní* argument je ukazatel na základ pole, které má být prohledáno. Argument *Compare* je ukazatel na uživatelsky zadanou rutinu, která porovnává dva prvky pole a vrátí hodnotu určující jejich relaci. **_lfind** volá rutinu *porovnání* jednou nebo vícekrát během hledání a předá ukazatelům dva prvky pole při každém volání. Rutina *porovnání* musí porovnat prvky a vracet nenulové hodnoty (což znamená, že prvky jsou rozdílné) nebo 0 (což znamená, že prvky jsou identické).

Tato funkce ověří své parametry. Pokud je hodnota *Compare*, *klíč* nebo *číslo* **null**nebo pokud je hodnota *Base* **null** a *číslo* je nenulové, nebo pokud je *Šířka* menší než nula, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [parametru. Ověřování](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **hodnotu null**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lfind**|\<search.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_lfind.c
// This program uses _lfind to search a string array
// for an occurrence of "hello".

#include <search.h>
#include <string.h>
#include <stdio.h>

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}

int main( )
{
   char *arr[] = {"Hi", "Hello", "Bye"};
   int n = sizeof(arr) / sizeof(char*);
   char **result;
   char *key = "hello";

   result = (char **)_lfind( &key, arr,
                      &n, sizeof(char *), compare );

   if( result )
      printf( "%s found\n", *result );
   else
      printf( "hello not found!\n" );
}
```

```Output
Hello found
```

## <a name="see-also"></a>Viz také:

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
