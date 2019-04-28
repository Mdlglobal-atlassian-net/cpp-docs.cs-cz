---
title: rename, _wrename
ms.date: 11/04/2016
apiname:
- rename
- _wrename
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 3536bfb6c38c99a8d6d943102fb9303dd4d85b7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357489"
---
# <a name="rename-wrename"></a>rename, _wrename

Přejmenování souboru nebo adresáře.

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

*newname*<br/>
Ukazatel na nový název.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0, pokud je úspěšné. V případě chyby, funkce vrátí nenulovou hodnotu a nastaví **errno** na jednu z následujících hodnot:

|Hodnota errno|Podmínka|
|-|-|
| **EACCES** | Soubor nebo adresář zadaný *newname* již existuje nebo jej nelze vytvořit (neplatná cesta); nebo *oldname* je adresář a *newname* Určuje jinou cestu. |
| **ENOENT** | Soubor nebo cesta zadaná položkou *oldname* nebyl nalezen. |
| **EINVAL** | Název obsahuje neplatné znaky. |

Je to možné návratové hodnoty, najdete v části [_doserrno, _errno, syserrlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Přejmenovat** funkce přejmenuje soubor nebo adresář zadaný *oldname* na název Dal *newname*. Starý název musí být cesta k existující soubor nebo adresář. Nový název nesmí být název existujícího souboru nebo adresáře. Můžete použít **přejmenovat** přesunout soubor do jiného zadáním jiné cestě z jednoho adresáře nebo zařízení *newname* argument. Však nelze používat **přejmenovat** přejděte do adresáře. Adresáře můžete přejmenovat, ale nepřesunuli.

**_wrename –** je verze širokého znaku **_rename**; argumenty, které mají **_wrename –** jsou širokoznaké řetězce. **_wrename –** a **_rename** se jinak chovají stejně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename –**|**Přejmenovat**|**Přejmenovat**|**_wrename**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Přejmenovat**|\<IO.h > nebo \<stdio.h >|
|**_wrename**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
