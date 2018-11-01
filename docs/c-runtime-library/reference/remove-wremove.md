---
title: remove, _wremove
ms.date: 11/04/2016
apiname:
- _wremove
- remove
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
ms.openlocfilehash: d5636912ea36fd1b1412a556d516ac3e8184e0b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613965"
---
# <a name="remove-wremove"></a>remove, _wremove

Odstranění souboru.

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

*Cesta*<br/>
Cesta k souboru má být odebrán.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0, pokud soubor se úspěšně odstranil. V opačném případě vrátí hodnotu -1 a nastaví **errno** buď **EACCES** k označení, že cesta Určuje soubor jen pro čtení nebo je soubor otevřen, nebo **ENOENT** označuje, že Název souboru nebo cesta nebyla nalezena nebo že cesta Určuje adresář.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratových kódech.

## <a name="remarks"></a>Poznámky

**Odebrat** funkce odstraní soubor určený parametrem *cestu.* **_wremove –** je verze širokého znaku **_Odebrat**; *cesta* argument **_wremove –** je širokoznaký řetězec. **_wremove –** a **_Odebrat** se jinak chovají stejně. Všechny popisovače souboru musí být uzavřen, dříve než může být odstraněna.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tremove –**|**remove**|**remove**|**_wremove**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**remove**|\<stdio.h > nebo \<io.h >|
|**_wremove**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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

### <a name="input-crtremovetxt"></a>Vstup: crt_remove.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Deleted 'CRT_REMOVE.TXT'
```

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
