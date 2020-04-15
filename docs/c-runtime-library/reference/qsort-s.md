---
title: qsort_s
ms.date: 4/2/2020
api_name:
- qsort_s
- _o_qsort_s
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
- qsort_s
helpviewer_keywords:
- arrays [C++], sorting
- quick-sort algorithm
- qsort_s function
- sorting arrays
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
ms.openlocfilehash: 6013098199e1b69d03dc9cf2780cbf4376abcc0d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332978"
---
# <a name="qsort_s"></a>qsort_s

Provádí rychlé řazení. Verze [qsort](qsort.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Začátek cílového pole.

*Číslo*<br/>
Velikost pole v prvcích.

*Šířka*<br/>
Velikost prvku v bajtů.

*Porovnat*<br/>
Funkce porovnání. První argument je ukazatel *kontextu.* Druhý argument je ukazatel na *klíč* pro hledání. Třetí argument je ukazatel na prvek pole, který má být porovnán s *klíčem*.

*Kontextu*<br/>
Ukazatel na kontext, který může být libovolný objekt, který musí mít rutina *porovnání* přístup.

## <a name="remarks"></a>Poznámky

Funkce **qsort_s** implementuje algoritmus rychlého řazení pro řazení pole *číselných* prvků, každý z *šířky* bajtů. *Základ* argumentu je ukazatel na základnu pole, které má být seřazeno. **qsort_s** přepíše toto pole seřazenými prvky. Porovnání *argumentů* je ukazatel na rutinu dodanou uživatelem, která porovnává dva prvky pole a vrací hodnotu určující jejich vztah. **qsort_s** volání *porovnání* rutiny jednou nebo vícekrát během řazení, předávání ukazatelů na dva prvky pole při každém volání:

```C
compare( context, (void *) & elem1, (void *) & elem2 );
```

Rutina musí porovnat prvky a pak vrátit jednu z následujících hodnot:

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|**elem1** méně než **elem2**|
|0|**elem1** ekvivalent **elem2**|
|> 0|**elem1** větší než **elem2**|

Pole je seřazeno v rostoucím pořadí, jak je definováno funkcí porovnání. Chcete-li seřadit pole v sestupném pořadí, obraťte pocit "větší než" a "menší než" ve funkci porovnání.

Pokud jsou funkci předány neplatné parametry, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí a **errno** je nastavena na **EINVAL**. Další informace naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="error-conditions"></a>Chybové stavy

|key|base|compare|num|šířka|errno|
|---------|----------|-------------|---------|-----------|-----------|
|**Null**|jakékoli|jakékoli|jakékoli|jakékoli|**EINVAL**|
|jakékoli|**Null**|jakékoli|!= 0|jakékoli|**EINVAL**|
|jakékoli|jakékoli|jakékoli|jakékoli|<= 0|**EINVAL**|
|jakékoli|jakékoli|**Null**|jakékoli|jakékoli|**EINVAL**|

**qsort_s** má stejné chování jako **qsort,** ale má *parametr kontextu* a nastaví **errno**. Předáním *parametru kontextu* mohou funkce porovnání použít ukazatel objektu pro přístup k funkcím objektu nebo k jiným informacím, které nejsou přístupné prostřednictvím ukazatele prvku. Přidání *parametru context* umožňuje **qsort_s** bezpečnější, protože *kontext* lze použít k zabránění reentrancy chyby zavedené pomocí statických proměnných zpřístupnit sdílené informace pro *funkci porovnání.*

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**qsort_s**|\<stdlib.h> \<a search.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovny:** Všechny verze [funkcí knihovny CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat parametr *kontextu* ve **funkci qsort_s.** Parametr *kontextu* usnadňuje provádění řazení bezpečných pro přístup z více vláken. Namísto použití statických proměnných, které musí být synchronizovány, aby byla zajištěna bezpečnost podprocesu, předajte v každém řazení jiný parametr *kontextu.* V tomto příkladu se jako parametr *kontextu* používá objekt národního prostředí.

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

## <a name="see-also"></a>Viz také

[Vyhledávání a řazení](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort](qsort.md)<br/>
