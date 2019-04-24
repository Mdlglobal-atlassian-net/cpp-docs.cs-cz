---
title: _lfind
ms.date: 11/04/2016
apiname:
- _lfind
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
- lfind
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 1508d54d6b2f2566e4aee3afef02af45b28e4f48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286489"
---
# <a name="lfind"></a>_lfind

Provádí lineárního hledání pro zadaný klíč. Bezpečnější verze této funkce je k dispozici. Zobrazit [_lfind_s –](lfind-s.md).

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
Objekt pro hledání.

*base*<br/>
Ukazatel na základní data vyhledávání.

*Číslo*<br/>
Počet prvků pole.

*Šířka*<br/>
Šířka prvků pole.

*compare*<br/>
Ukazatel na rutiny porovnání. První parametr je ukazatel na klíč pro hledání. Druhý parametr je ukazatel na prvek pole, která se má porovnat s klíčem.

## <a name="return-value"></a>Návratová hodnota

Pokud je nalezen klíč, **_lfind –** vrací ukazatel na prvek v poli *základní* , který odpovídá *klíč*. Pokud není nalezen klíč, **_lfind –** vrátí **NULL**.

## <a name="remarks"></a>Poznámky

**_Lfind –** funkce provádí lineárního hledání pro hodnotu *klíč* v poli *číslo* prvky, každý z *šířka* bajtů. Na rozdíl od **bsearch –**, **_lfind –** nevyžaduje, aby pole, který se má seřadit. *Základní* argument je ukazatel na základní pole, které chcete prohledat. *Porovnání* argument je ukazatel na uživatelem zadané rutinou, která porovná dva prvky pole a vrátí hodnotu určující, jejich vztahu. **_lfind –** volání *porovnání* rutinní jednou nebo vícekrát během hledání předání ukazatele do dvou prvků pole při každém volání. *Porovnání* rutina musí porovnat prvky a potom vrátí nenulovou hodnotu (tj. elementy se liší), nebo 0 (tj. elementy jsou identické).

Tato funkce ověřuje své parametry. Pokud *porovnání*, *klíč* nebo *číslo* je **NULL**, nebo pokud *základní* je **NULL**a *číslo* je nenulová nebo pokud *šířka* je menší než nula, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **NULL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lfind**|\<search.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
