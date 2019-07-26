---
title: fopen_s, _wfopen_s
ms.date: 11/04/2016
apiname:
- _wfopen_s
- fopen_s
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
- fopen_s
- _tfopen_s
- _wfopen_s
helpviewer_keywords:
- _wfopen_s function
- opening files, for file I/O
- _tfopen_s function
- tfopen_s function
- wfopen_s function
- fopen_s function
- Unicode [C++], creating files
- Unicode [C++], writing files
- files [C++], opening
- Unicode [C++], files
ms.assetid: c534857e-39ee-4a3f-bd26-dfe551ac96c3
ms.openlocfilehash: e4ccce3c4a4fe1e327b7830ef03f6ab69f2d7814
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376213"
---
# <a name="fopens-wfopens"></a>fopen_s, _wfopen_s

Otevře soubor. Tyto verze [fopen, _wfopen](fopen-wfopen.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t fopen_s(
   FILE** pFile,
   const char *filename,
   const char *mode
);
errno_t _wfopen_s(
   FILE** pFile,
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Ukazatel na ukazatel souboru, který dostane ukazatel na otevřený soubor.

*Bitmap*<br/>
Bitmap.

*Mode*<br/>
Typ povoleného přístupu.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; chybový kód při selhání. Další informace o těchto kódech chyb najdete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

### <a name="error-conditions"></a>Chybové stavy

|*pFile*|*Bitmap*|*Mode*|Návratová hodnota|Obsah *pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**NULL**|Jakýmikoli|Jakýmikoli|**EINVAL**|oproti|
|Jakýmikoli|**NULL**|Jakýmikoli|**EINVAL**|oproti|
|Jakýmikoli|Jakýmikoli|**NULL**|**EINVAL**|oproti|

## <a name="remarks"></a>Poznámky

Soubory, které jsou otevřeny pomocí **fopen_s** a **_wfopen_s** , nelze sdílet. Pokud požadujete, aby bylo možné soubor sdílet, použijte [_fsopen, _wfsopen](fsopen-wfsopen.md) s odpovídající konstantou režimu sdílení, například **_SH_DENYNO** pro sdílení pro čtení a zápis.

Funkce **fopen_s** otevře soubor určený parametrem *filename*. **_wfopen_s** je **fopen_s**verze s velkým znakem; argumenty **_wfopen_s** jsou řetězce s libovolným znakem. **_wfopen_s** a **fopen_s** se chovají stejně jinak.

**fopen_s** akceptuje cesty, které jsou platné v systému souborů v okamžiku provedení; Cesty UNC a cesty zahrnující mapované síťové jednotky jsou přijímány serverem **fopen_s** , pokud systém, který spouští kód, má přístup ke sdílené nebo mapované síťové jednotce v době spuštění. Při vytváření cest pro **fopen_s**neprovádějte předpoklady týkající se dostupnosti jednotek, cest nebo síťových sdílených složek ve spouštěcím prostředí. Jako oddělovače adresářů v cestě můžete použít buď lomítka (/),\\nebo zpětná lomítka ().

Tyto funkce ověřují své parametry. Pokud je *pFile*, *filename*nebo *Mode* ukazatel s hodnotou null, tyto funkce generují výjimku neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

Vždy zkontrolujte vrácenou hodnotu a ověřte, zda byla funkce úspěšná, než v souboru provedete další operace. Pokud dojde k chybě, vrátí se kód chyby a globální proměnná **errno** se nastaví. Další informace najdete v tématech [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="unicode-support"></a>Podpora kódování Unicode

**fopen_s** podporuje datové proudy souborů Unicode. Pokud chcete otevřít nový nebo existující soubor Unicode, předejte příznak *CCS* , který určuje požadované kódování pro **fopen_s**:

**fopen_s (& FP, "NewFile. txt"; "RW; CCS =** _Encoding_ **");**

Povolené hodnoty *kódování* jsou **Unicode**, **UTF-8**a **UTF-16LE**. Pokud není zadána žádná hodnota pro *kódování*, **FOPEN_S** použije kódování ANSI.

Pokud soubor již existuje a je otevřen pro čtení nebo připojení, značka pořadí bajtů (BOM), pokud je k dispozici v souboru, určuje kódování. Kódování kusovníku má přednost před kódováním, které je určeno příznakem *CCS* . Kódování *CCS* se používá pouze v případě, že není PŘÍTOMEN žádný kusovník, nebo pokud je soubor novým souborem.

> [!NOTE]
> Detekce kusovníku platí jenom pro soubory, které jsou otevřené v režimu Unicode. To znamená předáním příznaku *CCS* .

Následující tabulka shrnuje režimy různých příznaků *CCS* , které jsou předány **Fopen_s** a označení pořadí bajtů v souboru.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Kódování použitá na základě příznaku CCS a kusovníku

|příznak CCS|Žádný kusovník (nebo nový soubor)|BOM UTF-8|BOM UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**SADY**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Soubory, které jsou otevřeny pro zápis do režimu Unicode, mají automaticky zapsaného kusovníku.

Pokud  je režim **"a, CCS =** _Encoding_ **"** , **fopen_s** se nejprve pokusí otevřít soubor s přístupem pro čtení i zápis. V případě úspěchu funkce přečte BOM a určí kódování souboru. Pokud to neproběhne úspěšně, funkce použije výchozí kódování souboru. V obou případech **fopen_s** znovu otevře soubor s přístupem jen pro zápis. (To se vztahuje na **a** jen není režimu **a+** .)

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

*Režim* řetězce znaků Určuje typ přístupu, který je požadován pro soubor, následovně.

|*Mode*|Access|
|-|-|
| **í** | Otevře se pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, volání **fopen_s** se nezdařilo. |
| **"w"** | Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah je zničen. |
| **určitého** | Otevře se pro zápis na konci souboru (přidávání) bez odebrání označení konec souboru (EOF) před zápisem nových dat do souboru. Vytvoří soubor, pokud neexistuje. |
| **"r +"** | Otevře se pro čtení i zápis. Soubor musí existovat. |
| **"w +"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah se zničí. |
| **"a +"** | Otevře se pro čtení a připojení. Operace připojení zahrnuje odstranění značky EOF před zápisem nových dat do souboru. Po dokončení zápisu se značka EOF neobnoví. Vytvoří soubor, pokud neexistuje. |

Když se soubor otevře pomocí typu přístupu **"a"** nebo **"a +"** , na konci souboru se objeví všechny operace zápisu. Ukazatel na soubor lze změnit pomocí [fseek](fseek-fseeki64.md) nebo Rewind, ale [](rewind.md)je vždy přesunut zpět na konec souboru před provedením jakékoli operace zápisu, aby existující data nemohly být přepsána.

Režim **"a"** neodstraní značku EOF před připojením k souboru. Po připojení k příkazu typ MS-DOS se zobrazí pouze data do původní značky EOF a nikoli do všech dat připojených k souboru. Režim **"a +"** odstraní značku EOF před připojením k souboru. Po připojení se v příkazu typ MS-DOS zobrazí všechna data v souboru. Režim **"a +"** je vyžadován pro připojení k souboru datového proudu, který je ukončen pomocí značky EOF CTRL + Z.

Je-li zadán typ přístupu **"r +"** , **"w +** " nebo **"a +"** , jsou povoleny čtení i zápis. (Soubor se označuje jako otevřený pro "aktualizaci".) Pokud však přepnete ze čtení na zápis, musí vstupní operace narazit na značku EOF. Pokud není k dispozici žádný znak EOF, je nutné použít volání do funkce umístění souboru. Funkce umístění souborů jsou **fsetpos**, [fseek](fseek-fseeki64.md)a Rewind. [](rewind.md) Když přepnete ze zápisu do čtení, je nutné použít volání **fflush** nebo na funkci umístění souboru.

Kromě výše uvedených hodnot mohou být do *režimu* zahrnuty následující znaky pro určení režimu překladu znaků nového řádku:

|Modifikátor *režimu*|Režim překladu|
|-|-|
| **t** | Otevřít v textovém (přeloženém) režimu. |
| **b** | Otevřít v binárním (nepřeloženém) režimu; překlady týkající se znaků návratového znaku a znaku čárového kanálu jsou potlačeny. |

V textovém (přeloženém) režimu je CTRL + Z interpretována jako znak konce souboru na vstupu. V souborech otevřených pro čtení/zápis pomocí **"a +"** **fopen_s** zkontroluje kombinaci kláves CTRL + Z na konci souboru a pokud je to možné, odstraní ho. K tomu dochází, protože použití [fseek](fseek-fseeki64.md) a **ftell** k přesunu v souboru, který končí kombinací kláves CTRL + Z, může způsobit, že se [fseek](fseek-fseeki64.md) nesprávně chová na konci souboru.

V textovém režimu jsou také přeloženy kombinace kanálů návratového řádku na začátek vstupu a znaky kanálu čáry jsou přeloženy na kombinace kanálů návratového řádku na výstupu. Pokud funkce vstupně-výstupních streamů v kódování Unicode funguje v textovém režimu (ve výchozím nastavení), předpokládá se, že zdrojový nebo cílový datový proud je sekvence vícebajtových znaků. Proto funkce vstupního streamu Unicode převádí vícebajtové znaky na velké znaky (jako by bylo volání funkce **mbtowc** ). Ze stejného důvodu funkce výstupní datové proudy Unicode převádějí velké znaky na vícebajtové znaky (jako při volání funkce **wctomb** ).

Pokud **t** nebo **b** není uveden v *režimu*, výchozí režim překladu je definován globální proměnnou [_fmode](../../c-runtime-library/fmode.md). Pokud je **t** nebo **b** předpona argumentu, funkce se nezdařila a vrátí **hodnotu null**.

Další informace o používání textových a binárních režimů v kódování Unicode a vícebajtových vstupně-výstupních operacích naleznete v tématu [text a v binárním režimu vstupně](../../c-runtime-library/text-and-binary-mode-file-i-o.md) -výstupních operací a [datových proudů Unicode v textových a binárních režimech](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|Modifikátor *režimu*|Chování|
|-|-|
| **c** | Povolte příznak potvrzení pro přidružený *název souboru* tak, aby se obsah vyrovnávací paměti souboru zapsal přímo na disk, pokud je zavolána možnost **fflush** nebo **_flushall** . |
| **n** | Obnovte příznak potvrzení pro přidružený *název souboru* na "bez potvrzení". Toto nastavení je výchozí. Také přepisuje příznak globálního potvrzení, Pokud propojíte program s COMMODE. OBJ. Pokud explicitně nepřipojíte program k COMMODE, je výchozí hodnota příznak pro globální potvrzování nepotvrzená. OBJ (viz [možnosti propojení](../../c-runtime-library/link-options.md)). |
| **N** | Určuje, že soubor není děděn podřízenými procesy. |
| **S** | Určuje, že ukládání do mezipaměti je optimalizované pro, ale ne omezené na, sekvenční přístup z disku. |
| **R** | Určuje, že ukládání do mezipaměti je optimalizované pro, ale ne omezené na, náhodný přístup z disku. |
| **T** | Určuje soubor jako dočasný. Pokud je to možné, nezaprázdní na disk. |
| **D** | Určuje soubor jako dočasný. Odstraní se po zavření posledního ukazatele na soubor. |
| **ccs=** _encoding_ | Určuje znakovou sadu kódovanou jako použitou pro tento soubor (jednu z **UTF-8**, **UTF-16LE**nebo **Unicode**). Pokud chcete kódování ANSI, ponechte nespecifikovanou. |

Platné znaky pro řetězec *režimu* použitý v **fopen_s** a [_fdopen](fdopen-wfdopen.md) odpovídají argumentům *oflag* používaným v [_open](open-wopen.md) a [_sopen](sopen-wsopen.md), a to následujícím způsobem.

|Znaky v řetězci *režimu*|Ekvivalentní hodnota *oflag* pro _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY** &#124; **_O_APPEND** (obvykle **_O_WRONLY** &#124; **_O_CREAT** &#124;* * _O_APPEND * *)|
|**a+**|**_O_RDWR** &#124; **_O_APPEND** (obvykle **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**r**|**_O_RDONLY**|
|**r+**|**_O_RDWR**|
|**w**|**_O_WRONLY** (obvykle **_O_WRONLY** &#124; **_O_CREAT** &#124;* * _O_TRUNC * *)|
|**w+**|**_O_RDWR** (obvykle **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**c**|Žádné|
|**n**|Žádný|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs=UNICODE**|**_O_WTEXT**|
|**ccs=UTF-8**|**_O_UTF8**|
|**ccs=UTF-16LE**|**_O_UTF16**|

Pokud používáte režim **RB** , nebude potřeba portovat kód a očekávat, že byste si museli přečíst velký soubor a/nebo nemusíte nic zajímat o výkon sítě, soubory Win32 mapované paměti můžou být také možností.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

Možnosti v *režimu* **c**, **n**a **t** jsou rozšířeními Microsoftu pro **fopen_s** a [_fdopen](fdopen-wfdopen.md) a neměla by se používat tam, kde je žádoucí přenositelnost ANSI.

## <a name="example"></a>Příklad

```C
// crt_fopen_s.c
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   errno_t err;

   // Open for read (will fail if file "crt_fopen_s.c" does not exist)
   err  = fopen_s( &stream, "crt_fopen_s.c", "r" );
   if( err == 0 )
   {
      printf( "The file 'crt_fopen_s.c' was opened\n" );
   }
   else
   {
      printf( "The file 'crt_fopen_s.c' was not opened\n" );
   }

   // Open for write
   err = fopen_s( &stream2, "data2", "w+" );
   if( err == 0 )
   {
      printf( "The file 'data2' was opened\n" );
   }
   else
   {
      printf( "The file 'data2' was not opened\n" );
   }

   // Close stream if it is not NULL
   if( stream )
   {
      err = fclose( stream );
      if ( err == 0 )
      {
         printf( "The file 'crt_fopen_s.c' was closed\n" );
      }
      else
      {
         printf( "The file 'crt_fopen_s.c' was not closed\n" );
      }
   }

   // All other files are closed:
   int numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen_s.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
