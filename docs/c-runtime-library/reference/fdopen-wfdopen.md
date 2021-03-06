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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 227f9e31c689b0259c429e2ffd9fce074903bd71
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920180"
---
# <a name="_fdopen-_wfdopen"></a>_fdopen, _wfdopen

Přidruží datový proud k souboru, který byl dříve otevřen pro vstupně-výstupní operace nízké úrovně.

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

*FD*<br/>
Popisovač souboru otevřeného souboru

*Mode*<br/>
Typ přístupu k souboru

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na otevřený datový proud. Hodnota nulového ukazatele označuje chybu. Pokud dojde k chybě, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven buď na **EBADF**, což indikuje špatný popisovač souboru, nebo **EINVAL**, což označuje, že *režim* byl ukazatel s hodnotou null.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_fdopen** přidružuje vstupně-výstupní proud se souborem, který je identifikován pomocí *FD*, a umožňuje tak otevření souboru, který je otevřen pro vstupně-výstupní operace nízké úrovně do vyrovnávací paměti a formátování. **_wfdopen** je verze **_fdopen**s velkým znakem; Argument *Mode* pro **_wfdopen** je řetězec s velkým znakem. **_wfdopen** a **_fdopen** se v opačném případě chová stejně.

Popisovače souborů předané do **_fdopen** jsou vlastněny vráceným datovým proudem **&#42;** . Pokud je **_fdopen** úspěšné, Nevolejte [ \_](close.md) v popisovači souboru Close. V vráceném souboru se zavolá [fclose](fclose-fcloseall.md) **&#42;** také zavře popisovač souboru.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|\_Kódování UNICODE \_a MBCS není definováno.|\_Definice znakové sady MBCS|\_Definováno kódováním UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

Řetězec znaků *režimu* určuje typ přístupu k souboru vyžádaného pro tento soubor:

| *Mode* | Access |
|--------|--------|
| **í** | Otevře se pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, volání **fopen** se nezdařilo. |
| **w** | Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah je zničen. |
| **určitého** | Otevře se pro zápis na konci souboru (připojení). Vytvoří soubor, pokud neexistuje. |
| **"r +"** | Otevře se pro čtení i zápis. Soubor musí existovat. |
| **"w +"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah se zničí. |
| **"a +"** | Otevře se pro čtení a připojení. Vytvoří soubor, pokud neexistuje. |

Když se soubor otevře s typem přístupu **"a"** nebo **"a +"** , na konci souboru se objeví všechny operace zápisu. Ukazatel na soubor lze změnit pomocí [fseek](fseek-fseeki64.md) nebo [Rewind](rewind.md), ale je vždy přesunut zpět na konec souboru před provedením jakékoli operace zápisu. Existující data proto nelze přepsat. Je-li zadán typ přístupu **"r +"**, **"w +"** nebo **"a +"** , jsou povoleny čtení i zápis (soubor je označován jako otevřený pro "aktualizaci"). Pokud však přepínáte mezi čtením a zápisem, musí se jednat o [fflush](fflush.md), [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)nebo [Rewind](rewind.md) operaci. Pokud chcete, můžete zadat aktuální pozici pro operaci [fsetpos](fsetpos.md) nebo [fseek](fseek-fseeki64.md) .

Kromě výše uvedených hodnot lze do *režimu* zahrnout také následující znaky, které určují režim překladu znaků nového řádku:

| Modifikátor *režimu* | Chování |
|-----------------|----------|
| **š** | Otevřít v textovém (přeloženém) režimu. V tomto režimu jsou kombinace pro návrat vozíku z řádku (CR-LF) přeloženy na vstup na jeden řádek (LF) na vstupu a znaky LF jsou přeloženy na kombinace znaků CR-LF na výstupu. Také CTRL + Z je interpretována jako znak konce souboru na vstupu. |
| **b** | Otevřené v binárním (nepřeloženém) režimu. Všechny překlady z režimu **t** jsou potlačeny. |
| **r** | Povolte příznak potvrzení pro přidružený *název souboru* , aby se obsah vyrovnávací paměti souboru zapsal přímo na disk, pokud je zavolána buď **fflush** nebo **_flushall** . |
| **n** | Obnovte příznak potvrzení pro přidružený *název souboru* na "bez potvrzení". Toto nastavení je výchozí. Také přepisuje příznak globálního potvrzení, Pokud propojíte program s Commode. obj. Pokud explicitně nepřipojíte program k Commode. obj, výchozí příznak autocommit je nastaven na možnost bez potvrzení. |

Možnosti *režimu* **t**, **c**a **n** jsou rozšířeními Microsoftu pro **fopen** a **_fdopen**. Nepoužívejte je, pokud chcete zachovat přenositelnost ANSI.

Pokud **t** nebo **b** není uveden v *režimu*, výchozí režim překladu je definován globální proměnnou [ \_fMode](../../c-runtime-library/fmode.md). Pokud je **t** nebo **b** předpona argumentu, funkce se nezdařila a vrátí hodnotu null. Diskuzi o textu a binárních režimech najdete v tématu [vstupně-výstupní operace se soubory textového a binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Platné znaky pro řetězec *režimu* použité v **fopen** a **_fdopen** odpovídají argumentům *oflag* použitým v [ \_otevřených](open-wopen.md) a [ \_sopen](sopen-wsopen.md), jak je znázorněno v této tabulce:

|Znaky v řetězci *režimu*|Ekvivalentní hodnota *oflag* pro **_open** a **_sopen**|
|---------------------------------|---------------------------------------------------|
|**určitého**|**\_O\_WRONLY &#124; \_o\_připojení** (obvykle ** \_o\_WRONLY &#124; \_o\_vytvoření &#124; \_o\_připojení**)|
|**a +**|**\_O\_RDWR &#124; \_o\_připojení** (obvykle ** \_o\_RDWR &#124; \_o\_připojení &#124; \_o\_** vytvořit)|
|**í**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (obvykle ** \_o\_WRONLY &#124; \_o\_vytvoření &#124; \_o\_TRUNC –**)|
|**w +**|**\_O\_RDWR** (obvykle ** \_o\_RDWR &#124; \_o\_vytvoření &#124; \_o\_TRUNC –**)|
|**b**|**\_O\_binárním souboru**|
|**š**|**\_O\_-text**|
|**r**|Žádné|
|**n**|Žádné|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fdopen**|\<stdio. h>|
|**_wfdopen**|\<stdio. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

### <a name="input-crt_fdopentxt"></a>Vstup: crt_fdopen. txt

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
[\_DUP, \_dUP2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_otevřít, \_wopen](open-wopen.md)<br/>
