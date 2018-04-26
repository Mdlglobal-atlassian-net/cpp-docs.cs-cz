---
title: _getcwd –, _wgetcwd – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wgetcwd
- _getcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd
- wgetcwd
- _wgetcwd
- tgetcwd
- _tgetcwd
dev_langs:
- C++
helpviewer_keywords:
- getcwd function
- working directory
- _wgetcwd function
- _getcwd function
- current working directory
- wgetcwd function
- directories [C++], current working
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7399c393199b59baf05f0ef4fd947cef60daf0c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="getcwd-wgetcwd"></a>_getcwd, _wgetcwd

Získá aktuální pracovní adresář.

## <a name="syntax"></a>Syntaxe

```C
char *_getcwd(
   char *buffer,
   int maxlen
);
wchar_t *_wgetcwd(
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro cestu.

*MAXLEN*<br/>
Maximální délka cesty ve znacích: **char** pro **_getcwd –** a **wchar_t** pro **_wgetcwd –**.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na *vyrovnávací paměti*. A **NULL** návratová hodnota určuje chybu, a **errno** nastavený buď na **enomem –**, označující, že je nedostatek paměti k přidělení *maxlen* bajtů (při **NULL** argument je zadána jako *vyrovnávací paměti*), nebo **erange –**, která znamená, že cesta je delší než *maxlen*  znaků. Pokud *maxlen* je menší než nebo rovna nule, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Getcwd –** funkce získá úplnou cestu aktuálního pracovního adresáře pro výchozí jednotce a ukládá je v *vyrovnávací paměti*. Argument celé číslo *maxlen* určuje maximální délku cesty. Pokud překročí délka cesty (včetně ukončující znak hodnoty null), dojde k chybě *maxlen*. *Vyrovnávací paměti* argument může být **NULL**; vyrovnávací paměti o velikosti alespoň *maxlen* (více pouze v případě potřeby) je automaticky přiděleno, pomocí **malloc –**, k uložení cestu. Této vyrovnávací paměti může být uvolněno později voláním **volné** a předání **_getcwd –** vrátit hodnotu (ukazatel na přidělené vyrovnávací paměti).

**_getcwd –** vrátí řetězec, který představuje cestu aktuálního pracovního adresáře. Pokud aktuální pracovní adresář je kořenový adresář, řetězec končí zpětné lomítko ( **\\** ). Pokud je aktuální pracovní adresář nastaven na jiný adresář než kořenový, řetězec končí názvem adresáře, nikoli zpětným lomítkem.

**_wgetcwd –** je verze široká charakterová **_getcwd –**; *vyrovnávací paměti* argument a vrátí hodnotu **_wgetcwd –** jsou široká charakterová řetězce. **_wgetcwd –** a **_getcwd –** chovat jinak shodně.

Když **_DEBUG –** a **_crtdbg_map_alloc –** jsou definovány, volání **_getcwd –** a **_wgetcwd –** jsou nahrazovány volání **_ getcwd_dbg –** a **_wgetcwd_dbg –** umožňující ladění přidělení paměti. Další informace najdete v tématu [_getcwd_dbg –, _wgetcwd_dbg –](getcwd-dbg-wgetcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getcwd**|\<Direct.h >|
|**_wgetcwd**|\<Direct.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %d\n", buffer, strnlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>Viz také

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
