---
title: _lfind
ms.date: 4/2/2020
api_name:
- _lfind
- _o__lfind
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 4721ba96e145b3c2fde4ce0bb73157bbbcab4dff
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916458"
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

*zkrat*<br/>
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základ dat hledání.

*Automatické*<br/>
Počet prvků pole.

*Délk*<br/>
Šířka prvků pole.

*porovnán*<br/>
Ukazatel na srovnávací rutinu. První parametr je ukazatel na klíč pro hledání. Druhý parametr je ukazatel na prvek pole, který má být porovnán s klíčem.

## <a name="return-value"></a>Návratová hodnota

Pokud je klíč nalezen, **_lfind** vrátí ukazatel na prvek pole na *bázi Base* , který odpovídá *klíči*. Pokud klíč nebyl nalezen, **_lfind** vrátí **hodnotu null**.

## <a name="remarks"></a>Poznámky

Funkce **_lfind** provede lineární hledání *klíč* hodnoty v poli *číselných* prvků, přičemž každý z nich má *šířku* . Na rozdíl od **bSearch**nevyžaduje **_lfind** pole k řazení. *Základní* argument je ukazatel na základ pole, které má být prohledáno. Argument *Compare* je ukazatel na uživatelsky zadanou rutinu, která porovnává dva prvky pole a vrátí hodnotu určující jejich relaci. **_lfind** volá rutinu *porovnání* jednou nebo vícekrát během hledání a předá ukazatel na dva prvky pole při každém volání. Rutina *porovnání* musí porovnat prvky a vracet nenulové hodnoty (což znamená, že prvky jsou rozdílné) nebo 0 (což znamená, že prvky jsou identické).

Tato funkce ověří své parametry. Pokud je **hodnota** *Compare*, *klíč* nebo *číslo* null nebo pokud je hodnota *Base* **null** a *číslo* je nenulové, nebo pokud je *Šířka* menší než nula, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **hodnotu null**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lfind**|\<Hledat. h>|

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

## <a name="see-also"></a>Viz také

[Hledání a řazení](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
