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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 730458c5027f8f690e8238b29cbdb1056f09ed68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338104"
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
Ukazatel na staré jméno.

*Newname*<br/>
Ukazatel na nový název.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0, pokud je úspěšná. Při chybě funkce vrátí nenulovou hodnotu a nastaví **chybně** na jednu z následujících hodnot:

|hodnota errno|Podmínka|
|-|-|
| **ACCACCES** | Soubor nebo adresář určený *novým názvem* již existuje nebo nemohl být vytvořen (neplatná cesta); nebo *oldname* je adresář a *newname* určuje jinou cestu. |
| **ENOENT** | Soubor nebo cesta určená *oldname* nebyl nalezen. |
| **EINVAL** | Název obsahuje neplatné znaky. |

Další možné vrácené hodnoty naleznete [v tématu _doserrno, _errno, syserrlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **přejmenování** přejmenuje soubor nebo adresář určený *starým názvem* na název pod názvem *newname*. Starý název musí být cestou existujícího souboru nebo adresáře. Nový název nesmí být název existujícího souboru nebo adresáře. Přejmenování **rename** můžete použít k přesunutí souboru z jednoho adresáře nebo zařízení do jiného tím, že v argumentu *newname* poskytnete jinou cestu. K přesunutí adresáře však nelze použít **přejmenování.** Adresáře lze přejmenovat, ale nepřesunout.

**_wrename** je širokoznaková verze **_rename**; argumenty, které **mají _wrename,** jsou řetězce s širokými znaky. **_wrename** a **_rename** se chovají stejně jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename**|**Přejmenovat**|**Přejmenovat**|**_wrename**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Přejmenovat**|\<io.h> \<nebo stdio.h>|
|**_wrename**|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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
