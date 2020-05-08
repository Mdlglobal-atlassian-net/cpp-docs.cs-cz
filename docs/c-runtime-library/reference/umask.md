---
title: _umask
ms.date: 4/2/2020
api_name:
- _umask
- _o__umask
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
- _umask
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
ms.openlocfilehash: 84735374a936e47691df82247f0202ecfcd86d9d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913848"
---
# <a name="_umask"></a>_umask

Nastaví výchozí masku oprávnění souboru. K dispozici je bezpečnější verze této funkce; viz [_umask_s](umask-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Výchozí nastavení oprávnění

## <a name="return-value"></a>Návratová hodnota

**_umask** vrátí předchozí hodnotu *pmode*. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Funkce **_umask** nastaví masku oprávnění souboru pro aktuální proces do režimu určeného parametrem *pmode*. Maska oprávnění k souborům upravuje nastavení oprávnění nových souborů vytvořených **_creat**, **_open**nebo **_sopen**. Pokud je bit v masce 1, odpovídající bit v hodnotě požadovaného oprávnění souboru je nastaven na hodnotu 0 (zakázáno). Pokud je bit v masce 0, odpovídající bit zůstane beze změny. Nastavení oprávnění pro nový soubor není nastavené, dokud se soubor nezavřá poprvé.

Celočíselný výraz *pmode* obsahuje jednu nebo obě následující konstanty manifestu definované v SYS\STAT.. Y

|*pmode*| |
|-|-|
| **_S_IWRITE** | Zápis povolen. |
| **_S_IREAD** | Čtení je povoleno. |
| **_S_IREAD** &#124; **_S_IWRITE** | Čtení a zápis jsou povoleny. |

Jsou-li obě konstanty zadány, jsou spojeny s bitovým operátorem OR ( **&#124;** ). Pokud je **_S_IREAD**argument *pmode* , čtení není povoleno (soubor je jen pro zápis). Pokud je **_S_IWRITE**argument *pmode* , zápis není povolen (soubor je jen pro čtení). Například pokud je bit zápisu nastaven v masce, všechny nové soubory budou jen pro čtení. Všimněte si, že v operačních systémech MS-DOS a Windows jsou všechny soubory čitelné. není možné poskytovat oprávnění pouze pro zápis. Proto nastavení bitu pro čtení pomocí **_umask** nemá žádný vliv na režimy souboru.

Pokud *pmode* není kombinací jedné z celočíselných konstant nebo zahrnuje alternativní sadu konstant, funkce je jednoduše ignoruje.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_umask**|\<IO. h>, \<sys/stat. h>, \<sys/types. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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
