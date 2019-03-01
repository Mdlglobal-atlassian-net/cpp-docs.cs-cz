---
title: bsearch
ms.date: 11/04/2016
apiname:
- bsearch
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: e170ce67d22c0d97825a7eb754546a29daac6d89
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210455"
---
# <a name="bsearch"></a>bsearch

Provádí binární vyhledávání seřazené pole. Bezpečnější verze této funkce je k dispozici. Zobrazit [bsearch_s –](bsearch-s.md).

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

*key*<br/>
Objekt pro hledání.

*base*<br/>
Ukazatele na základní dat hledání.

*Číslo*<br/>
Počet prvků.

*Šířka*<br/>
Šířka prvků.

*compare*<br/>
Funkce zpětného volání, která porovná dva elementy. První je ukazatel na klíč pro hledání a druhý je ukazatel na prvek pole, která se má porovnat s klíčem.

## <a name="return-value"></a>Návratová hodnota

**bsearch –** vrací ukazatel na výskyt *klíč* pole, na které odkazuje *základní*. Pokud *klíč* nenajde, vrátí funkce hodnotu **NULL**. Pokud pole není ve vzestupném pořadí řazení nebo obsahuje duplicitní záznamy s identickými klíči, je výsledkem nepředvídatelné.

## <a name="remarks"></a>Poznámky

**Bsearch –** funkce provádí binárního vyhledávání seřazené pole *číslo* prvky, každý z *šířka* bajty. *Základní* hodnota je ukazatel na základní pole pro hledání, a *klíč* je hodnota vyhledané. *Porovnání* parametrem je ukazatel do uživatelem zadané rutinu, která porovnává požadovaný klíč k elementu pole a vrátí jednu z následujících hodnot zadáním jejich vztahu:

|Hodnota vrácená *porovnání* rutina|Popis|
|-----------------------------------------|-----------------|
|\< 0|Klíč je menší než prvek pole.|
|0|Klíč je rovna prvek pole.|
|> 0|Klíč je větší než prvek pole.|

Tato funkce ověřuje své parametry. Pokud *porovnání*, *klíč* nebo *číslo* je **NULL**, nebo pokud *základní* je **NULL**a *číslo* je nenulová nebo pokud *šířka* je nula, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na `EINVAL` a funkce vrátí **NULL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**bsearch**|\<stdlib.h > a \<search.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program řadí pole řetězců s qsort – a pak používá bsearch – k vyhledání slov "cat".

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

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
