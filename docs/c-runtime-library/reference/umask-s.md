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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 712313314c67d15987326e3e3a920cd5f1039239
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913881"
---
# <a name="_umask_s"></a>_umask_s

Nastaví výchozí masku oprávnění souboru. Verze [_umask](umask.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>Parametry

*Mode*<br/>
Výchozí nastavení oprávnění

*pOldMode*<br/>
Předchozí hodnota nastavení oprávnění

## <a name="return-value"></a>Návratová hodnota

Vrátí kód chyby, pokud *režim* neurčuje platný režim nebo ukazatel *POldMode* má **hodnotu null**.

### <a name="error-conditions"></a>Chybové stavy

|*Mode*|*pOldMode*|Návratová hodnota|Obsah *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|jakýmikoli|**PLATNOST**|**EINVAL**|Neupraveno|
|Neplatný režim|jakýmikoli|**EINVAL**|Neupraveno|

Pokud nastane jedna z výše uvedených podmínek, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **_umask_s** vrátí **EINVAL** a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_umask_s** nastaví masku oprávnění souboru pro aktuální proces do režimu určeného parametrem *Mode*. Maska oprávnění k souborům upravuje nastavení oprávnění nových souborů vytvořených **_creat**, **_open**nebo **_sopen**. Pokud je bit v masce 1, odpovídající bit v hodnotě požadovaného oprávnění souboru je nastaven na hodnotu 0 (zakázáno). Pokud je bit v masce 0, odpovídající bit zůstane beze změny. Nastavení oprávnění pro nový soubor není nastavené, dokud se soubor nezavřá poprvé.

Celočíselný výraz *pmode* obsahuje jednu nebo obě následující konstanty manifestu definované v SYS\STAT.. Y

|*pmode*||
|-|-|
|**_S_IWRITE**|Zápis povolen.|
|**_S_IREAD**|Čtení je povoleno.|
|**_S_IREAD** \| **_S_IWRITE**|Čtení a zápis jsou povoleny.|

Jsou-li obě konstanty zadány, jsou spojeny s bitovým operátorem OR ( **|** ). Pokud je argument *režimu* **_S_IREAD**, čtení není povoleno (soubor je jen pro zápis). Pokud je argument *režimu* **_S_IWRITE**, zápis není povolen (soubor je jen pro čtení). Například pokud je bit zápisu nastaven v masce, všechny nové soubory budou jen pro čtení. Všimněte si, že v operačních systémech MS-DOS a Windows jsou všechny soubory čitelné. není možné poskytovat oprávnění pouze pro zápis. Proto nastavení bitu pro čtení pomocí **_umask_s** nemá žádný vliv na režimy souboru.

Pokud *pmode* není kombinací jedné z celočíselných konstant nebo zahrnuje alternativní sadu konstant, funkce je jednoduše ignoruje.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_umask_s**|\<IO. h> a \<sys/stat. h> a \<sys/types. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
