---
title: _umask_s
ms.date: 4/2/2020
api_name:
- _umask_s
- _o__umask_s
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
- unmask_s
- _umask_s
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
ms.openlocfilehash: d590910d5f5092a78ad64c8f9ef0aa259211e226
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362181"
---
# <a name="_umask_s"></a>_umask_s

Nastaví výchozí masku oprávnění k souboru. Verze [_umask](umask.md) s vylepšeními zabezpečení, jak je popsáno v [části Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>Parametry

*Režimu*<br/>
Výchozí nastavení oprávnění.

*pOldMode*<br/>
Předchozí hodnota nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

Vrátí kód chyby, pokud *režim* neurčuje platný režim nebo ukazatel *pOldMode* je **NULL**.

### <a name="error-conditions"></a>Chybové stavy

|*Režimu*|*pOldMode*|Návratová hodnota|Obsah *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|jakékoli|**Null**|**EINVAL**|nezměněno|
|neplatný režim|jakékoli|**EINVAL**|nezměněno|

Pokud dojde k jedné z výše uvedených podmínek, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **vrátí _umask_s** **funkce EINVAL** a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_umask_s** nastaví masku oprávnění k souboru aktuálního procesu do režimu určeného *režimem*. Maska oprávnění k souboru upravuje nastavení oprávnění nových souborů vytvořených **_creat**, **_open**nebo **_sopen**. Pokud je bit v masce 1, odpovídající bit v požadované hodnotě oprávnění souboru je nastaven na 0 (zakázáno). Pokud bit v masce je 0, odpovídající bit zůstane beze změny. Nastavení oprávnění pro nový soubor není nastaveno, dokud není soubor poprvé uzavřen.

Integer výraz *pmode* obsahuje jednu nebo obě následující konstanty manifestu definované v SYS\STAT. H:

|*pmode*||
|-|-|
|**_S_IWRITE**|Psaní povoleno.|
|**_S_IREAD**|Čtení povoleno.|
|**_S_IREAD** \| **_S_IWRITE**|Čtení a psaní povoleno.|

Pokud jsou uvedeny obě konstanty, jsou spojeny **|** s bitovým operátorem OR ( ). Pokud je argument *režimu* **_S_IREAD**, čtení není povoleno (soubor je pouze pro zápis). Pokud je argument *režimu* **_S_IWRITE**, zápis není povolen (soubor je jen pro čtení). Pokud je například v masce nastaven zapisovací bit, budou všechny nové soubory jen pro čtení. Všimněte si, že s MS-DOS a operační systémy Windows, všechny soubory jsou čitelné; není možné udělit oprávnění pouze pro zápis. Proto nastavení čtecí bit s **_umask_s** nemá žádný vliv na režimy souboru.

Pokud *pmode* není kombinací jedné z konstant manifestu nebo obsahuje alternativní sadu konstant, funkce je jednoduše ignoruje.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_umask_s**|\<io.h> \<a sys/stat.h> a \<sys/types.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_umask_s.c
/* This program uses _umask_s to set
* the file-permission mask so that all future
* files will be created as read-only files.
* It also displays the old mask.
*/

#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask, err;

   /* Create read-only files: */
   err = _umask_s( _S_IWRITE, &oldmask );
   if (err)
   {
      printf("Error setting the umask.\n");
      exit(1);
   }
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
[_umask](umask.md)<br/>
