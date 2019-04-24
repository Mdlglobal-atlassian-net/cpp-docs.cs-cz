---
title: _fdopen, _wfdopen
ms.date: 12/12/2017
apiname:
- _fdopen
- _wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 0cde110bf1dd12c23a6b0b658809502743d9edd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334772"
---
# <a name="fdopen-wfdopen"></a>_fdopen, _wfdopen

Přidruží datového proudu souboru, který byl dříve otevřen pro vstupně-výstupních operací nízké úrovně.

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

*fd*<br/>
Popisovač souboru otevřený souboru.

*Režim*<br/>
Druh přístupu k souborům.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na Otevřít datový proud. Hodnota nulového ukazatele indikuje chybu. Pokud dojde k chybě, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastaven buď na **EBADF**, což naznačuje chybný soubor popisovač nebo **EINVAL**, což znamená, že *režimu*  byl ukazatel s hodnotou null.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Fdopen –** funkce přidruží proud vstupně-výstupní operace souboru, který je identifikován *fd*a tím umožňuje soubor, který je otevřen pro I/O nízké úrovně, které mají být ukládány do vyrovnávací paměti a ve formátu. **_wfdopen –** je verze širokého znaku **_fdopen –**; *režimu* argument **_wfdopen –** je širokoznaký řetězec. **_wfdopen –** a **_fdopen –** jinak chovají stejně.

Předaná do popisovače souboru **_fdopen –** patří ve vráceném **souboru &#42;**  datového proudu. Pokud **_fdopen –** proběhne úspěšně, nevolejte [ \_zavřete](close.md) na popisovač souboru. Volání [fclose –](fclose-fcloseall.md) na vrácený **souboru &#42;**  také uzavře popisovač souboru.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|\_Kódování UNICODE a \_znakové sady MBCS nedefinovaná.|\_Znakové sady MBCS definovaný|\_Definované kódování UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

*Režimu* řetězec znaků určuje typ souboru požadovaného přístupu k souboru:

| *Režim* | Access |
|--------|--------|
| **"r"** | Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, **fopen** volání selže. |
| **"w"** | Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah zničen. |
| **"a"** | Otevře se pro zápis na konci souboru (připojením). Vytvoří soubor, pokud neexistuje. |
| **"r +"** | Otevře pro čtení i zápis. Soubor musí existovat. |
| **"w +"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah zničen. |
| **"a +"** | Otevře pro čtení a připojení. Vytvoří soubor, pokud neexistuje. |

Při otevření souboru se **"a"** nebo **"a +"** získat přístup k typu, všechny zápisu operace dojít na konci souboru. Ukazatel na soubor lze přesunout pomocí [fseek](fseek-fseeki64.md) nebo [rewind](rewind.md), ale to je vždy přesunut na konec souboru před jakékoli zápisu operace provádí. Žádná existující data proto nemohou být přepsána. Když **"r +"**, **"w +"**, nebo **"a +"** je zadán přístupový typ, je povoleno čtení i zápis (Tento soubor říká, že je otevřen pro "úpravy"). Ale při přepínání mezi čtení a zápis, musí existovat podílející [fflush –](fflush.md), [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md), nebo [rewind](rewind.md) operace. Můžete určit aktuální pozici pro [fsetpos](fsetpos.md) nebo [fseek](fseek-fseeki64.md) operace, pokud chcete.

Kromě výše uvedených hodnot, tyto znaky můžou být i součástí *režimu* pro určení režimu překladu pro znaky nového řádku:

| *režim* modifikátor | Chování |
|-----------------|----------|
| **t** | Otevřít v textovém (přeloženém) režimu. V tomto režimu kombinace návrat na začátek řádku return-line kanál (CR-LF) jsou přeloženy do jedné odřádkování (LF) na vstupu a LF jsou přeloženy na výstupu jako kombinace CR-LF. Také Ctrl + Z je interpretován jako znak koncové souboru na vstupu. |
| **b** | Otevřít v binárním (nepřeloženém) režimu. Překlady z **t** režimu jsou potlačeny. |
| **c** | Povolte příznak pro zápis pro přidružený *filename* tak, aby se obsah vyrovnávací paměti souboru zapsán přímo na disk, pokud **fflush –** nebo **_flushall –** je volána. |
| **n** | Resetovat příznak pro zápis pro přidružený *filename* na "Neukládat." Toto nastavení je výchozí. Přepíše také globální, pokud propojení s Commode.obj. Výchozí globální příznak je "Neukládat", pokud výslovně nedojde k propojení s Commode.obj. |

**t**, **c**, a **n** *režimu* možnosti jsou rozšíření Microsoft pro **fopen** a **_fdopen –**. Nepoužívejte je, pokud chcete zachovat přenositelnost ANSI.

Pokud **t** nebo **b** není uveden v *režimu*, je výchozí režim překladu definován pomocí globální proměnné [ \_fmode –](../../c-runtime-library/fmode.md). Pokud **t** nebo **b** předponou argumentu, funkce selže a vrátí hodnotu NULL. Diskuzi o textovém a binárním režimu, najdete v článku [textového a binárního režimu souboru vstupně-výstupních operací](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Platné znaky pro *režimu* řetězec použitý v **fopen** a **_fdopen –** odpovídají *oflag* argumenty použité v [ \_otevřete](open-wopen.md) a [ \_sopen –](sopen-wsopen.md), jak je uvedeno v této tabulce:

|Znaky v *režimu* řetězec|Ekvivalentní *oflag* hodnota **_Otevřít** a **_sopen**|
|---------------------------------|---------------------------------------------------|
|**a**|**\_O\_WRONLY &#124; \_O\_APPEND** (obvykle  **\_O\_WRONLY &#124; \_O\_CREAT &#124; \_O \_Připojit**)|
|**a+**|**\_O\_RDWR &#124; \_O\_APPEND** (obvykle  **\_O\_RDWR &#124; \_O\_APPEND &#124; \_O\_ VYTVOŘENÍ** )|
|**r**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (obvykle  **\_O\_WRONLY &#124; \_O\_CREAT &#124; \_O\_TRUNC**)|
|**w+**|**\_O\_RDWR** (obvykle  **\_O\_RDWR &#124; \_O\_CREAT &#124; \_O\_TRUNC**)|
|**b**|**\_O\_BINÁRNÍ**|
|**t**|**\_O\_TEXT**|
|**c**|Žádné|
|**n**|Žádný|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

### <a name="input-crtfdopentxt"></a>Vstup: crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>Výstup

```Output
Lines in file: 2
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[\_DUP, \_dup2 –](dup-dup2.md)<br/>
[fclose –, \_fcloseall –](fclose-fcloseall.md)<br/>
[fopen, \_wfopen –](fopen-wfopen.md)<br/>
[freopen, \_wfreopen –](freopen-wfreopen.md)<br/>
[\_Otevřete, \_wopen –](open-wopen.md)<br/>
