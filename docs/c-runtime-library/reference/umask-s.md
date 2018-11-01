---
title: _umask_s
ms.date: 11/04/2016
apiname:
- _umask_s
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
ms.openlocfilehash: 878a22cb2884c36e792ff8dead1453582addb5b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480664"
---
# <a name="umasks"></a>_umask_s

Nastaví výchozí masku souboru oprávnění. Verze [_umask –](umask.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>Parametry

*Režim*<br/>
Výchozí nastavení oprávnění.

*pOldMode*<br/>
Předchozí hodnota nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

Vrátí kód chyby, pokud *režimu* neurčuje platný režim nebo *pOldMode* ukazatel **NULL**.

### <a name="error-conditions"></a>Chybové podmínky

|*Režim*|*pOldMode*|Návratová hodnota|Obsah *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|Všechny|**HODNOTU NULL**|**EINVAL**|Nezměněno|
|Neplatný režim|Všechny|**EINVAL**|Nezměněno|

Pokud dojde k jedné z výše uvedených podmínek, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **_umask_s –** vrátí **EINVAL** a nastaví **errno** k **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Umask_s –** funkce nastaví masky souboru oprávnění aktuálního procesu k režimu určeném *režimu*. Maska oprávnění soubor upravuje nastavení oprávnění nové soubory vytvořené v **_creat –**, **_Otevřít**, nebo **_sopen**. Pokud bit masky je 1, odpovídající bit v souboru hodnota požadovaná oprávnění nastavená na hodnotu 0 (zakázáno). Pokud bit masky na hodnotu 0, odpovídající bit zůstane beze změny. Nastavení oprávnění pro nový soubor není nastavena, dokud není zavřena soubor poprvé.

Celočíselný výraz *pmode* obsahuje jednu nebo obě z následujících konstant manifestu definovaných v SYS\STAT. V:

|*pmode*||
|-|-|
|**_S_IWRITE**|Zápis povolen.|
|**_S_IREAD**|Čtení povolené.|
|**_S_IREAD** \| **_S_IWRITE**|Čtení a zápis povolen.|

Když jsou uvedeny oba konstanty, jsou spojeny pomocí bitového operátoru OR – operátor ( **|** ). Pokud *režimu* argument je **_S_IREAD**, není povoleno čtení (soubor je jen pro zápis). Pokud *režimu* argument je **_S_IWRITE**, není povolen zápis (soubor je jen pro čtení). Pokud je bit zápisu nastavený v masce, všechny nové soubory bude třeba jen pro čtení. Upozorňujeme, že zástupného kódu MS-DOS a operační systémy Windows, je čitelný; všechny soubory není možné poskytnout oprávnění jen pro zápis. Proto nastavení čtení bit s **_umask_s –** nemá žádný vliv na jeho režimy.

Pokud *pmode* není kombinaci některou z konstant manifestu nebo zahrnuje alternativní sadu konstant, funkce bude jednoduše ignorovat ty.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_umask_s**|\<IO.h > a \<sys/stat.h > a \<sys/types.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
