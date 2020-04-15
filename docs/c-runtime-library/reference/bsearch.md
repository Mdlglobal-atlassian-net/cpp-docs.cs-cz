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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: efad391eb2512cfa59cc3597430a84727676f27e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333803"
---
# <a name="bsearch"></a>bsearch

Provede binární hledání seřazené pole. K dispozici je bezpečnější verze této funkce. viz [bsearch_s](bsearch-s.md).

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

*Klíč*\
Ukazatel na klíč, který chcete vyhledat.

*Základní*\
Ukazatel na základnu vyhledávacích dat.

*Číslo*\
Počet prvků.

*Šířka*\
Šířka prvků.

*Porovnat*\
Funkce zpětného volání, která porovnává dva prvky. První je ukazatel na klíč pro hledání a druhý je ukazatel na prvek pole, který má být porovnán s klíčem.

## <a name="return-value"></a>Návratová hodnota

**bsearch** vrátí ukazatel na výskyt *klíče* v poli, na které odkazuje *základna*. Pokud *klíč* nebyl nalezen, funkce vrátí **hodnotu NULL**. Pokud pole není ve vzestupném pořadí řazení nebo obsahuje duplicitní záznamy s identickými klíči, výsledek je nepředvídatelný.

## <a name="remarks"></a>Poznámky

Funkce **bsearch** provádí binární vyhledávání seřazeného pole *číselných* prvků, každý *šířka* bajtů ve velikosti. *Základní* hodnota je ukazatel na základnu pole, které má být prohledáno, a *klíč* je požadovaná hodnota. Parametr *porovnání* je ukazatel na rutinu dodanou uživatelem, která porovnává požadovaný klíč s elementem pole. Vrátí jednu z následujících hodnot, které určují jejich vztah:

|Hodnota vrácená *pomocí rutiny porovnání*|Popis|
|-----------------------------------------|-----------------|
|\<0|Klíč je menší než prvek pole.|
|0|Klíč se rovná prvku pole.|
|> 0|Klíč je větší než prvek pole.|

Tato funkce ověřuje její parametry. Pokud *je porovnání*, *klíč* nebo *číslo* **null**nebo pokud je *základna* **NULL** a *číslo* je nenulová nebo pokud je *šířka* nula, funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, je `EINVAL` hodnota **errno** nastavena na hodnotu a funkce vrátí **hodnotu NULL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> \<a search.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program seřadí řetězec pole s qsort, a pak používá bsearch najít slovo "kočka".

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

[Vyhledávání a řazení](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
