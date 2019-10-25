---
title: bsearch
ms.date: 10/22/2019
api_name:
- bsearch
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: 6b476cbdd5e9c072cae03ad1091a96e2d0b7422b
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811099"
---
# <a name="bsearch"></a>bsearch

Provede binární hledání seřazeného pole. K dispozici je bezpečnější verze této funkce; viz [bsearch_s](bsearch-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *bsearch(
   const void *key,
   const void *base,
   size_t num,
   size_t width,
   int ( __cdecl *compare ) (const void *key, const void *datum)
);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Ukazatel na klíč, který chcete vyhledat.

*základní*\
Ukazatel na základ dat hledání.

\ *číslo*
Počet elementů.

\ *šířky*
Šířka prvků

*porovnat*\
Funkce zpětného volání, která porovnává dva elementy. První je ukazatel na klíč pro hledání a druhý je ukazatel na prvek pole, který má být porovnán s klíčem.

## <a name="return-value"></a>Návratová hodnota

**bSearch** vrací ukazatel na výskyt *klíče* v poli, na které ukazuje *základ*. Pokud *klíč* není nalezen, funkce vrátí **hodnotu null**. Pokud pole není ve vzestupném pořadí řazení nebo obsahuje duplicitní záznamy se stejnými klíči, výsledek je nepředvídatelné.

## <a name="remarks"></a>Poznámky

Funkce **bSearch** provádí binární hledání seřazeného pole *číselného* prvku, přičemž každý z nich má velikost *v bajtech* . *Základní* hodnota je ukazatel na základ pole, které má být prohledáno, a *klíč* je hledaná hodnota. Parametr *Compare* je ukazatel na uživatelsky zadanou rutinu, která porovnává požadovaný klíč s elementem pole. Vrátí jednu z následujících hodnot, které určují jejich vztah:

|Hodnota vrácená rutinou *Compare*|Popis|
|-----------------------------------------|-----------------|
|\< 0|Klíč je menší než prvek pole.|
|0,8|Klíč je roven elementu pole.|
|> 0|Klíč je větší než prvek pole.|

Tato funkce ověří své parametry. Pokud je hodnota *Compare*, *klíč* nebo *číslo* **null**nebo pokud je hodnota *Base* **null** a *číslo* je nenulové, nebo pokud je *Šířka* nula, funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [parametru. Ověřování](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaveno na `EINVAL` a funkce vrátí **hodnotu null**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**bsearch**|\<Stdlib. h > a \<Search. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program seřadí pole řetězců pomocí qsort a pak pomocí bSearch hledá slovo "Cat".

```C
// crt_bsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( char **arg1, char **arg2 )
{
   /* Compare all of both strings: */
   return _strcmpi( *arg1, *arg2 );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};
   char **result;
   char *key = "cat";
   int i;

   /* Sort using Quicksort algorithm: */
   qsort( (void *)arr, sizeof(arr)/sizeof(arr[0]), sizeof( char * ), (int (*)(const
   void*, const void*))compare );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch( (char *) &key, (char *)arr, sizeof(arr)/sizeof(arr[0]),
                              sizeof( char * ), (int (*)(const void*, const void*))compare );
   if( result )
      printf( "\n%s found at %Fp\n", *result, result );
   else
      printf( "\nCat not found!\n" );
}
```

```Output
cat cow dog goat horse human pig rat
cat found at 002F0F04
```

## <a name="see-also"></a>Viz také:

[Hledání a řazení](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
