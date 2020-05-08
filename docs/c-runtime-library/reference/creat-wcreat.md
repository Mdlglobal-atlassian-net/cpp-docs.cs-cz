---
title: _creat, _wcreat
ms.date: 4/2/2020
api_name:
- _creat
- _wcreat
- _o__creat
- _o__wcreat
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 379a4adbf17755341fed6a48c649afe29e150fe5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912117"
---
# <a name="_creat-_wcreat"></a>_creat, _wcreat

Vytvoří nový soubor. **_creat** a **_wcreat** jsou zastaralé; místo toho použijte [_sopen_s _wsopen_s](sopen-s-wsopen-s.md) .

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

Funkce **_creat** vytvoří nový soubor nebo otevře a zkrátí existující soubor. **_wcreat** je verze **_creat**s velkým znakem; Argument *filename* pro **_wcreat** je řetězec s velkým znakem. **_wcreat** a **_creat** se chovají identicky jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Pokud soubor určený parametrem *filename* neexistuje, vytvoří se nový soubor s daným nastavením oprávnění a otevře se pro zápis. Pokud soubor již existuje a jeho oprávnění povoluje zápis, **_creat** zkrátí soubor na délku 0, zničí předchozí obsah a otevře jej pro zápis. Nastavení oprávnění *pmode*se vztahuje pouze na nově vytvořené soubory. Po prvním zavření nového souboru obdrží zadané nastavení oprávnění. Celočíselný výraz *pmode* obsahuje jednu nebo obě konstanty manifestu **_S_IWRITE** a **_S_IREAD**definované v SYS\Stat.h. Jsou-li obě konstanty zadány, jsou spojeny s bitovým operátorem OR ( **&#124;** ). Parametr *pmode* je nastaven na jednu z následujících hodnot.

|Hodnota|Definice|
|-----------|----------------|
|**_S_IWRITE**|Zápis povolen.|
|**_S_IREAD**|Čtení je povoleno.|
|**_S_IREAD** &#124; **_S_IWRITE**|Čtení a zápis jsou povoleny.|

Pokud není uděleno oprávnění k zápisu, je soubor určen jen pro čtení. Všechny soubory jsou vždy čitelné; není možné poskytovat oprávnění pouze pro zápis. Režimy **_S_IWRITE** a **_S_IREAD** | **_S_IWRITE** jsou pak ekvivalentní. Soubory otevřené pomocí **_creat** jsou vždy otevřeny v režimu kompatibility (viz [_sopen](sopen-wsopen.md)) s **_SH_DENYNO**.

**_creat** před nastavením oprávnění použít aktuální masku oprávnění k souboru *pmode* (viz [_umask](umask.md)). **_creat** je primárně k dispozici pro kompatibilitu s předchozími knihovnami. Volání **_open** s **_O_CREAT** a **_O_TRUNC** v parametru *oflag* je ekvivalentem **_creat** a je vhodnější pro nový kód.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_creat**|\<IO. h>|\<sys/Types. h> \<, sys/stat. h> \<, errno. h>|
|**_wcreat**|\<IO. h> nebo \<WCHAR. h>|\<sys/Types. h> \<, sys/stat. h> \<, errno. h>|

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

## <a name="see-also"></a>Viz také

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
