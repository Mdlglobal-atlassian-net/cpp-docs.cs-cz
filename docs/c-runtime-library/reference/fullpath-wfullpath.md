---
title: _fullpath –, _wfullpath – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b472987b0cac41c57e5fd22b2eedecef522613b4
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
---
# <a name="fullpath-wfullpath"></a>_fullpath, _wfullpath

Vytvoří název absolutní nebo úplnou cestu pro zadaný relativní cesta.

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
Ukazatel na vyrovnávací paměť obsahující název absolutní nebo úplné cesty, nebo **NULL**.

*relPath*<br/>
Relativní cesta.

*Hodnota maxLength*<br/>
Maximální délka vyrovnávací paměť názvu absolutní cestu (*absPath*). Se délka v bajtech pro **_fullpath –** , ale v široké znaky (**wchar_t**) pro **_wfullpath –**.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na vyrovnávací paměť obsahující absolutní cesta (*absPath*). Pokud dojde k chybě (například pokud je předaná hodnota *relPath* zahrnuje písmeno jednotky, které není platná nebo nebyla nalezena, nebo pokud délka názvu vytvořený absolutní cestu (*absPath*) je větší než *maxLength*), funkce vrátí hodnotu **NULL**.

## <a name="remarks"></a>Poznámky

**_Fullpath –** funkce rozšíří názvem relativní cesty v *relPath* jeho plně kvalifikovanou nebo absolutní cesta a ukládá tento název v *absPath*. Pokud *absPath* je **NULL**, **malloc** se používá k přidělení vyrovnávací paměti dostatečně dlouhé, aby udržení název cesty. Je zodpovědností volajícího, aby bez této vyrovnávací paměti. Relativní cesta Určuje cestu do jiného umístění z aktuálního umístění (například aktuální pracovní adresář: "."). Název absolutní cesta je rozšíření relativní cesta název, který stavy celou cestu potřebné k dosažení požadované umístění z kořenového adresáře systému souborů. Na rozdíl od **_makepath –**, **_fullpath –** lze použít k získání názvu absolutní cesta relativní cesty (*relPath*), zahrnují ". /"nebo".. nebo "v jejich názvy.

Pokud chcete používat C běhové rutiny, například žádost musí obsahovat soubory hlaviček, které obsahují deklarace pro rutiny. Každý soubor hlaviček patří příkaz odkazy na umístění souboru relativní způsobem (z pracovní adresář aplikace):

```C
#include <stdlib.h>
```

Když může být absolutní cesta k souboru (skutečné umístění systému souborů):

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath –** automaticky zpracovává argumenty řetězce vícebajtových znaků podle potřeby, rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky aktuálně používán. **_wfullpath –** je verze široká charakterová **_fullpath –**; argumenty řetězce, které mají **_wfullpath –** jsou široká charakterová řetězce. **_wfullpath –** a **_fullpath –** vyjma toho, že se chovají stejně jako **_wfullpath –** nezpracovává řetězců vícebajtových znaků.

Pokud **_DEBUG –** a **_crtdbg_map_alloc –** jsou obě definovány, volání **_fullpath –** a **_wfullpath –** jsou nahrazovány volání **_fullpath_dbg –** a **_wfullpath_dbg –** umožňující ladění přidělení paměti. Další informace najdete v tématu [_fullpath_dbg –, _wfullpath_dbg –](fullpath-dbg-wfullpath-dbg.md).

Tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md), pokud *maxlen* je menší než nebo rovna 0. Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **NULL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath –**|**_fullpath –**|**_wfullpath**|

Pokud *absPath* vyrovnávací paměť je **NULL**, **_fullpath –** volání [malloc –](malloc.md) přidělit vyrovnávací paměť a ignoruje *maxLength*  argument. Je zodpovědností má volající se zrušit přidělení této vyrovnávací paměti (pomocí [volné](free.md)) podle potřeby. Pokud *relPath* argument určuje diskovou jednotku, aktuální adresář této jednotky je v kombinaci s cestou.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fullpath –**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
