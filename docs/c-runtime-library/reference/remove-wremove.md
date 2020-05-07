---
title: remove, _wremove
ms.date: 4/2/2020
api_name:
- _wremove
- remove
- _o__wremove
- _o_remove
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
- remove
- _wremove
- _tremove
helpviewer_keywords:
- tremove function
- _wremove function
- files [C++], deleting
- _tremove function
- files [C++], removing
- wremove function
- remove function
ms.assetid: b6345ec3-3289-4645-93a4-28b9e478cc19
ms.openlocfilehash: bf3eedaa9c24e7385686e2343857e69171e43090
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917842"
---
# <a name="remove-_wremove"></a>remove, _wremove

Odstraní soubor.

## <a name="syntax"></a>Syntaxe

```C
int remove(
   const char *path
);
int _wremove(
   const wchar_t *path
);
```

### <a name="parameters"></a>Parametry

*dílčí*<br/>
Cesta k souboru, který se má odebrat

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí hodnotu 0, pokud je soubor úspěšně odstraněn. V opačném případě vrátí hodnotu-1 a nastaví **errno** buď na **EACCES** , aby označoval, že cesta Určuje soubor, který je jen pro čtení, určí adresář, nebo je soubor otevřen nebo **ENOENT** , aby označoval, že název souboru nebo cesta nebyla nalezena.

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Funkce **Remove** odstraní soubor určený *cestou.* **_wremove** je verze **_remove**s velkým znakem; Argument *cesty* pro **_wremove** je řetězec s velkým znakem. **_wremove** a **_remove** se chovají identicky jinak. Aby bylo možné odstranit všechny popisovače souboru, je třeba jej zavřít.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tremove**|**remove**|**remove**|**_wremove**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**remove**|\<stdio. h> nebo \<IO. h>|
|**_wremove**|\<stdio. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_remove.c
/* This program uses remove to delete crt_remove.txt */

#include <stdio.h>

int main( void )
{
   if( remove( "crt_remove.txt" ) == -1 )
      perror( "Could not delete 'CRT_REMOVE.TXT'" );
   else
      printf( "Deleted 'CRT_REMOVE.TXT'\n" );
}
```

### <a name="input-crt_removetxt"></a>Vstup: crt_remove. txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Deleted 'CRT_REMOVE.TXT'
```

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
