---
title: _unlink, _wunlink
ms.date: 11/04/2016
api_name:
- _unlink
- _wunlink
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
ms.openlocfilehash: 878a1b4aa009bc8528dfac1908ed26c7e3b269ae
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957395"
---
# <a name="_unlink-_wunlink"></a>_unlink, _wunlink

Odstraní soubor.

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

*Bitmap*<br/>
Název souboru, který se má odebrat

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0, pokud bylo úspěšné. V opačném případě funkce vrátí hodnotu-1 a nastaví **errno** na **EACCES**, což znamená, že cesta Určuje soubor, který je jen pro čtení, nebo adresář, nebo na **ENOENT**, což znamená, že soubor nebo cestu nenaleznou.

Další informace o těchto a dalších návratových kódech naleznete v tématech [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Funkce **_unlink** odstraní soubor určený parametrem *filename*. **_wunlink** je **_unlink**verze s velkým znakem; Argument *filename* pro **_wunlink** je řetězec s velkým znakem. Tyto funkce se chovají identicky jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tunlink**|**_unlink**|**_unlink**|**_wunlink**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_unlink**|\<IO. h > a \<stdio. h >|
|**_wunlink**|\<IO. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="code-example"></a>Příklad kódu

Tento program používá _unlink k odstranění CRT_UNLINK. TXT.

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

### <a name="input-crt_unlinktxt"></a>Vstup: crt_unlink. txt

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
