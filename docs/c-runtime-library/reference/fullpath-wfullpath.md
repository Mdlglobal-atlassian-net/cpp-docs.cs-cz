---
title: _fullpath, _wfullpath
ms.date: 11/04/2016
apiname:
- _fullpath
- _wfullpath
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
ms.openlocfilehash: aeacaf581b7f33ee893754c192ae547376ce73ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550394"
---
# <a name="fullpath-wfullpath"></a>_fullpath, _wfullpath

Vytvoří název protokolu absolutní nebo úplnou cestu pro název zadaná relativní cesta.

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
Ukazatel do vyrovnávací paměti obsahující název absolutní nebo úplnou cestu nebo **NULL**.

*relPath*<br/>
Relativní cesta.

*maxLength*<br/>
Maximální délka vyrovnávací paměti název absolutní cesta (*absPath*). Se délka v bajtech pro **_fullpath –** , ale v široké znaky (**wchar_t**) pro **_wfullpath –**.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel do vyrovnávací paměti, který obsahuje absolutní cesta (*absPath*). Pokud dojde k chybě (například, pokud hodnota předaná v *relPath* obsahuje písmeno jednotky, který není platný nebo se nedá najít, nebo pokud délka názvu vytvořená absolutní cesta (*absPath*) je větší než *maxLength*), funkce vrátí **NULL**.

## <a name="remarks"></a>Poznámky

**_Fullpath –** funkce rozšiřuje název relativní cesty v *relPath* jeho plně kvalifikovaný nebo absolutní cestu a ukládá tento název v *absPath*. Pokud *absPath* je **NULL**, **malloc** se používá k přidělení vyrovnávací paměti dostatečně dlouhé pro uchování název cesty. Je odpovědností volajícího uvolnit této vyrovnávací paměti. Relativní cesta Určuje cestu z aktuálního umístění do jiného umístění (jako je například aktuální pracovní adresář: "."). Představuje název absolutní cesta je rozšíření relativní název cesty, která uvádí celou cestu potřebné k dosažení požadovaného umístění z kořenového adresáře systému souborů. Na rozdíl od **_makepath –**, **_fullpath –** slouží k získání absolutní cesta pro relativní cesty (*relPath*), které zahrnují ". /"nebo".. / "v názvu.

Pro použití rutin C za běhu, třeba aplikace musí obsahovat soubory hlaviček, které obsahují deklarace pro rutiny. Každý soubor hlaviček zahrnují odkazy na prohlášení umístění souboru relativní způsobem (z aplikace pracovní adresář):

```C
#include <stdlib.h>
```

Když může být absolutní cestu k souboru (skutečné umístění systému souborů):

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath –** automaticky zpracovává argumenty vícebajtových řetězců znaků podle potřeby, rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která aktuálně používán. **_wfullpath –** je verze širokého znaku **_fullpath –**; řetězcové argumenty **_wfullpath –** jsou širokoznaké řetězce. **_wfullpath –** a **_fullpath –** chovají stejně, s výjimkou, že **_wfullpath –** nezpracovává vícebajtové znakové řetězce.

Pokud **_DEBUG** a **_CRTDBG_MAP_ALLOC** jsou definovány, volání **_fullpath –** a **_wfullpath –** jsou nahrazena voláními **_fullpath_dbg –** a **_wfullpath_dbg –** umožňuje ladit přidělování paměti. Další informace najdete v tématu [_fullpath_dbg – _wfullpath_dbg –](fullpath-dbg-wfullpath-dbg.md).

Tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md), pokud *maxlen* je menší než nebo rovna 0. Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí **NULL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath –**|**_fullpath –**|**_wfullpath**|

Pokud *absPath* vyrovnávací paměť je **NULL**, **_fullpath –** volání [malloc](malloc.md) přidělit vyrovnávací paměť a ignoruje *maxLength*  argument. Je odpovědností volajícího uvolnit této vyrovnávací paměti (pomocí [bezplatné](free.md)) podle potřeby. Pokud *relPath* argument určuje diskovou jednotku, je aktuální adresáře této jednotky kombinovat s cestou.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fullpath –**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
