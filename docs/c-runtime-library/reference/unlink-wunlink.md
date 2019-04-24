---
title: _unlink, _wunlink
ms.date: 11/04/2016
apiname:
- _unlink
- _wunlink
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
- _tunlink
- _unlink
- wunlink
- _wunlink
helpviewer_keywords:
- files [C++], deleting
- _wunlink function
- wunlink function
- unlink function
- _unlink function
- tunlink function
- files [C++], removing
- _tunlink function
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
ms.openlocfilehash: ec59a02f1302fe4a2149889cf1b48090d061d6b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268769"
---
# <a name="unlink-wunlink"></a>_unlink, _wunlink

Odstranění souboru.

## <a name="syntax"></a>Syntaxe

```C
int _unlink(
   const char *filename
);
int _wunlink(
   const wchar_t *filename
);
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Název souboru se má odebrat.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0 v případě úspěšného ověření. V opačném případě vrátí funkce hodnotu -1 a nastaví **errno** k **EACCES**, což znamená, že cesta Určuje jen pro čtení souboru nebo adresáře, nebo **ENOENT**, což znamená, že soubor nebo cesta nebyl nalezen.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratových kódů.

## <a name="remarks"></a>Poznámky

**_Unlink –** funkce odstraní soubor určený parametrem *filename*. **_wunlink –** je verze širokého znaku **_unlink –**; *filename* argument **_wunlink –** je širokoznaký řetězec. Tyto funkce chovají identicky jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tunlink**|**_unlink**|**_unlink**|**_wunlink**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_unlink**|\<io.h> and \<stdio.h>|
|**_wunlink**|\<IO.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="code-example"></a>Příklad kódu

Tento program využívá _unlink – odstranit CRT_UNLINK. TXT.

```C
// crt_unlink.c

#include <stdio.h>

int main( void )
{
   if( _unlink( "crt_unlink.txt" ) == -1 )
      perror( "Could not delete 'CRT_UNLINK.TXT'" );
   else
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );
}
```

### <a name="input-crtunlinktxt"></a>Vstup: crt_unlink.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Deleted 'CRT_UNLINK.TXT'
```

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[remove, _wremove](remove-wremove.md)<br/>
