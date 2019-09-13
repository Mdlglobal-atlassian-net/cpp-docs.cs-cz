---
title: _creat, _wcreat
ms.date: 11/04/2016
api_name:
- _creat
- _wcreat
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
ms.openlocfilehash: d278bffbfdf856956a20b01da4dad2ba00952359
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938896"
---
# <a name="_creat-_wcreat"></a>_creat, _wcreat

Vytvoří nový soubor. **_creat** a **_wcreat** se už nepoužívají. místo toho použijte [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md) .

## <a name="syntax"></a>Syntaxe

```C
int _creat(
   const char *filename,
   int pmode
);
int _wcreat(
   const wchar_t *filename,
   int pmode
);
```

### <a name="parameters"></a>Parametry

*Bitmap*<br/>
Název nového souboru

*pmode*<br/>
Nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce, pokud jsou úspěšné, vrátí popisovač souboru do vytvořeného souboru. V opačném případě vrátí funkce hodnotu-1 a nastaví **errno** , jak je znázorněno v následující tabulce.

|nastavení **errno**|Popis|
|---------------------|-----------------|
|**EACCES**|*filename* určuje existující soubor, který je jen pro čtení, nebo místo souboru určí adresář.|
|**EMFILE**|Nejsou k dispozici žádné další popisovače souboru.|
|**ENOENT**|Zadaný soubor nebyl nalezen.|

Pokud má *název souboru* **hodnotu null**, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí-1.

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_creat** vytvoří nový soubor nebo otevře a zkrátí stávající. **_wcreat** je **_creat**verze s velkým znakem; Argument *filename* pro **_wcreat** je řetězec s velkým znakem. **_wcreat** a **_creat** se chovají stejně jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Pokud soubor určený parametrem *filename* neexistuje, vytvoří se nový soubor s daným nastavením oprávnění a otevře se pro zápis. Pokud soubor již existuje a jeho nastavení oprávnění povoluje zápis, **_creat** zkrátí soubor na délku 0, zničí předchozí obsah a otevře jej pro zápis. Nastavení oprávnění *pmode*se vztahuje pouze na nově vytvořené soubory. Po prvním zavření nového souboru obdrží zadané nastavení oprávnění. Celočíselný výraz *pmode* obsahuje jednu nebo obě konstanty manifestu **_S_IWRITE** a **_S_IREAD**definované v SYS\Stat.h. Jsou-li obě konstanty zadány, jsou spojeny s bitovým **&#124;** operátorem OR (). Parametr *pmode* je nastaven na jednu z následujících hodnot.

|Value|Definice|
|-----------|----------------|
|**_S_IWRITE**|Zápis povolen.|
|**_S_IREAD**|Čtení je povoleno.|
|**_S_IREAD** &#124; **_S_IWRITE**|Čtení a zápis jsou povoleny.|

Pokud není uděleno oprávnění k zápisu, je soubor určen jen pro čtení. Všechny soubory jsou vždy čitelné; není možné poskytovat oprávnění pouze pro zápis. Režimy **_S_IWRITE** a **_S_IREAD** |  **_S_IWRITE** jsou pak ekvivalentní. Soubory otevřené pomocí **_creat** se vždy otevřou v režimu kompatibility (viz [_Sopen](sopen-wsopen.md)) s **_SH_DENYNO**.

**_creat** aplikuje aktuální masku oprávnění souboru na *pmode* před nastavením oprávnění (viz [_umask](umask.md)). **_creat** je primárně k dispozici pro kompatibilitu s předchozími knihovnami. Volání **_open** s **_O_CREAT** a **_O_TRUNC** v parametru *oflag* je ekvivalentní **_creat** a je vhodnější pro nový kód.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/Types. h > \<, sys/stat. h > \<, errno. h >|
|**_wcreat**|\<IO. h > nebo \<WCHAR. h >|\<sys/Types. h > \<, sys/stat. h > \<, errno. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_creat.c
// compile with: /W3
// This program uses _creat to create
// the file (or truncate the existing file)
// named data and open it for writing.

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int fh;

   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996
   // Note: _creat is deprecated; use _sopen_s instead
   if( fh == -1 )
      perror( "Couldn't create data file" );
   else
   {
      printf( "Created data file.\n" );
      _close( fh );
   }
}
```

```Output
Created data file.
```

## <a name="see-also"></a>Viz také:

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
