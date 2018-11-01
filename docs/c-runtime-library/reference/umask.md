---
title: _umask
ms.date: 11/04/2016
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
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
ms.openlocfilehash: f51e2c19933953eb4910cdeb5e1ec50b7387bd59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677159"
---
# <a name="umask"></a>_umask

Nastaví výchozí masku souboru oprávnění. Bezpečnější verze této funkce je k dispozici. Zobrazit [_umask_s –](umask-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Výchozí nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

**_umask –** vrátí předchozí hodnotu *pmode*. Není vrácena žádná chyba.

## <a name="remarks"></a>Poznámky

**_Umask –** funkce nastaví masky souboru oprávnění aktuálního procesu k režimu určeném *pmode*. Maska oprávnění soubor upravuje nastavení oprávnění nové soubory vytvořené v **_creat –**, **_Otevřít**, nebo **_sopen**. Pokud bit masky je 1, odpovídající bit v souboru hodnota požadovaná oprávnění nastavená na hodnotu 0 (zakázáno). Pokud bit masky na hodnotu 0, odpovídající bit zůstane beze změny. Nastavení oprávnění pro nový soubor není nastavena, dokud není zavřena soubor poprvé.

Celočíselný výraz *pmode* obsahuje jednu nebo obě z následujících konstant manifestu definovaných v SYS\STAT. V:

|*pmode*||
|-|-|
**_S_IWRITE**|Zápis povolen.
**_S_IREAD**|Čtení povolené.
**_S_IREAD** \| **_S_IWRITE**|Čtení a zápis povolen.

Když jsou uvedeny oba konstanty, jsou spojeny pomocí bitového operátoru OR – operátor ( **|** ). Pokud *pmode* argument je **_S_IREAD**, není povoleno čtení (soubor je jen pro zápis). Pokud *pmode* argument je **_S_IWRITE**, není povolen zápis (soubor je jen pro čtení). Pokud je bit zápisu nastavený v masce, všechny nové soubory bude třeba jen pro čtení. Upozorňujeme, že zástupného kódu MS-DOS a operační systémy Windows, je čitelný; všechny soubory není možné poskytnout oprávnění jen pro zápis. Proto nastavení čtení bit s **_umask –** nemá žádný vliv na jeho režimy.

Pokud *pmode* není kombinaci některou z konstant manifestu nebo zahrnuje alternativní sadu konstant, funkce bude jednoduše ignorovat ty.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_umask**|\<IO.h >, \<sys/stat.h >, \<sys/types.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
