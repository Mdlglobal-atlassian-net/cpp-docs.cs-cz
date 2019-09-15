---
title: qsort_s
ms.date: 11/04/2016
api_name:
- qsort_s
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
- qsort_s
helpviewer_keywords:
- arrays [C++], sorting
- quick-sort algorithm
- qsort_s function
- sorting arrays
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
ms.openlocfilehash: aa911dbf2990bb976341a19cdb1eb88707c90e79
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949762"
---
# <a name="qsort_s"></a>qsort_s

Provede rychlé řazení. Verze [qsort](qsort.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
void qsort_s(
   void *base,
   size_t num,
   size_t width,
   int (__cdecl *compare )(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Parametry

*base*<br/>
Začátek cílového pole

*Automatické*<br/>
Velikost pole v elementech

*Šířka*<br/>
Velikost elementu v bajtech

*compare*<br/>
Funkce porovnání. První argument je *kontextový* ukazatel. Druhý argument je ukazatel na *klíč* pro hledání. Třetí argument je ukazatel na prvek pole, který má být porovnán s *klíčem*.

*context*<br/>
Ukazatel na kontext, který může být libovolný objekt, ke kterému má rutina *porovnání* potřebovat přístup.

## <a name="remarks"></a>Poznámky

Funkce **qsort_s** implementuje algoritmus rychlého řazení pro řazení pole *číselných* prvků, z každé *šířky* bajtů. *Základem* argumentu je ukazatel na základ pole, které má být seřazeno. **qsort_s** přepíše toto pole setříděnými prvky. Argument *Compare* je ukazatel na uživatelsky zadanou rutinu, která porovná dva prvky pole a vrátí hodnotu určující jejich relaci. **qsort_s** volá rutinu *porovnání* jednou nebo víckrát během řazení a předá ukazatelům dva prvky pole při každém volání:

```C
compare( context, (void *) & elem1, (void *) & elem2 );
```

Rutina musí porovnat prvky a pak vracet jednu z následujících hodnot:

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|**elem1** menší než **elem2**|
|0|**elem1** ekvivalent **elem2**|
|> 0|**elem1** větší než **elem2**|

Pole je seřazené ve vzestupném pořadí, jak je definováno funkcí porovnání. Chcete-li seřadit pole v klesajícím pořadí, obraťte se na výraz "větší než" a "menší než" v rámci funkce porovnání.

Pokud jsou funkci předány neplatné parametry, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí a **errno** se nastaví na **EINVAL**. Další informace najdete v tématech [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|klíč|base|compare|počet|šířka|errno|
|---------|----------|-------------|---------|-----------|-----------|
|**NULL**|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|**EINVAL**|
|Jakýmikoli|**NULL**|Jakýmikoli|!= 0|Jakýmikoli|**EINVAL**|
|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|<= 0|**EINVAL**|
|Jakýmikoli|Jakýmikoli|**NULL**|Jakýmikoli|Jakýmikoli|**EINVAL**|

**qsort_s** má stejné chování jako **qsort** , ale má *kontextový* parametr a nastavuje **errno**. Předáním *kontextového* parametru mohou funkce porovnání použít ukazatel na objekt pro přístup k funkcionalitě objektu nebo jiným informacím, které nejsou přístupné prostřednictvím ukazatele na prvek. Přidání *kontextového* parametru vede k **qsort_sější** zabezpečení, protože *kontext* lze použít k tomu, aby se zabránilo chybám Vícenásobný přístup zavedeným pomocí statických proměnných, aby byly k dispozici sdílené informace pro funkci *Compare* .

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**qsort_s**|\<Stdlib. h > a \<Search. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovna** Všechny verze [funkcí knihovny CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít *kontextový* parametr ve funkci **qsort_s** . *Kontextový* parametr usnadňuje provádění řazení z více vláken. Namísto použití statických proměnných, které musí být synchronizovány, aby bylo zajištěno zabezpečení vlákna, předejte v každém řazení jiný *kontextový* parametr. V tomto příkladu se jako *kontextový* parametr používá objekt národního prostředí.

```cpp
// crt_qsort_s.cpp
// compile with: /EHsc /MT
#include <stdlib.h>
#include <stdio.h>
#include <search.h>
#include <process.h>
#include <locale.h>
#include <locale>
#include <windows.h>
using namespace std;

// The sort order is dependent on the code page.  Use 'chcp' at the
// command line to change the codepage.  When executing this application,
// the command prompt codepage must match the codepage used here:

#define CODEPAGE_850

#ifdef CODEPAGE_850
// Codepage 850 is the OEM codepage used by the command line,
// so \x00e1 is the German Sharp S in that codepage and \x00a4
// is the n tilde.

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00a4ol", "Espa\x00a4" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.850"
#define SPANISH_LOCALE "Spanish_Spain.850"
#define ENGLISH_LOCALE "English_US.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S and \x001f for the n tilde.
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00f1ol", "Espa\x00f1" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.1252"
#define SPANISH_LOCALE "Spanish_Spain.1252"
#define ENGLISH_LOCALE "English_US.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making sort_array vulnerable to thread
// conflicts.

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char s1[256];
    char s2[256];
    strcpy_s(s1, 256, *(char**)str1);
    strcpy_s(s2, 256, *(char**)str2);
    _strlwr_s( s1, sizeof(s1) );
    _strlwr_s( s2, sizeof(s2) );

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(s1,
       &s1[strlen(s1)], s2, &s2[strlen(s2)]);

}

void sort_array(char *array[], int num, locale &loc)
{
    qsort_s(array, num, sizeof(char*), compare, &loc);
}

void print_array(char *a[], int c)
{
   for (int i = 0; i < c; i++)
      printf("%s ", a[i]);
   printf("\n");

}

void sort_german(void * Dummy)
{
   sort_array(array1, 6, locale(GERMAN_LOCALE));
}

void sort_spanish(void * Dummy)
{
   sort_array(array2, 3, locale(SPANISH_LOCALE));
}

void sort_english(void * Dummy)
{
   sort_array(array3, 3, locale(ENGLISH_LOCALE));
}

int main( )
{
   int i;
   HANDLE threads[3];

   printf("Unsorted input:\n");
   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);

   // Create several threads that perform sorts in different
   // languages at the same time.

   threads[0] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_german , 0, NULL));
   threads[1] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_spanish, 0, NULL));
   threads[2] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_english, 0, NULL));

   for (i = 0; i < 3; i++)
   {
      if (threads[i] == reinterpret_cast<HANDLE>(-1))
      {
         printf("Error creating threads.\n");
         exit(1);
      }
   }

   // Wait until all threads have terminated.
   WaitForMultipleObjects(3, threads, true, INFINITE);

   printf("Sorted output: \n");

   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);
}
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Unsorted input:
weiß weis annehmen weizen Zeit weit
Español España espantado
table tableux tablet
Sorted output:
annehmen weiß weis weit weizen Zeit
España Español espantado
table tablet tableux
```

## <a name="see-also"></a>Viz také:

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort](qsort.md)<br/>
