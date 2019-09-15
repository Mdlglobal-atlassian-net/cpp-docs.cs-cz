---
title: _fullpath, _wfullpath
ms.date: 11/04/2016
api_name:
- _fullpath
- _wfullpath
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wfullpath
- fullpath
- _wfullpath
- _fullpath
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
ms.openlocfilehash: 30e62716c496ebb1a39b53a420f372a6e743c2c0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956272"
---
# <a name="_fullpath-_wfullpath"></a>_fullpath, _wfullpath

Vytvoří absolutní nebo úplný název cesty pro zadaný relativní název cesty.

## <a name="syntax"></a>Syntaxe

```C
char *_fullpath(
   char *absPath,
   const char *relPath,
   size_t maxLength
);
wchar_t *_wfullpath(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength
);
```

### <a name="parameters"></a>Parametry

*absPath*<br/>
Ukazatel na vyrovnávací paměť obsahující absolutní nebo úplný název cesty nebo **hodnotu null**.

*relPath*<br/>
Název relativní cesty

*maxLength*<br/>
Maximální délka vyrovnávací paměti názvu absolutní cesty (*absPath*). Tato délka je v bajtech pro **_fullpath** , ale v různých znacích (**wchar_t**) pro **_wfullpath**.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na vyrovnávací paměť obsahující absolutní název cesty (*absPath*). Pokud se vyskytne chyba (například pokud hodnota předaná v *relPath* zahrnuje písmeno jednotky, které není platné nebo se nedá najít, nebo pokud je délka vytvořeného absolutního názvu cesty (*absPath*) větší než hodnota *MaxLength*), vrátí funkce **Hodnota null**.

## <a name="remarks"></a>Poznámky

Funkce **_fullpath** rozbalí název relativní cesty v *relPath* k jeho plně kvalifikované nebo absolutní cestě a uloží tento název v *absPath*. Pokud má AbsPath **hodnotu null** **, použije se k** přidělení vyrovnávací paměti dostatečné délky pro název cesty. Je odpovědností volajícího uvolnit tuto vyrovnávací paměť. Relativní cesta název určuje cestu k jinému umístění z aktuálního umístění (například aktuální pracovní adresář: "."). Absolutní cesta název je rozšíření názvu relativní cesty, které uvádí celou cestu nutnou k dosažení požadovaného umístění z kořenového adresáře systému souborů. Na rozdíl od **_makepath**se dá **_fullpath** použít k získání absolutní cesty pro relativní cesty (*relPath*), které zahrnují "./" nebo ".. v jejich názvech.

Například chcete-li použít rutiny run-time jazyka C, musí aplikace zahrnovat hlavičkové soubory, které obsahují deklarace pro rutiny. Každý soubor hlaviček include obsahuje odkazy na umístění souboru relativním způsobem (z pracovního adresáře aplikace):

```C
#include <stdlib.h>
```

v případě, že absolutní cesta (skutečné umístění systému souborů) souboru může být:

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath** automaticky zpracovává argumenty vícebajtového řetězce znaků podle potřeby a rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která se právě používá. **_wfullpath** je **_fullpath**verze s velkým znakem; řetězcové argumenty, které se mají **_wfullpath** , jsou řetězce s libovolným znakem. **_wfullpath** a **_fullpath** se chovají stejně, s výjimkou toho, že **_wfullpath** zpracovává řetězce vícebajtových znaků.

Pokud jsou definovány obě **_DEBUG** a **_CRTDBG_MAP_ALLOC** , volání **_fullpath** a **_wfullpath** jsou nahrazena voláními **_fullpath_dbg** a **_wfullpath_dbg** , aby bylo možné ladit přidělení paměti. Další informace najdete v tématu [_fullpath_dbg, _wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md).

Tato funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md), pokud *MAXLEN* je menší nebo rovno 0. Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **hodnotu null**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

Pokud má vyrovnávací paměť AbsPath **hodnotu null**, **_fullpath** [zavolá metodu](malloc.md) pro přidělení vyrovnávací paměti a ignoruje argument *MaxLength* . Je zodpovědností volajícího [uvolnit](free.md)tuto vyrovnávací paměť (podle potřeby). Pokud argument *relPath* určuje diskovou jednotku, bude aktuální adresář této jednotky kombinován s cestou.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<Stdlib. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fullpath.c
// This program demonstrates how _fullpath
// creates a full path from a partial path.

#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
#include <direct.h>

void PrintFullPath( char * partialPath )
{
   char full[_MAX_PATH];
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )
      printf( "Full path is: %s\n", full );
   else
      printf( "Invalid path\n" );
}

int main( void )
{
   PrintFullPath( "test" );
   PrintFullPath( "\\test" );
   PrintFullPath( "..\\test" );
}
```

```Output
Full path is: C:\Documents and Settings\user\My Documents\test
Full path is: C:\test
Full path is: C:\Documents and Settings\user\test
```

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
