---
title: _umask – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _umask
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
- _umask
dev_langs:
- C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce3053bfb19cc81dff15d41d1b5bc6d405da619f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="umask"></a>_umask

Nastaví výchozí oprávnění souboru masku. Bezpečnější verze této funkce je k dispozici. v tématu [_umask_s –](umask-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Výchozí nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

**_umask –** vrátí předchozí hodnotu *pmode*. Neexistuje žádný návratový chyby.

## <a name="remarks"></a>Poznámky

**_Umask –** funkce nastaví oprávnění souborů maska aktuální proces do režimu určeného *pmode*. Oprávnění souborů maska upraví nastavení oprávnění nových souborů vytvořených **_creat –**, **_Otevřít**, nebo **_sopen –**. Pokud bit do masky je 1, příslušné bity v hodnotě souboru požadované oprávnění nastavená na hodnotu 0 (zakázáno). Pokud bit v maska je 0, odpovídající bit je ponechán beze změny. Nastavení oprávnění pro vytvoření nového souboru není nastavena, dokud soubor se zavřel poprvé.

Celočíselný výraz *pmode* obsahuje jedno nebo obě následující manifestu konstanty definované v SYS\STAT. V:

|*pmode*||
|-|-|
**_S_IWRITE –**|Zápis povolen.
**_S_IREAD –**|Čtení povolené.
**_S_IREAD –** \| **_S_IWRITE –**|Čtení a zápis povolen.

Pokud jsou zadány oba konstanty, jsou spojeny pomocí operátoru bitové operace OR ( **|** ). Pokud *pmode* argument je **_s_iread –**, čtení není povolen (soubor je jen pro zápis). Pokud *pmode* argument je **_s_iwrite –**, není povolen zápis (soubor je jen pro čtení). Pokud je bit zápisu nastavený v masce, všechny nové soubory bude třeba jen pro čtení. Upozorňujeme, že MS-DOS a operační systémy Windows, jsou všechny soubory čitelný; není možné udělit oprávnění jen pro zápis. Proto nastavení čtení bit s **_umask –** nemá žádný vliv na režimy v souboru.

Pokud *pmode* není kombinace jednoho z manifestu konstanty nebo zahrnuje alternativní sady konstant, funkce bude ignorovat ty.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_umask**|\<IO.h >, \<sys/stat.h >, \<sys/types.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_umask.c
// compile with: /W3
// This program uses _umask to set
// the file-permission mask so that all future
// files will be created as read-only files.
// It also displays the old mask.
#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask;

   /* Create read-only files: */
   oldmask = _umask( _S_IWRITE ); // C4996
   // Note: _umask is deprecated; consider using _umask_s instead
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
