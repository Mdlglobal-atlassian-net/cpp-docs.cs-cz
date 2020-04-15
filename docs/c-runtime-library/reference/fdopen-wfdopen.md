---
title: _fdopen, _wfdopen
ms.date: 4/2/2020
api_name:
- _fdopen
- _wfdopen
- _o__fdopen
- _o__wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
ms.openlocfilehash: 82a7e891e8bd6031ebbf761534b6df7cd8488d36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347390"
---
# <a name="_fdopen-_wfdopen"></a>_fdopen, _wfdopen

Přidruží datový proud k souboru, který byl dříve otevřen pro vstupně-videa nižší úrovně.

## <a name="syntax"></a>Syntaxe

```C
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Popisovač souboru otevřeného souboru.

*Režimu*<br/>
Typ přístupu k souborům.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí ukazatel na otevřený datový proud. Hodnota ukazatele null označuje chybu. Dojde-li k chybě, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **errno** je nastavena buď **na EBADF**, což znamená chybný popisovač souboru nebo **EINVAL**, což znamená, že *režim* byl nulový ukazatel.

Další informace o těchto a dalších kódech chyb naleznete [v tématu _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_fdopen** přidruží vstupně-v.O datový proud se souborem, který je identifikován *fd*, a umožňuje soubor, který je otevřen pro nízké úrovně V/O, které mají být uloženy do vyrovnávací paměti a formátovány. **_wfdopen** je širokoznaková verze **_fdopen**; argument *mode,* který má **_wfdopen,** je řetězec s širokým znakem. **_wfdopen** a **_fdopen** jinak chovají stejně.

Popisovače souborů předané do **_fdopen** jsou vlastněny vráceným **datovým proudem &#42;souboru.** Pokud **_fdopen** úspěšné, nevolejte [ \_zavřít](close.md) popisovač souboru. Volání [fclose](fclose-fcloseall.md) na vrácené **souboru &#42;** také zavře popisovač souboru.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|\_UNICODE \_a MBCS nejsou definovány|\_MBCS definice|\_UNICODE, definice|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

Řetězec znaků *režimu* určuje typ přístupu k souboru požadovaný pro soubor:

| *Režimu* | Access |
|--------|--------|
| **"r"** | Otevírá se pro čtení. Pokud soubor neexistuje nebo jej nelze najít, volání **fopen** se nezdaří. |
| **"w"** | Otevře prázdný soubor pro psaní. Pokud daný soubor existuje, jeho obsah je zničen. |
| **"a"** | Otevře se pro zápis na konci souboru (připojení). Vytvoří soubor, pokud neexistuje. |
| **"r+"** | Otevírá se pro čtení i psaní. Soubor musí existovat. |
| **"w+"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah je zničen. |
| **"a+"** | Otevírá se pro čtení a připojení. Vytvoří soubor, pokud neexistuje. |

Při otevření souboru s typem přístupu **"a"** nebo **"a+",** všechny operace zápisu dojít na konci souboru. Ukazatel souboru lze přemístit pomocí [fseek](fseek-fseeki64.md) nebo [převinout zpět](rewind.md), ale je vždy přesunuta zpět na konec souboru před provedením jakékoli operace zápisu. Existující data tedy nelze přepsat. Pokud je zadán typ přístupu **"r+"**, **"w+"** nebo **"a+",** je povoleno čtení i zápis (soubor je údajně otevřený pro "aktualizovat"). Však při přepínání mezi čtení min. a zápisem, musí být zasahující [fflush](fflush.md), [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md), nebo [převíjení vzad](rewind.md) operace. Můžete určit aktuální pozici pro [fsetpos](fsetpos.md) nebo [fseek](fseek-fseeki64.md) operace, pokud chcete.

Kromě výše uvedených hodnot mohou být v *režimu* zahrnuty také následující znaky pro určení režimu překladu znaků nového řádku:

| *modifikátor režimu* | Chování |
|-----------------|----------|
| **t** | Otevřít v textovém (přeloženém) režimu. V tomto režimu jsou kombinace zpětného kanálu vozíku (CR-LF) přeloženy do jednořádkových kanálů (LF) na vstupu a lf znaky jsou přeloženy do kombinací CR-LF na výstupu. Ctrl+Z je také interpretován jako znak konce souboru na vstupu. |
| **B** | Otevřít v binárním (nepřeloženém) režimu. Všechny překlady z režimu **t** jsou potlačeny. |
| **C** | Povolte příznak potvrzení pro přidružený *název souboru,* aby byl obsah vyrovnávací paměti souboru zapsán přímo na disk, pokud je volána **fflush** nebo **_flushall.** |
| **N** | Obnovte příznak potvrzení pro přidružený *název souboru* na "no-commit". Toto nastavení je výchozí. Také přepíše příznak globální potvrzení, pokud propojíte program s Commode.obj. Výchozí hodnota příznaku globálního potvrzení je "no-commit", pokud explicitně nepropojíte program s commode.obj. |

Možnosti *režimu* **t**, **c**a **n** jsou rozšíření společnosti Microsoft pro **fopen** a **_fdopen**. Nepoužívejte je, pokud chcete zachovat přenositelnost ANSI.

Pokud **t** nebo **b** není uveden v *režimu*, výchozí režim překladu je definován globální proměnnou [ \_fmode](../../c-runtime-library/fmode.md). Pokud **t** nebo **b** je předponou argument, funkce se nezdaří a vrátí NULL. Diskuse o texta a binární režimy naleznete [v tématu Text a binární režim soubor V/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Platné znaky pro řetězec *režimu* použitý v **fopen** a **_fdopen** odpovídají argumentům *oflag* použitým v [ \_otevřeném](open-wopen.md) a [ \_sopen](sopen-wsopen.md), jak je znázorněno v této tabulce:

|Znaky v *řetězci režimu*|Ekvivalentní hodnota *opříznaku* pro **_open** a **_sopen**|
|---------------------------------|---------------------------------------------------|
|**A**|**\_O\_WRONLY \_\_&#124; O APPEND** (obvykle ** \_\_O WRONLY \_&#124; O\_CREAT \_&#124; O\_APPEND)**|
|**a+**|**\_O\_RDWR \_\_&#124; O APPEND** (obvykle ** \_\_O RDWR \_&#124; O\_APPEND \_&#124; O\_CREAT)**|
|**R**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**W**|**\_O\_WRONLY** (obvykle ** \_\_O \_\_WRONLY \_&#124;\_O CREAT &#124; O TRUNC)**|
|**w+**|**\_O\_RDWR** (obvykle ** \_\_O \_\_RDWR \_&#124;\_O CREAT &#124; O TRUNC)**|
|**B**|**\_O\_BINÁRNÍ**|
|**t**|**\_O\_TEXT**|
|**C**|Žádný|
|**N**|Žádný|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crt_fdopentxt"></a>Vstup: crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>Výstup

```Output
Lines in file: 2
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup, \_dup2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_otevřít, \_wopen](open-wopen.md)<br/>
