---
title: qsort
ms.date: 4/2/2020
api_name:
- qsort
- _o_qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- qsort
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: 09de57e206eb6fd4a75a0a9444332136aeee0e9d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338251"
---
# <a name="qsort"></a>qsort

Provádí rychlé řazení. K dispozici je bezpečnější verze této funkce. viz [qsort_s](qsort-s.md).

## <a name="syntax"></a>Syntaxe

```C
void qsort(
   void *base,
   size_t number,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>Parametry

*base*<br/>
Začátek cílového pole.

*Číslo*<br/>
Velikost pole v prvcích.

*Šířka*<br/>
Velikost prvku v bajtů.

*Porovnat*<br/>
Ukazatel na rutinu dodanou uživatelem, která porovnává dva prvky pole a vrací hodnotu, která určuje jejich vztah.

## <a name="remarks"></a>Poznámky

Funkce **qsort** implementuje algoritmus rychlého řazení pro řazení pole *číselných* prvků, každý z *šířky* bajtů. *Základ* argumentu je ukazatel na základnu pole, které má být seřazeno. **qsort** přepíše toto pole pomocí seřazených prvků.

**qsort** volá *rutinu porovnání* jednou nebo vícekrát během řazení a předá ukazatele na dva prvky pole při každém volání.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

Rutina porovná prvky a vrátí jednu z následujících hodnot.

|Porovnat vrácenou hodnotu funkce|Popis|
|-----------------------------------|-----------------|
|< 0|**elem1** méně než **elem2**|
|0|**elem1** ekvivalent **elem2**|
|> 0|**elem1** větší než **elem2**|

Pole je seřazeno v rostoucím pořadí, jak je definováno funkcí porovnání. Chcete-li seřadit pole v sestupném pořadí, obraťte pocit "větší než" a "menší než" ve funkci porovnání.

Tato funkce ověřuje její parametry. Pokud *porovnání* nebo *číslo* je **NULL**, nebo pokud *base* je **NULL** a *číslo* je nenulová, nebo pokud *šířka* je menší než nula, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí a **errno** je nastavena na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**qsort**|\<stdlib.h> \<a search.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_qsort.c
// arguments: every good boy deserves favor

/* This program reads the command-line
* parameters and uses qsort to sort them. It
* then displays the sorted arguments.
*/

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main( int argc, char **argv )
{
   int i;
   /* Eliminate argv[0] from sort: */
   argv++;
   argc--;

   /* Sort remaining args using Quicksort algorithm: */
   qsort( (void *)argv, (size_t)argc, sizeof( char * ), compare );

   /* Output sorted list: */
   for( i = 0; i < argc; ++i )
      printf( " %s", argv[i] );
   printf( "\n" );
}

int compare( const void *arg1, const void *arg2 )
{
   /* Compare all of both strings: */
   return _stricmp( * ( char** ) arg1, * ( char** ) arg2 );
}
```

```Output
boy deserves every favor good
```

## <a name="see-also"></a>Viz také

[Vyhledávání a řazení](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
