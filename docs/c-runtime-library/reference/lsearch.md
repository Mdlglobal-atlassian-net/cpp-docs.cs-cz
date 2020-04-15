---
title: _lsearch
ms.date: 4/2/2020
api_name:
- _lsearch
- _o__lsearch
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
- _lsearch
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: a6ef3d86ffe8f03da34d4a374bddda1452815672
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341638"
---
# <a name="_lsearch"></a>_lsearch

Provádí lineární hledání hodnoty; přidá na konec seznamu, pokud není nalezen. K dispozici je bezpečnější verze této funkce. viz [_lsearch_s](lsearch-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *_lsearch(
   const void *key,
   void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základnu pole, které mají být prohledány.

*Číslo*<br/>
Počet prvků.

*Šířka*<br/>
Šířka každého prvku pole.

*Porovnat*<br/>
Ukazatel na rutinu porovnání. První parametr je ukazatel na klíč pro vyhledávání. Druhý parametr je ukazatel na prvek pole, který má být porovnán s klíčem.

## <a name="return-value"></a>Návratová hodnota

Pokud je klíč nalezen, **_lsearch** vrátí ukazatel na prvek pole na *základně,* který odpovídá *klíči*. Pokud klíč nebyl nalezen, **_lsearch** vrátí ukazatel na nově přidanou položku na konci pole.

## <a name="remarks"></a>Poznámky

Funkce **_lsearch** provádí lineární hledání *klíče* hodnoty v poli *číselných* prvků, každý z *šířky* bajtů. Na rozdíl od **bsearch** **_lsearch** nevyžaduje řazení pole. Pokud *klíč* nebyl nalezen, **_lsearch** jej přidá na konec pole a přírůstky *číslo*.

Argument *porovnání* je ukazatel na rutinu dodanou uživatelem, která porovnává dva prvky pole a vrací hodnotu určující jejich vztah. **_lsearch** volá *porovnání* rutiny jednou nebo vícekrát během hledání, předávání ukazatelů na dva prvky pole na každé volání. *porovnat* musí porovnat prvky a vrátit buď nenulovou (což znamená, že prvky jsou různé) nebo 0 (což znamená, že prvky jsou identické).

Tato funkce ověřuje její parametry. Pokud *je hodnota porovnání*, *klíč* nebo *číslo* **null**nebo pokud je *hodnota* **NULL** a *číslo* je nenulová nebo pokud je *šířka* menší než nula, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **je chybné číslo** nastaveno na **hodnotu EINVAL** a funkce vrátí **hodnotu NULL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_lsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main(void)
{
   char * wordlist[4] = { "hello", "thanks", "bye" };
                            // leave room to grow...
   int n = 3;
   char **result;
   char *key = "extra";
   int i;

   printf( "wordlist before _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );

   result = (char **)_lsearch( &key, wordlist,
                      &n, sizeof(char *), compare );

   printf( "wordlist after _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );
}

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}
```

```Output
wordlist before _lsearch: hello thanks bye
wordlist after _lsearch: hello thanks bye extra
```

## <a name="see-also"></a>Viz také

[Vyhledávání a řazení](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
