---
title: rename, _wrename
ms.date: 4/2/2020
api_name:
- rename
- _wrename
- _o__wrename
- _o_rename
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wrename
- _trename
- Rename
helpviewer_keywords:
- trename function
- directories [C++], renaming
- renaming directories
- names [C++], changing file
- _trename function
- rename function
- wrename function
- files [C++], renaming
- _wrename function
- names [C++], changing directory
- renaming files
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
ms.openlocfilehash: b0a5f43d92d6dd85626f00bf5c2a6350e5bfa10f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917791"
---
# <a name="rename-_wrename"></a>rename, _wrename

Přejmenujte soubor nebo adresář.

## <a name="syntax"></a>Syntaxe

```C
int rename(
   const char *oldname,
   const char *newname
);
int _wrename(
   const wchar_t *oldname,
   const wchar_t *newname
);
```

### <a name="parameters"></a>Parametry

*oldname*<br/>
Ukazatel na starý název.

*nového*<br/>
Ukazatel na nový název.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0, pokud je úspěšná. Při chybě funkce vrátí nenulovou hodnotu a nastaví **errno** na jednu z následujících hodnot:

|hodnota errno|Podmínka|
|-|-|
| **EACCES** | Soubor nebo adresář určený parametrem *Nový_název* již existuje nebo jej nelze vytvořit (neplatná cesta); nebo *oldname* je adresář a *Nový_název* Určuje jinou cestu. |
| **ENOENT** | Soubor nebo cesta určená parametrem *oldname* se nenašly. |
| **EINVAL** | Název obsahuje neplatné znaky. |

Další možné návratové hodnoty naleznete v tématu [_doserrno, _errno, syserrlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **přejmenování** přejmenuje soubor nebo adresář určený parametrem *oldname* na název zadaný pomocí *Nový_název*. Starý název musí být cesta k existujícímu souboru nebo adresáři. Nový název nesmí být názvem existujícího souboru nebo adresáře. Pomocí parametru **Přejmenovat** můžete přesunout soubor z jednoho adresáře nebo zařízení do jiného tak, že v argumentu *Nový_název* zadáte jinou cestu. Nelze však použít příkaz **Přejmenovat** k přesunutí adresáře. Adresáře lze přejmenovat, ale nebudou přesunuty.

**_wrename** je verze **_rename**s velkým znakem; argumenty **_wrename** jsou řetězce s libovolným znakem. **_wrename** a **_rename** se chovají identicky jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename**|**Změňte**|**Změňte**|**_wrename**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Změňte**|\<IO. h> nebo \<stdio. h>|
|**_wrename**|\<stdio. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_renamer.c
/* This program attempts to rename a file named
* CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation
* to succeed, a file named CRT_RENAMER.OBJ must exist and
* a file named CRT_RENAMER.JBO must not exist.
*/

#include <stdio.h>

int main( void )
{
   int  result;
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";

   /* Attempt to rename file: */
   result = rename( old, new );
   if( result != 0 )
      printf( "Could not rename '%s'\n", old );
   else
      printf( "File '%s' renamed to '%s'\n", old, new );
}
```

### <a name="output"></a>Výstup

```Output
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'
```

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
