---
title: _creat, _wcreat
ms.date: 11/04/2016
apiname:
- _creat
- _wcreat
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 901a95a6a9361f95f38749dacf1a5001d97b3761
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494988"
---
# <a name="creat-wcreat"></a>_creat, _wcreat

Vytvoří nový soubor. **_creat –** a **_wcreat –** jsou zastaralé; použijte [_sopen_s – _wsopen_s –](sopen-s-wsopen-s.md) místo.

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

*Název souboru*<br/>
Název nového souboru.

*pmode*<br/>
Nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce v případě úspěchu vrátí popisovač souboru do vytvořeného souboru. V opačném případě vrátí funkce hodnotu -1 a nastaví **errno** jak je znázorněno v následující tabulce.

|**errno** nastavení|Popis|
|---------------------|-----------------|
|**EACCES**|*Název souboru* určuje existující soubor jen pro čtení nebo určuje adresář, nikoli soubor.|
|**EMFILE**|Nejsou k dispozici žádné další popisovače souboru.|
|**ENOENT**|Zadaný soubor nebyl nalezen.|

Pokud *filename* je **NULL**, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Creat –** funkce vytvoří nový soubor nebo se otevře a zkrátí nějaký existující. **_wcreat –** je verze širokého znaku **_creat –**; *filename* argument **_wcreat –** je širokoznaký řetězec. **_wcreat –** a **_creat –** se jinak chovají stejně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat –**|**_creat**|**_creat**|**_wcreat**|

Pokud soubor určený *filename* buď neexistuje, vytvoří nový soubor se vytvoří pomocí nastavení dané oprávnění a je otevřen pro zápis. Pokud soubor už existuje a její nastavení oprávnění umožňuje zápis, **_creat –** zkrátí soubor, který má délku 0, zničení předchozí obsah a otevře jej pro zápis. Nastavení oprávnění *pmode*, platí pouze pro nově vytvořené soubory. Nový soubor obdrží nastavení zadané oprávnění po prvním propojení se zavře. Celočíselný výraz *pmode* obsahuje jeden nebo oba z konstant manifestu **_S_IWRITE** a **_S_IREAD**definované v SYS\Stat.h. Když jsou uvedeny oba konstanty, jsou spojeny s bitový operátor or ( **&#124;** ). *Pmode* parametr je nastaven na jednu z následujících hodnot.

|Hodnota|Definice|
|-----------|----------------|
|**_S_IWRITE**|Zápis povolen.|
|**_S_IREAD**|Čtení povolené.|
|**_S_IREAD** &AMP;#124; **_S_IWRITE**|Čtení a zápis povolen.|

Pokud tento parametr není zadaný oprávnění k zápisu, soubor je jen pro čtení. Všechny soubory jsou vždy čitelné; není možné poskytnout oprávnění jen pro zápis. Režimy **_S_IWRITE** a **_S_IREAD** | **_S_IWRITE** pak jsou ekvivalentní. Soubory otevřené pomocí **_creat –** jsou vždy otevřen v režimu kompatibility (viz [_sopen](sopen-wsopen.md)) s **_SH_DENYNO**.

**_creat –** použije aktuální masku souboru oprávnění k *pmode* před nastavením oprávnění (viz [_umask –](umask.md)). **_creat –** je k dispozici kvůli kompatibilitě s předchozím knihovny. Volání **_Otevřít** s **_O_CREAT** a **_O_TRUNC** v *oflag* parametr je ekvivalentní k **_creat –** a je vhodnější pro nový kód.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_creat**|\<IO.h >|\<SYS/Types.h >, \<sys/stat.h >, \<errno.h >|
|**_wcreat**|\<IO.h > nebo \<wchar.h >|\<SYS/Types.h >, \<sys/stat.h >, \<errno.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
