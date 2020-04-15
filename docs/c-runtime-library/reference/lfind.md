---
title: _lfind
ms.date: 4/2/2020
api_name:
- _lfind
- _o__lfind
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 287cbd8bc9cc567a4a0d5b9505d57098197bc545
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342179"
---
# <a name="_lfind"></a>_lfind

Provede lineární hledání zadaného klíče. K dispozici je bezpečnější verze této funkce. viz [_lfind_s](lfind-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *_lfind(
   const void *key,
   const void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základnu vyhledávacích dat.

*Číslo*<br/>
Počet prvků pole.

*Šířka*<br/>
Šířka prvků pole.

*Porovnat*<br/>
Ukazatel na srovnávací rutinu. První parametr je ukazatel na klíč pro vyhledávání. Druhý parametr je ukazatel na prvek pole, který má být porovnán s klíčem.

## <a name="return-value"></a>Návratová hodnota

Pokud je klíč nalezen, **_lfind** vrátí ukazatel na prvek pole na *základně,* který odpovídá *klíči*. Pokud klíč nebyl nalezen, **vrátí _lfind** **hodnotu NULL**.

## <a name="remarks"></a>Poznámky

Funkce **_lfind** provádí lineární hledání *klíče* hodnoty v poli *číselných* prvků, každý z *šířky* bajtů. Na rozdíl od **bsearch** **_lfind** nevyžaduje řazení pole. *Základní* argument je ukazatel na základnu pole, které má být prohledáno. Argument *porovnání* je ukazatel na rutinu dodanou uživatelem, která porovnává dva prvky pole a pak vrátí hodnotu určující jejich vztah. **_lfind** volání *porovnání* rutiny jednou nebo vícekrát během hledání, předávání ukazatelů na dva prvky pole na každé volání. Porovnání *compare* rutina musí porovnat prvky a potom vrátit nenulovou (což znamená, že prvky jsou různé) nebo 0 (což znamená, že prvky jsou identické).

Tato funkce ověřuje její parametry. Pokud *je hodnota porovnání*, *klíč* nebo *číslo* **null**nebo pokud je *hodnota* **NULL** a *číslo* je nenulová nebo pokud je *šířka* menší než nula, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **je chybné číslo** nastaveno na **hodnotu EINVAL** a funkce vrátí **hodnotu NULL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lfind**|\<search.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_lfind.c
// This program uses _lfind to search a string array
// for an occurrence of "hello".

#include <search.h>
#include <string.h>
#include <stdio.h>

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}

int main( )
{
   char *arr[] = {"Hi", "Hello", "Bye"};
   int n = sizeof(arr) / sizeof(char*);
   char **result;
   char *key = "hello";

   result = (char **)_lfind( &key, arr,
                      &n, sizeof(char *), compare );

   if( result )
      printf( "%s found\n", *result );
   else
      printf( "hello not found!\n" );
}
```

```Output
Hello found
```

## <a name="see-also"></a>Viz také

[Vyhledávání a řazení](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
