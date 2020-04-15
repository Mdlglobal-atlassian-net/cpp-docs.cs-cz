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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 6a3d7ea81b2f6b1a7e87c706ca883394e02dff3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338140"
---
# <a name="remove-_wremove"></a>remove, _wremove

Odstraňte soubor.

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

*Cestu*<br/>
Cesta k odebrání souboru.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí hodnotu 0, pokud je soubor úspěšně odstraněn. V opačném případě vrátí -1 a nastaví **errno** buď **eACCES** označují, že cesta určuje soubor jen pro čtení, určuje adresář nebo je soubor otevřen, nebo **ENOENT** označuje, že název souboru nebo cesta nebyla nalezena.

Další informace o těchto a dalších návratových kódech naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

Funkce **remove** odstraní soubor určený *cestou.* **_wremove** je širokoznaková verze **_remove**; argument *cesty* k **_wremove** je řetězec s širokým znakem. **_wremove** a **_remove** se chovají stejně jinak. Všechny popisovače souboru musí být před odstraněním uzavřeny.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tremove**|**remove**|**remove**|**_wremove**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**remove**|\<stdio.h> \<nebo io.h>|
|**_wremove**|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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

### <a name="input-crt_removetxt"></a>Vstup: crt_remove.txt

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
