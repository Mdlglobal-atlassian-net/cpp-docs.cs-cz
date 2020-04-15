---
title: _fullpath, _wfullpath
ms.date: 4/2/2020
api_name:
- _fullpath
- _wfullpath
- _o__fullpath
- _o__wfullpath
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
ms.openlocfilehash: 0910cf4f39e00be84e683cd6f3b9afbeb3f2a749
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345488"
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
Ukazatel na vyrovnávací paměť obsahující absolutní nebo úplný název cesty nebo **NULL**.

*relPath*<br/>
Relativní název cesty.

*Maxlength*<br/>
Maximální délka vyrovnávací paměti absolutního názvu cesty (*absPath*). Tato délka je v bajtů pro **_fullpath,** ale v široké znaky (**wchar_t**) pro **_wfullpath**.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí ukazatel na vyrovnávací paměť obsahující absolutní název cesty (*absPath*). Pokud dojde k chybě (například pokud hodnota předaná v *relPath* obsahuje písmeno jednotky, které není platné nebo nelze najít, nebo pokud je délka vytvořeného absolutního názvu cesty (*absPath*) větší než *maxLength*), vrátí funkce **hodnotu NULL**.

## <a name="remarks"></a>Poznámky

Funkce **_fullpath** rozšíří relativní název cesty v *relPath* na plně kvalifikovanou nebo absolutní cestu a uloží tento název v *absPath*. Pokud *absPath* je **NULL**, **malloc** se používá k přidělení vyrovnávací paměti dostatečné délky pro uložení názvu cesty. Je odpovědností volajícího k uvolnění této vyrovnávací paměti. Relativní název cesty určuje cestu k jinému umístění z aktuálního umístění (například aktuální pracovní adresář: "."). Absolutní název cesty je rozšíření relativní název cesty, který uvádí celou cestu potřebnou k dosažení požadovaného umístění z kořenového adresáře systému souborů. Na rozdíl od **_makepath**lze **_fullpath** získat absolutní název cesty pro relativní cesty (*relPath),* které obsahují "./" nebo ".. /" na jejich jména.

Chcete-li například použít rutiny c run-time, aplikace musí obsahovat soubory hlaviček, které obsahují deklarace pro rutiny. Každý soubor záhlaví obsahuje příkaz odkazuje na umístění souboru relativním způsobem (z pracovního adresáře aplikace):

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <stdlib.h>
```

pokud absolutní cesta (skutečné umístění systému souborů) souboru může být:

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath** podle potřeby automaticky zpracovává argumenty vícebajtových řetězců a rozpozná se sekvence vícebajtových znaků podle aktuálně používáné vícebajtové znakové stránky. **_wfullpath** je širokoznaková verze **_fullpath**; argumenty řetězce, které **mají _wfullpath,** jsou řetězce s širokými znaky. **_wfullpath** a **_fullpath** se chovají stejně s tím rozdílem, že **_wfullpath** nezpracovává vícebajtové řetězce znaků.

Pokud jsou definovány **_DEBUG** a **_CRTDBG_MAP_ALLOC,** volání **_fullpath** a **_wfullpath** jsou nahrazeny voláními **_fullpath_dbg** a **_wfullpath_dbg,** aby bylo možné ladit přidělení paměti. Další informace naleznete [v tématu _fullpath_dbg, _wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md).

Tato funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md), pokud *je hodnota maxlen* menší nebo rovna 0. Pokud je spuštění povoleno pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **hodnotu NULL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

Pokud je vyrovnávací paměť *absPath* **null**, **_fullpath** volání [malloc](malloc.md) přidělit vyrovnávací paměti a ignoruje *argument maxLength.* Je odpovědností volajícího navrátit tuto vyrovnávací paměť (pomocí [free)](free.md)podle potřeby. Pokud argument *relPath* určuje diskovou jednotku, bude aktuální adresář této jednotky kombinován s cestou.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
