---
title: fopen_s, _wfopen_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bef5587188cebe4ed7e91cbd95eb46cca7f05044
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405624"
---
# <a name="fopens-wfopens"></a>fopen_s, _wfopen_s

Otevře soubor. Tyto verze nástroje [fopen –, _wfopen –](fopen-wfopen.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ukazatel na ukazatele souboru, který se zobrazí ukazatel na otevřený soubor.

*Název souboru*<br/>
Název souboru.

*Režim*<br/>
Typ přístupu povolena.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěšného; Kód chyby při selhání. V tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o tyto kódy chyb.

### <a name="error-conditions"></a>Chybové stavy

|*pFile*|*Název souboru*|*Režim*|Návratová hodnota|Obsah *pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**HODNOTU NULL**|všechny|všechny|**EINVAL –**|Beze změny|
|všechny|**HODNOTU NULL**|všechny|**EINVAL –**|Beze změny|
|všechny|všechny|**HODNOTU NULL**|**EINVAL –**|Beze změny|

## <a name="remarks"></a>Poznámky

Soubory, které jsou otevřené podle **fopen_s –** a **_wfopen_s –** nejsou lze sdílet. Pokud budete vyžadovat, aby byl soubor lze sdílet, použijte [_fsopen –, _wfsopen –](fsopen-wfsopen.md) s příslušnou sdílení konstanta režimu – například **_sh_denyno –** pro sdílení pro čtení a zápis.

**Fopen_s –** funkce otevře soubor, který je zadán *filename*. **_wfopen_s –** je verze široká charakterová **fopen_s –**; argumenty, které mají **_wfopen_s –** jsou široká charakterová řetězce. **_wfopen_s –** a **fopen_s –** chovat jinak shodně.

**fopen_s –** přijímá cesty, které jsou platné v systému souborů v okamžiku spuštění; Přijal UNC cesty a cesty, které zahrnují namapované síťové jednotky **fopen_s –** tak dlouho, dokud systém, který spouští kód má přístup ke sdílené složce nebo namapované síťové jednotky při spuštění. Když vytvoříte cesty pro **fopen_s –**, nevytvářejte předpoklady o dostupnosti jednotek, cesty, nebo síťové sdílené složky v prostředí pro spuštění. Můžete použít buď lomítka (/) nebo zpětná lomítka (\\) jako oddělovače adresáře v cestě.

Tyto funkce ověřit jejich parametrů. Pokud *pFile*, *filename*, nebo *režimu* je ukazatel s hodnotou null, tyto funkce vygeneruje výjimka neplatný parametr, jak je popsáno v [ověření parametru ](../../c-runtime-library/parameter-validation.md).

Vždy Zkontrolujte návratovou hodnotu chcete zobrazit, pokud bylo úspěšné funkce před provedením jakékoli další operace na souboru. Pokud dojde k chybě, je vrácen kód chyby a globální proměnné **errno** nastavena. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="unicode-support"></a>Podpora kódování Unicode

**fopen_s –** podporuje kódování Unicode souborů datových proudů. Chcete-li otevřít nové nebo existující souboru Unicode, předat *ccs* příznak, který určuje požadovanou kódování **fopen_s –**:

**fopen_s – (& fp, "novýsoubor.txt", "rw, ccs =**_kódování_**");**

Povolené hodnoty *kódování* jsou **UNICODE**, **UTF-8**, a **znakové sady UTF-16LE**. Pokud existuje není zadaná žádná hodnota pro *kódování*, **fopen_s –** používá kódování ANSI.

Pokud soubor již existuje a je otevřen pro čtení nebo připojením, bajtů pořadí značky (Kusovníku), pokud je k dispozici v souboru Určuje kódování. Kódování BOM má přednost před přes kódování, která je zadána *ccs* příznak. *Ccs* kódování je použít pouze v případě žádné BOM je přítomen nebo pokud je soubor nový soubor.

> [!NOTE]
> Detekce BOM platí jenom pro soubory, které jsou otevřeny v režimu Unicode; To znamená, službou předávání *ccs* příznak.

Následující tabulka shrnuje pro různé režimy *ccs* příznaky, které jsou uvedeny k **fopen_s –** a značky pořadí bajtů v souboru.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Použít na základě kódování ccs příznak a BOM

|CCS příznak|Žádné BOM (nebo nový soubor)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**KÓDOVÁNÍ UNICODE**|**ZNAKOVÉ SADY UTF-16LE**|**ZNAKOVÉ SADY UTF-8**|**ZNAKOVÉ SADY UTF-16LE**|
|**ZNAKOVÉ SADY UTF-8**|**ZNAKOVÉ SADY UTF-8**|**ZNAKOVÉ SADY UTF-8**|**ZNAKOVÉ SADY UTF-16LE**|
|**ZNAKOVÉ SADY UTF-16LE**|**ZNAKOVÉ SADY UTF-16LE**|**ZNAKOVÉ SADY UTF-8**|**ZNAKOVÉ SADY UTF-16LE**|

Soubory, které jsou otevřené pro zápis v režimu Unicode mají Kusovník zapisovat do nich automaticky.

Pokud *režimu* je **"a, ccs =**_kódování_**"**, **fopen_s –** poprvé pokusí otevřít soubor s oprávnění ke čtení přístup a přístup pro zápis. V případě úspěšného funkce přečte BOM určete kódování pro soubor; Pokud je úspěšné, funkce používá výchozí kódování pro soubor. V obou případech **fopen_s –** znovu otevře soubor s přístupem jen pro zápis. (To se vztahuje na **a** jen není režimu **a+**.)

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s –**|**fopen_s –**|**fopen_s –**|**_wfopen_s**|

Řetězec znaků *režimu* Určuje typ přístupu, který je požadovaný pro soubor, následujícím způsobem.

|*Režim*|Access|
|-|-|
**"r"**|Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, **fopen_s –** volání selže.
**"w"**|Otevře se prázdný soubor pro zápis. Pokud je daný soubor existuje, její obsah se způsobem zničena.
**"a"**|Otevře pro zápis na konec souboru (připojení) bez odebrání značky end souboru (EOF) před nová data jsou zapsána do souboru. Pokud neexistuje, vytvoří soubor.
**"r +"**|Otevře pro čtení i zápis. Soubor musí existovat.
**"w +"**|Otevře se prázdný soubor pro čtení i zápis. Pokud soubor existuje, její obsah se způsobem zničena.
**"+"**|Otevře pro čtení a připojením. Připojování operaci zahrnuje odebrání značky EOF před nová data jsou zapsána do souboru. Po dokončení zápisu, nedojde k obnovení EOF značky. Pokud neexistuje, vytvoří soubor.

Při otevření souboru s použitím **"a"** nebo **"+"** přístup k typu, všechny zápisu operace probíhají na konci souboru. Ukazatele souboru můžete změnit jejich umístění pomocí [fseek](fseek-fseeki64.md) nebo [rewind](rewind.md), ale je vždy přesunuta zpět na konec souboru před všechny zápisu operace se provádí tak, aby existující data nelze přepsat.

**"A"** režimu neodebere značky EOF před připojením k souboru. Po připojení došlo k chybě, MS-DOS typ příkazu se zobrazí pouze data až původní EOF značky a není žádná data, která je připojena k souboru. **"+"** Režimu odebrat značky EOF před připojením k souboru. Po připojení, zobrazí příkaz MS-DOS typ všechna data v tomto souboru. **"+"** Režim je vyžadován pro připojení do datového proudu souboru, který je ukončen pomocí kombinace kláves CTRL + Z EOF značky.

Když **"r +"**, **"w +"**, nebo **"+"** byl zadán typ přístupu, jsou povoleny pro čtení i zápis. (Soubor říká, že je třeba otevřít pro "update".) Ale po přepnutí z čtení pro zápis vstupní operaci dojde EOF značky. Pokud není k dispozici žádné konce souboru, je nutné použít použité volání funkce umístění souboru. Umístění souboru funkce jsou **fsetpos –**, [fseek](fseek-fseeki64.md), a [rewind](rewind.md). Po přepnutí z zápis do čtení, je nutné použít použité volání buď **fflush –** nebo funkci umístění souboru.

Kromě výše uvedené hodnoty můžou být součástí následující znaky *režimu* k určení režim překladu pro znaky nového řádku:

|*režim* – modifikátor|Režim překladu|
|-|-|
**t**|Otevřete v textu (přeložit) režimu.
**b**|Otevřete v binárním režimu (nepřeložený); jsou potlačovány překlady zahrnující znaky CR a konce řádku.

V režimu textových (přeložit) CTRL + Z interpretována jako znak end souboru na vstup. V souborech otevřít pro čtení/zápis s **"+"**, **fopen_s –** kontroluje CTRL + Z na konci souboru a odstraní ji, pokud je to možné. To je provést, protože používá [fseek](fseek-fseeki64.md) a **ftell –** v souboru, který může způsobit, že na konci CTRL + Z, přesuňte [fseek](fseek-fseeki64.md) chovat nesprávně blíží konec souboru.

Také v režimu textových znaků CR vrátit-konce řádku kombinace jsou převedeny do jednoho přečtené na vstup a znaky konce řádku jsou převedeny na kombinace znaků CR vrátit-konce řádku na výstup. Pokud funkce datového proudu I/O Unicode funguje v režimu textových (výchozí), zdroj nebo cílový datový proud předpokládá se, že posloupnosti vícebajtových znaků. Proto funkce vstupního datového proudu Unicode převést více-bajtové znaky na široké znaky (jako Pokud voláním **mbtowc –** funkce). Ze stejného důvodu, funkce výstup datového proudu Unicode převést více-bajtové znaky široké znaky (jako Pokud voláním **wctomb –** funkce).

Pokud **t** nebo **b** není uveden v *režimu*, je výchozí režim překladu definované globální proměnná [_fmode –](../../c-runtime-library/fmode.md). Pokud **t** nebo **b** předponou argument, funkce selže a vrátí je **NULL**.

Další informace o používání textovém a binárním režimu v kódování Unicode a vícebajtové datového proudu I/O najdete v tématu [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [vstupně-výstupní datový proud Unicode v textovém a binárním režimu](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|*režim* – modifikátor|Chování|
|-|-|
**c**|Povolit příznak potvrzení pro přidruženého *filename* tak, aby obsah souboru vyrovnávací paměti je zapsán přímo na disk v případě buď **fflush –** nebo **_flushall –** je volána.
**n**|Resetujte příznak potvrzení pro přidruženého *filename* na "Ne potvrzováním." Toto nastavení je výchozí. Pokud jste váš program s COMMODE.OBJ také přepisuje příznak globálního potvrzení. Globální potvrzení příznak výchozí hodnota je "Ne potvrzováním" Pokud explicitně propojit váš program s COMMODE. OBJ (viz [možnosti odkazů](../../c-runtime-library/link-options.md)).
**N**|Určuje, že soubor není zděděna podřízené procesy.
**S**|Určuje, že ukládání do mezipaměti je optimalizovaná pro, ale není omezen na, sekvenční přístup z disku.
**R**|Určuje, že ukládání do mezipaměti je optimalizovaná pro, ale není omezena na náhodný přístup z disku.
**T**|Určuje soubor jako dočasnou. Pokud je to možné, není vyprázdněných na disk.
**D**|Určuje soubor jako dočasnou. Odstraní se při zavření posledního ukazatele souboru.
**CCS =**_kódování_|Určuje kódovaného znakové sady (jeden z **UTF-8**, **znakové sady UTF-16LE**, nebo **UNICODE**) pro tento soubor. Ponechejte neurčené, pokud chcete kódování ANSI.

Platné znaky pro *režimu* řetězec použitý v **fopen_s –** a [_fdopen –](fdopen-wfdopen.md) odpovídají *oflag* argumenty použité v [_ Otevřete](open-wopen.md) a [_sopen –](sopen-wsopen.md), a to takto.

|Znaky v *režimu* řetězec|Ekvivalentní *oflag* hodnotu _Otevřít/_sopen –|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_wronly –** &#124; **_o_append –** (obvykle **_o_wronly –** &#124; **_o_creat –** &#124;** _o_append – **)|
|**+**|**_O_rdwr –** &#124; **_o_append –** (obvykle **_o_rdwr –** &#124; **_o_append –** &#124; **_o_creat –** )|
|**r**|**_O_RDONLY –**|
|**r +**|**_O_RDWR –**|
|**w**|**_O_wronly –** (obvykle **_o_wronly –** &#124; **_o_creat –** &#124;** _o_trunc – **)|
|**w +**|**_O_rdwr –** (obvykle **_o_rdwr –** &#124; **_o_creat –** &#124; **_o_trunc –**)|
|**b**|**_O_BINARY –**|
|**t**|**_O_TEXT –**|
|**c**|Žádné|
|**n**|Žádné|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**CCS = kódování UNICODE**|**_O_WTEXT**|
|**CCS = UTF-8**|**_O_UTF8**|
|**CCS = UTF-16LE**|**_O_UTF16**|

Pokud používáte **rb** režimu, nebudete muset portu kódu a očekávají čtení spoustu soubor a/nebo nezáleží výkon sítě, soubory mapované paměti Win32 může být také možnost.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fopen_s –**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

**c**, **n**, a **t** *režimu* možnosti jsou rozšíření Microsoft pro **fopen_s –** a [_fdopen –](fdopen-wfdopen.md) a neměl by se používat, kde je žádoucí přenositelnost ANSI.

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

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
