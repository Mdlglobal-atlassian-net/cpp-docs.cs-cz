---
title: _lsearch
ms.date: 11/04/2016
api_name:
- _lsearch
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
- _lsearch
- lsearch
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: 92973536df478f4176970929c5f4dd48352bed13
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954078"
---
# <a name="_lsearch"></a>_lsearch

Provede lineární hledání hodnoty. Pokud se nenajde, přidá se na konec seznamu. K dispozici je bezpečnější verze této funkce; viz [_lsearch_s](lsearch-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *_lsearch(
   const void *key,
   void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základ pole, které má být prohledáno.

*Automatické*<br/>
Počet elementů.

*Šířka*<br/>
Šířka každého elementu pole.

*compare*<br/>
Ukazatel na srovnávací rutinu. První parametr je ukazatel na klíč pro hledání. Druhý parametr je ukazatel na prvek pole, který má být porovnán s klíčem.

## <a name="return-value"></a>Návratová hodnota

Pokud je klíč nalezen, vrátí **_lsearch** ukazatel na element pole na *bázi Base* , který odpovídá *klíči*. Pokud klíč není nalezen, vrátí **_lsearch** ukazatel na nově přidanou položku na konci pole.

## <a name="remarks"></a>Poznámky

Funkce **_lsearch** provede lineární hledání *klíč* hodnoty v poli *číselných* prvků, přičemž každý z nich má *šířku* . Na rozdíl od **bSearch**, **_lsearch** nevyžaduje řazení pole. Pokud *klíč* není nalezen, **_lsearch** ho přidá na konec pole a zvýší *číslo*.

Argument *Compare* je ukazatel na uživatelsky zadanou rutinu, která porovná dva prvky pole a vrátí hodnotu určující jejich relaci. **_lsearch** volá rutinu *porovnání* jednou nebo vícekrát během hledání a předá ukazatelům dva prvky pole při každém volání. *porovnání* musí porovnat prvky a vracet buď nenulovou hodnotu (což znamená, že prvky jsou rozdílné) nebo 0 (což znamená, že prvky jsou identicky).

Tato funkce ověří své parametry. Pokud je hodnota *Compare*, *klíč* nebo *číslo* **null**nebo pokud je hodnota *Base* **null** a *číslo* je nenulové, nebo pokud je *Šířka* menší než nula, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [parametru. Ověřování](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **hodnotu null**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_lsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main(void)
{
   char * wordlist[4] = { "hello", "thanks", "bye" };
                            // leave room to grow...
   int n = 3;
   char **result;
   char *key = "extra";
   int i;

   printf( "wordlist before _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );

   result = (char **)_lsearch( &key, wordlist,
                      &n, sizeof(char *), compare );

   printf( "wordlist after _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );
}

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}
```

```Output
wordlist before _lsearch: hello thanks bye
wordlist after _lsearch: hello thanks bye extra
```

## <a name="see-also"></a>Viz také:

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
