---
title: _lsearch – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f38dd8a23cce652b93794f62c775962482fe159
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="lsearch"></a>_lsearch

Provede lineárního hledání pro hodnotu; Přidá na konec seznamu, pokud není nalezen. Bezpečnější verze této funkce je k dispozici. v tématu [_lsearch_s –](lsearch-s.md).

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
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základní pole má proběhnout.

*Číslo*<br/>
Počet elementů.

*Šířka*<br/>
Šířka každého pole elementu.

*compare*<br/>
Ukazatel na rutiny porovnání. První parametr je ukazatel na klíč pro vyhledávání. Druhý parametr je ukazatel na element pole, který se má porovnat s klíčem.

## <a name="return-value"></a>Návratová hodnota

Pokud je nalezen klíč, **_lsearch –** vrací ukazatel na element pole v *základní* odpovídající *klíč*. Pokud není nalezen klíč, **_lsearch –** vrací ukazatel na nově přidané položky na konci tohoto pole.

## <a name="remarks"></a>Poznámky

**_Lsearch –** funkce provádí lineárního hledání pro hodnotu *klíč* v pole *číslo* elementy, každý z *šířka* bajtů. Na rozdíl od **bsearch –**, **_lsearch –** nevyžaduje pole, která se má seřadit. Pokud *klíč* není nalezen, **_lsearch –** přidá na konec pole a zvýší *číslo*.

*Porovnat* argument je ukazatel na rutiny zadanou uživatelem, který porovnává dva elementy pole a vrátí hodnotu udávající, jejich vztahu. **_lsearch –** volání *porovnat* rutiny jeden či více krát během hledání, předávání ukazatele na dva elementy pole při každém volání. *porovnání* musí porovnat elementy a vrátit buď nenulové hodnoty (tj. elementy se liší), nebo 0 (tj. elementy jsou identické).

Tato funkce ověří jeho parametry. Pokud *porovnat*, *klíč* nebo *číslo* je **NULL**, nebo pokud *základní* má hodnotu NULL a **číslo*  je nenulové hodnoty, nebo pokud *šířka* je menší než nula, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a funkce vrátí hodnotu **NULL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lsearch**|\<Search.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
