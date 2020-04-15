---
title: _unlink, _wunlink
ms.date: 4/2/2020
api_name:
- _unlink
- _wunlink
- _o__unlink
- _o__wunlink
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
ms.openlocfilehash: ffc1a64c60d41246773d5e262523000355b0de3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361264"
---
# <a name="_unlink-_wunlink"></a>_unlink, _wunlink

Odstraňte soubor.

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

*Název_souboru*<br/>
Název souboru, který chcete odebrat.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0 v případě úspěchu. V opačném případě funkce vrátí -1 a nastaví **errno** na **EACCES**, což znamená, že cesta určuje soubor jen pro čtení nebo adresář nebo **ENOENT**, což znamená, že soubor nebo cesta nebyla nalezena.

Další informace o těchto a dalších návratových kódech naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

Funkce **_unlink** odstraní soubor určený *názvem souboru*. **_wunlink** je širokoznaková verze **_unlink**; argument *název souboru,* který **má _wunlink,** je řetězec s širokým znakem. Tyto funkce se chovají stejně jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tunlink**|**_unlink**|**_unlink**|**_wunlink**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_unlink**|\<io.h> \<a stdio.h>|
|**_wunlink**|\<io.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="code-example"></a>Příklad kódu

Tento program používá _unlink k odstranění CRT_UNLINK. Txt.

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

### <a name="input-crt_unlinktxt"></a>Vstup: crt_unlink.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Deleted 'CRT_UNLINK.TXT'
```

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[remove, _wremove](remove-wremove.md)<br/>
