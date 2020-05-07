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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3d9c3481b37e94dbb59ee7356caafc53501045ea
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913261"
---
# <a name="qsort"></a>qsort

Provede rychlé řazení. K dispozici je bezpečnější verze této funkce; viz [qsort_s](qsort-s.md).

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
Začátek cílového pole

*Automatické*<br/>
Velikost pole v elementech

*Délk*<br/>
Velikost elementu v bajtech

*porovnán*<br/>
Ukazatel na uživatelsky zadanou rutinu, která porovná dva prvky pole a vrátí hodnotu, která určuje jejich relaci.

## <a name="remarks"></a>Poznámky

Funkce **qsort** implementuje algoritmus rychlého řazení pro řazení pole *číselných* prvků, z každé *šířky* bajtů. *Základem* argumentu je ukazatel na základ pole, které má být seřazeno. **qsort** přepisuje toto pole pomocí seřazených prvků.

**qsort** volá rutinu *porovnání* jednou nebo vícekrát během řazení a předá ukazatelům dva prvky pole při každém volání.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

Rutina porovná prvky a vrátí jednu z následujících hodnot.

|Porovnat návratovou hodnotu funkce|Popis|
|-----------------------------------|-----------------|
|< 0|**elem1** menší než **elem2**|
|0|**elem1** ekvivalent **elem2**|
|> 0|**elem1** větší než **elem2**|

Pole je seřazené ve vzestupném pořadí, jak je definováno funkcí porovnání. Chcete-li seřadit pole v klesajícím pořadí, obraťte se na výraz "větší než" a "menší než" v rámci funkce porovnání.

Tato funkce ověří své parametry. Pokud je **hodnota** *Compare* nebo *Number* null nebo pokud je hodnota *Base* **null** a *číslo* je nenulové, nebo pokud je *Šířka* menší než nula, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí a **errno** se nastaví na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**qsort**|\<Stdlib. h> a \<Search. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Hledání a řazení](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
