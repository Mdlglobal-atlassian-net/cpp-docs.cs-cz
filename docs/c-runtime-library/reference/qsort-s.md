---
title: "qsort_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: qsort_s
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
apitype: DLLExport
f1_keywords: qsort_s
dev_langs: C++
helpviewer_keywords:
- arrays [C++], sorting
- quick-sort algorithm
- qsort_s function
- sorting arrays
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 333473d0b0b7e50e2b0faebef02835dcaf577440
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="qsorts"></a>qsort_s
Provede rychlé řazení. Verzi [qsort –](../../c-runtime-library/reference/qsort.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void qsort_s(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `base`  
 Spuštění cílového pole.  
  
 `num`  
 Velikost pole v elementech.  
  
 `width`  
 Element velikost v bajtech.  
  
 `compare`  
 Porovnání funkce. První argument je `context` ukazatel. Druhý argument je ukazatel `key` pro hledání. Třetí argument je ukazatel na element pole, který se má porovnat s `key`.  
  
 `context`  
 Ukazatel na kontext, který může být libovolná objektu, který `compare` rutiny potřebuje přístup k.  
  
## <a name="remarks"></a>Poznámky  
 `qsort_s` Funkce implementuje algoritmus rychlého řazení seřadit pole `num` elementy, každý z `width` bajtů. Argument `base` je ukazatel na základní pole, která se má seřadit. `qsort_s`Toto pole přepíše seřazené elementy. Argument `compare` je ukazatel na rutiny zadanou uživatelem, který porovnává dva elementy pole a vrátí hodnotu udávající, jejich vztahu. `qsort_s`volání `compare` rutiny jeden či více krát při řazení, předávání ukazatele na dva elementy pole při každém volání:  
  
```  
compare( context, (void *) & elem1, (void *) & elem2 );  
```  
  
 Rutiny musí porovnat elementy a pak se vraťte jednu z následujících hodnot:  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|< 0|`elem1`menší než`elem2`|  
|0|`elem1`ekvivalent hodnoty`elem2`|  
|> 0|`elem1`větší než`elem2`|  
  
 Pole je seřadit ve vzestupném pořadí, podle definice funkce porovnání. Do pole v sestupném pořadí řazení, reverse smysl "větší než" a "menší než" ve funkci porovnání.  
  
 Pokud jsou předány neplatné parametry pro funkce, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, pak funkce vrátí hodnotu a `errno` je nastaven na `EINVAL`. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|klíč|base|compare|Poče|šířka|Kód chyby|  
|---------|----------|-------------|---------|-----------|-----------|  
|`NULL`|všechny|všechny|všechny|všechny|`EINVAL`|  
|všechny|`NULL`|všechny|!= 0|všechny|`EINVAL`|  
|všechny|všechny|všechny|všechny|<= 0|`EINVAL`|  
|všechny|všechny|`NULL`|všechny|všechny|`EINVAL`|  
  
 `qsort_s`má stejné chování jako `qsort` , ale má `context` parametr a nastaví `errno`. Předáním `context` parametr porovnání funkcí můžete použít ukazatele na objekt přístup k objektu funkce nebo jiné informace není k dispozici prostřednictvím ukazatele k elementu. Přidání `context` parametr díky `qsort_s` bezpečnější, protože `context` umožňuje vyhnout opětovné zadání chyby zavedená pomocí statické proměnné a zpřístupněte sdílené informace k `compare` funkce.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`qsort_s`|\<stdlib.h > a \<search.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
 **Knihovny:** všechny verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `context` parametr ve `qsort_s` funkce. `context` Parametr usnadňuje provést řazení bezpečné pro přístup z více vláken. Místo použití statické proměnné, které musí být synchronizovány pro zajištění bezpečnosti přístup z více vláken, předat jiné `context` parametr v každém řazení. V tomto příkladu se používá objekt národního prostředí, jako `context` parametr.  
  
```  
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
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
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
 [Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch_s –](../../c-runtime-library/reference/bsearch-s.md)   
 [_lsearch_s –](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)