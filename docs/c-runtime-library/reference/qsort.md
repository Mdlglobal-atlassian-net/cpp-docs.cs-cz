---
title: qsort – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- qsort
dev_langs:
- C++
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d6aea0d0857d26237716464ea4eda778d1e0f85
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="qsort"></a>qsort

Provede rychlé řazení. Bezpečnější verze této funkce je k dispozici. v tématu [qsort_s –](qsort-s.md).

## <a name="syntax"></a>Syntaxe

```C
void qsort(
   void *base,
   size_t num,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>Parametry

*základní* začátek cílového pole.

*číslo* pole velikost v elementy.

*Šířka* Element velikost v bajtech.

*porovnání* ukazatel na rutiny zadanou uživatelem, který porovnává dva elementy pole a vrátí hodnotu, která určuje jejich vztahu.

## <a name="remarks"></a>Poznámky

**Qsort –** funkce implementuje algoritmus rychlého řazení seřadit pole *číslo* elementy, každý z *šířka* bajtů. Argument *základní* je ukazatel na základní pole, která se má seřadit. **qsort –** přepíše toto pole pomocí seřazené elementy.

**qsort –** volání *porovnat* rutiny jeden nebo více krát při řazení a předá ukazatele dva elementy pole při každém volání.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

Rutiny porovná elementy a vrátí jednu z následujících hodnot.

|Porovnání návratovou hodnotu funkce|Popis|
|-----------------------------------|-----------------|
|< 0|**elem1** menší než **elem2**|
|0|**elem1** ekvivalentní **elem2**|
|> 0|**elem1** větší než **elem2**|

Pole je seřadit ve vzestupném pořadí, podle definice funkce porovnání. Do pole v sestupném pořadí řazení, reverse smysl "větší než" a "menší než" ve funkci porovnání.

Tato funkce ověří jeho parametry. Pokud *porovnat* nebo *číslo* je **NULL**, nebo pokud *základní* je **NULL** a **číslo* je nenulové hodnoty, nebo pokud *šířka* je menší než nula, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu a **errno** je nastaven na **einval –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**qsort**|\<stdlib.h > a \<search.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
