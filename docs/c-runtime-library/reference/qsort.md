---
title: qsort
ms.date: 11/04/2016
apiname:
- qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- qsort
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: 8a770965a03e43227b99f122924c723691f79c61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358096"
---
# <a name="qsort"></a>qsort

Provádí rychlé řazení. Bezpečnější verze této funkce je k dispozici. Zobrazit [qsort_s –](qsort-s.md).

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
Spuštění cílového pole.

*Číslo*<br/>
Velikost pole prvků.

*Šířka*<br/>
Element velikost v bajtech.

*compare*<br/>
Ukazatel na uživatelem zadané rutinou, která porovná dva prvky pole a vrátí hodnotu, která určuje jejich vzájemný vztah.

## <a name="remarks"></a>Poznámky

**Qsort –** implementuje algoritmus rychlého řazení řazení pole funkce *číslo* prvky, každý z *šířka* bajtů. Argument *základní* je ukazatel na základní pole, který se má seřadit. **qsort –** přepíše toto pole pomocí seřazených elementy.

**qsort –** volání *porovnání* rutinní jeden nebo více krát během řazení a předá dva prvky pole ukazatelů na každé volání.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

Rutina porovná prvky a vrátí jednu z následujících hodnot.

|Porovnání návratovou hodnotu funkce|Popis|
|-----------------------------------|-----------------|
|< 0|**elem1** menší než **elem2**|
|0|**elem1** ekvivalentní **elem2**|
|> 0|**elem1** větší než **elem2**|

Pole je seřazený ve vzestupném pořadí, jak je definováno ve funkci porovnání. Chcete-li seřadit pole v sestupném pořadí, zaměňte význam "větší než" a "menší než" ve funkci porovnání.

Tato funkce ověřuje své parametry. Pokud *porovnání* nebo *číslo* je **NULL**, nebo pokud *základní* je **NULL** a *číslo* je nenulová nebo pokud *šířka* je menší než nula, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí a **errno** je nastavena na **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**qsort**|\<stdlib.h > a \<search.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
