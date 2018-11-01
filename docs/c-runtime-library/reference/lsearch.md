---
title: _lsearch
ms.date: 11/04/2016
apiname:
- _lsearch
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
f1_keywords:
- _lsearch
- lsearch
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: 340e8ac382972b15acc52013d5d6a51352db969c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532808"
---
# <a name="lsearch"></a>_lsearch

Provádí lineárního hledání pro hodnotu; Přidá na konec seznamu, pokud není nalezen. Bezpečnější verze této funkce je k dispozici. Zobrazit [_lsearch_s –](lsearch-s.md).

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

*Klíč*<br/>
Objekt pro hledání.

*base*<br/>
Ukazatel na základní pole, které chcete prohledat.

*Číslo*<br/>
Počet prvků.

*Šířka*<br/>
Šířka každého prvku pole.

*compare*<br/>
Ukazatel na rutiny porovnání. První parametr je ukazatel na klíč pro hledání. Druhý parametr je ukazatel na prvek pole k porovnání s klíči.

## <a name="return-value"></a>Návratová hodnota

Pokud je nalezen klíč, **_lsearch –** vrací ukazatel na prvek v poli *základní* , který odpovídá *klíč*. Pokud není nalezen klíč, **_lsearch –** vrací ukazatel na nově přidané položky na konec pole.

## <a name="remarks"></a>Poznámky

**_Lsearch –** funkce provádí lineárního hledání pro hodnotu *klíč* v poli *číslo* prvky, každý z *šířka* bajtů. Na rozdíl od **bsearch –**, **_lsearch –** nevyžaduje, aby pole, který se má seřadit. Pokud *klíč* nenajde, **_lsearch –** přidá na konec objektu array a zvýší hodnotu *číslo*.

*Porovnání* argument je ukazatel na uživatelem zadané rutinou, která porovná dva prvky pole a vrátí hodnotu určující jejich vztahu. **_lsearch –** volání *porovnání* rutinní jednou nebo vícekrát během hledání předání ukazatele do dvou prvků pole při každém volání. *porovnání* musí porovnat prvky a buď vrátí nenulovou hodnotu (tj. elementy se liší), nebo 0 (tj. elementy jsou identické).

Tato funkce ověřuje své parametry. Pokud *porovnání*, *klíč* nebo *číslo* je **NULL**, nebo pokud *základní* je **NULL**a *číslo* je nenulová nebo pokud *šířka* je menší než nula, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **NULL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lsearch**|\<Search.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
