---
title: bsearch
ms.date: 4/2/2020
api_name:
- bsearch
- _o_bsearch
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 7843c1cd15a4bd39e1b24676402d635bd5f2de90
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913371"
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

*zkrat*\
Ukazatel na klíč, který chcete vyhledat.

*základ*\
Ukazatel na základ dat hledání.

*Automatické*\
Počet elementů.

*Délk*\
Šířka prvků

*porovnán*\
Funkce zpětného volání, která porovnává dva elementy. První je ukazatel na klíč pro hledání a druhý je ukazatel na prvek pole, který má být porovnán s klíčem.

## <a name="return-value"></a>Návratová hodnota

**bSearch** vrací ukazatel na výskyt *klíče* v poli, na které ukazuje *základ*. Pokud *klíč* není nalezen, funkce vrátí **hodnotu null**. Pokud pole není ve vzestupném pořadí řazení nebo obsahuje duplicitní záznamy se stejnými klíči, výsledek je nepředvídatelné.

## <a name="remarks"></a>Poznámky

Funkce **bSearch** provádí binární hledání seřazeného pole *číselného* prvku, přičemž každý z nich má velikost *v bajtech* . *Základní* hodnota je ukazatel na základ pole, které má být prohledáno, a *klíč* je hledaná hodnota. Parametr *Compare* je ukazatel na uživatelsky zadanou rutinu, která porovnává požadovaný klíč s elementem pole. Vrátí jednu z následujících hodnot, které určují jejich vztah:

|Hodnota vrácená rutinou *Compare*|Popis|
|-----------------------------------------|-----------------|
|\<0,8|Klíč je menší než prvek pole.|
|0|Klíč je roven elementu pole.|
|> 0|Klíč je větší než prvek pole.|

Tato funkce ověří své parametry. Pokud je **hodnota** *Compare*, *klíč* nebo *číslo* null nebo pokud je hodnota *Base* **null** a *číslo* je nenulové, nebo pokud je *Šířka* nula, funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na `EINVAL` a funkce vrátí **hodnotu null**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**bsearch**|\<Stdlib. h> a \<Search. h>|

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

## <a name="see-also"></a>Viz také

[Hledání a řazení](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
