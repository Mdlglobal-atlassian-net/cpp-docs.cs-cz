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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b451f979f2925a31f5baaac52351c5d2c0a76da0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362025"
---
# <a name="_umask"></a>_umask

Nastaví výchozí masku oprávnění k souboru. K dispozici je bezpečnější verze této funkce. viz [_umask_s](umask-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Výchozí nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

**_umask** vrátí předchozí hodnotu *pmode*. Neexistuje žádná chyba vrátit.

## <a name="remarks"></a>Poznámky

Funkce **_umask** nastaví masku oprávnění k souboru aktuálního procesu do režimu určeného *režimem pmode*. Maska oprávnění k souboru upravuje nastavení oprávnění nových souborů vytvořených **_creat**, **_open**nebo **_sopen**. Pokud je bit v masce 1, odpovídající bit v požadované hodnotě oprávnění souboru je nastaven na 0 (zakázáno). Pokud bit v masce je 0, odpovídající bit zůstane beze změny. Nastavení oprávnění pro nový soubor není nastaveno, dokud není soubor poprvé uzavřen.

Integer výraz *pmode* obsahuje jednu nebo obě následující konstanty manifestu definované v SYS\STAT. H:

|*pmode*| |
|-|-|
| **_S_IWRITE** | Psaní povoleno. |
| **_S_IREAD** | Čtení povoleno. |
| **_S_IREAD** **&#124; _S_IWRITE** | Čtení a psaní povoleno. |

Pokud jsou obě konstanty uvedeny, jsou spojeny s bitovým operátorem OR ( **&#124;** ). Pokud je argument *pmode* **_S_IREAD**, čtení není povoleno (soubor je pouze pro zápis). Pokud je argument *pmode* **_S_IWRITE**, zápis není povolen (soubor je jen pro čtení). Pokud je například v masce nastaven zapisovací bit, budou všechny nové soubory jen pro čtení. Všimněte si, že s MS-DOS a operační systémy Windows, všechny soubory jsou čitelné; není možné udělit oprávnění pouze pro zápis. Proto nastavení čtecí bit s **_umask** nemá žádný vliv na režimy souboru.

Pokud *pmode* není kombinací jedné z konstant manifestu nebo obsahuje alternativní sadu konstant, funkce je jednoduše ignoruje.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h \<>, sys/types.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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
[Vstupně-nosné(v" nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
