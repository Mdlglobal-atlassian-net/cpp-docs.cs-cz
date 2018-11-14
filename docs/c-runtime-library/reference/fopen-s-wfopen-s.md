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
ms.openlocfilehash: 1309f991b8251bde7d614aa274d8d2e9da7a8ed3
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51333343"
---
# <a name="fopens-wfopens"></a>fopen_s, _wfopen_s

Otevře se soubor. Tyto verze [fopen _wfopen –](fopen-wfopen.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ukazatel na ukazatel na soubor, který bude příjemcem ukazatel na otevřený soubor.

*Název souboru*<br/>
Název souboru.

*Režim*<br/>
Typ přístupu povolený.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; Kód chyby při selhání. Zobrazit [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto chybových kódech.

### <a name="error-conditions"></a>Chybové podmínky

|*pFile*|*Název souboru*|*Režim*|Návratová hodnota|Obsah *pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**HODNOTU NULL**|Všechny|Všechny|**EINVAL**|beze změny|
|Všechny|**HODNOTU NULL**|Všechny|**EINVAL**|beze změny|
|Všechny|Všechny|**HODNOTU NULL**|**EINVAL**|beze změny|

## <a name="remarks"></a>Poznámky

Soubory, které jsou otevírány **fopen_s** a **_wfopen_s** nejsou sdílet. Pokud budete požadovat, aby soubor sdílet, použijte [_fsopen – _wfsopen –](fsopen-wfsopen.md) s odpovídající sdílení režimu konstantou – například **_SH_DENYNO** pro čtení a zápisu pro sdílení obsahu.

**Fopen_s** funkce otevře soubor, který je určen *filename*. **_wfopen_s** je verze širokého znaku **fopen_s**; argumenty, které mají **_wfopen_s** jsou širokoznaké řetězce. **_wfopen_s** a **fopen_s** se jinak chovají stejně.

**fopen_s** přijímá cesty, které jsou platné v době vykonání; systému souborů Se přijal cesty UNC a cesty, které vyžadují namapované síťové jednotky **fopen_s** tak dlouho, dokud systém, který se spouští kód má přístup ke sdílené složce nebo namapované síťové jednotky při spuštění. Při vytváření cest pro **fopen_s**, nemusíte vytvářet předpoklady o dostupnosti jednotky, cesty, nebo sdílených síťových složek ve spouštěcím prostředí. Můžete použít buď lomítka (/), nebo zpětná lomítka (\\) jako oddělovač v cestě.

Tyto funkce ověřují své parametry. Pokud *pFile*, *filename*, nebo *režimu* je ukazatel s hodnotou null, tyto funkce generují výjimku neplatného parametru, jak je popsáno v [Parameter Validation ](../../c-runtime-library/parameter-validation.md).

Vždy Zkontrolujte návratovou hodnotu, pokud chcete zobrazit, pokud se spuštění funkce zdařilo před provedením jakékoli operace v souboru. Pokud dojde k chybě, je vrácen kód chyby a globální proměnné **errno** nastavena. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="unicode-support"></a>Podpora kódování Unicode

**fopen_s** podporuje datové proudy souborů Unicode. Chcete-li otevřít nový nebo existující soubor Unicode, předejte *ccs* příznak, který určuje požadované kódování **fopen_s**:

**fopen_s (& fp, "novýsoubor.txt", "rw, ccs =**_kódování_**");**

Povolené hodnoty parametru *kódování* jsou **UNICODE**, **UTF-8**, a **UTF-16LE**. Pokud zde není zadána žádná hodnota pro *kódování*, **fopen_s** používá kódování ANSI.

Pokud soubor již existuje a je otevřen pro čtení nebo zobrazení, Byte pořadí Mark (Kusovníku), pokud jsou k dispozici v souboru Určuje kódování. BOM kódování má přednost před kódováním, která je zadána *ccs* příznak. *Ccs* kódování se používá pouze v případě BOM je k dispozici nebo pokud se jedná o nový soubor.

> [!NOTE]
> BOM detekce je aplikována pouze na soubory, které jsou otevřeny v režimu Unicode. To znamená podle předání *ccs* příznak.

Následující tabulka shrnuje režimy pro různé *ccs* příznaky, které jsou uvedeny **fopen_s** a pro značky pořadí bajtů v souboru.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Kódování použitá na základě příznaku ccs a BOM

|CCS příznak|Žádný BOM (nebo nový soubor)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**KÓDOVÁNÍ UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Soubory, které jsou otevřené pro zápis v režimu Unicode mají automaticky zapsaný BOM.

Pokud *režimu* je **", ccs =**_kódování_**"**, **fopen_s** poprvé pokusí otevřít soubor s čtení přístup a oprávnění k zápisu. V případě úspěchu, přečte funkce BOM pro určení kódování souboru. Pokud není úspěšné, funkce používá výchozí kódování souboru. V obou případech **fopen_s** znovu otevře soubor s přístupem jen pro zápis. (To se vztahuje na **a** jen není režimu **a+**.)

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s –**|**fopen_s –**|**fopen_s –**|**_wfopen_s**|

Řetězec znaků *režimu* určuje druh přístupu, které jsou požadovány pro soubor, následujícím způsobem.

|*Režim*|Access|
|-|-|
| **"r"** | Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, **fopen_s** volání selže. |
| **"w"** | Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah zničen. |
| **"a"** | Otevře se pro zápis na konci souboru (přidávání) bez odstranění značky end file (EOF) před zápisem do souboru. Vytvoří soubor, pokud neexistuje. |
| **"r +"** | Otevře pro čtení i zápis. Soubor musí existovat. |
| **"w +"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah zničen. |
| **"a +"** | Otevře pro čtení a připojení. Operace zobrazení zahrnuje odstranění značky EOF před zápisem do souboru. Nedojde k obnovení značky EOF po dokončení zápisu. Vytvoří soubor, pokud neexistuje. |

Když je soubor otevřen pomocí **"a"** nebo **"a +"** získat přístup k typu, všechny zápisu operace dojít na konci souboru. Ukazatel na soubor lze přesunout pomocí [fseek](fseek-fseeki64.md) nebo [rewind](rewind.md), ale to je vždy přesunut na konec souboru před jakékoli zápisu operace provádí, takže existující data nelze přepsat.

**"A"** režimu neodstraní značku EOF před připojením k souboru. Po připojení došlo k chybě, příkaz MS-DOS TYPE zobrazí pouze data až po původní značku EOF, nikoliv data, která se připojuje k souboru. **"A +"** režimu odstranění značky EOF před připojením k souboru. Po připojení zobrazí příkaz MS-DOS TYPE všechna data v souboru. **"A +"** režim je vyžadován pro přidávání do datového proudu souboru, který je přerušen pomocí značku EOF CTRL + Z.

Když **"r +"**, **"w +"**, nebo **"a +"** je zadán přístupový typ, je povoleno čtení i zápis. (Tento soubor se říká, že bude otevřen pro "úpravy".) Avšak po přepnutí ze čtení na zápis musí vstupní operace narazit na značku EOF. Pokud není dostupný žádný EOF, musíte použít opětovné volání funkce polohování souboru. Funkce polohování souboru jsou **fsetpos**, [fseek](fseek-fseeki64.md), a [rewind](rewind.md). Po přepnutí ze zápisu na čtení, je nutné použít opětovné volání na buď **fflush –** nebo na funkci polohování souboru.

Kromě výše uvedených hodnot, mohou být součástí následující znaky *režimu* pro určení režimu překladu pro znaky nového řádku:

|*režim* modifikátor|Režim překladu|
|-|-|
| **t** | Otevřít v textovém (přeloženém) režimu. |
| **b** | Otevřít v binárním (nepřeloženém) režimu; překlady typů návrat na začátek řádku a znak odřádkování jsou potlačeny. |

V textovém (přeloženém) režimu je CTRL + Z interpretováno jako endovém souborovém znak na vstupu. V souborech otevřených pro čtení/zápis s **"a +"**, **fopen_s** vyhledává CTRL + Z na konci souboru a odstraní ji, pokud je to možné. Toto je provedeno z důvodu použití [fseek](fseek-fseeki64.md) a **ftell –** pro přesun v rámci souboru, který končí CTRL + Z, může způsobit, že [fseek](fseek-fseeki64.md) nesprávné chování na konci souboru.

V textovém režimu, také kombinace typu návrat návrat na začátek řádku-jsou přeloženy na vstupu a znaky odřádkování jsou přeloženy na kombinace návratový znak odřádkování návrat na začátek řádku na výstupu. Pokud pracuje funkce datového proudu vstupně-Unicode v textovém režimu (výchozí), zdroj nebo cílový datový proud brán jako sekvence vícebajtových znaků. Proto se funkce vstupním datovým proudem sady Unicode převodu vícebajtových znaků na široké znaky (jako by volání **mbtowc** funkce). Ze stejného důvodu, převést funkce proudem sady Unicode široké znaky na vícebajtové znaky (jako by volání **wctomb –** funkce).

Pokud **t** nebo **b** není uveden v *režimu*, je výchozí režim překladu definován pomocí globální proměnné [_fmode](../../c-runtime-library/fmode.md). Pokud **t** nebo **b** předponou argumentu, funkce selže a vrátí **NULL**.

Další informace o používání textové a binární režimy v kódování Unicode a vícebajtových stream vstupně-najdete v tématu [textového a binárního režimu souboru vstupně-výstupních operací](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [vstupně-výstupní Stream kódování Unicode v textovém a binárním režimu](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|*režim* modifikátor|Chování|
|-|-|
| **c** | Povolte příznak pro zápis pro přidružený *filename* tak, aby se obsah vyrovnávací paměti souboru zapsán přímo na disk, pokud **fflush –** nebo **_flushall –** je volána. |
| **n** | Resetovat příznak pro zápis pro přidružený *filename* na "Neukládat." Toto nastavení je výchozí. Přepíše také globální, pokud propojení s COMMODE.OBJ. Výchozí globální příznak je "Neukládat", pokud výslovně nedojde k propojení programu s COMMODE. OBJ (viz [možnosti propojení](../../c-runtime-library/link-options.md)). |
| **N** | Určuje, že soubor není děděný podřízenými procesy. |
| **S** | Určuje, že je mezipaměť optimalizovaná pro, ale nikoliv omezená, sekvenčním přístupem z disku. |
| **R** | Určuje, že je mezipaměť optimalizovaná pro, ale nikoliv omezená, náhodný přístup z disku. |
| **T** | Určuje soubor jako dočasný. Pokud je to možné, není zapsán na disk. |
| **D** | Určuje soubor jako dočasný. Je smazán po uzavření posledního ukazatele na soubor. |
| **CCS =**_kódování_ | Určuje kódovaného znakovou sadu (jeden z **UTF-8**, **UTF-16LE**, nebo **UNICODE**) pro tento soubor. Ponechte nevyplněné, pokud chcete, aby kódování ANSI. |

Platné znaky pro *režimu* řetězec použitý v **fopen_s** a [_fdopen –](fdopen-wfdopen.md) odpovídají *oflag* argumenty použité v [_ Otevřete](open-wopen.md) a [_sopen](sopen-wsopen.md), následujícím způsobem.

|Znaky v *režimu* řetězec|Ekvivalentní *oflag* hodnotu _Otevřít/_sopen|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY** &#124; **_O_APPEND** (obvykle **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_APPEND **)|
|**a +**|**_O_RDWR** &#124; **_O_APPEND** (obvykle **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**r**|**_O_RDONLY**|
|**r +**|**_O_RDWR**|
|**w**|**_O_WRONLY** (obvykle **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_TRUNC **)|
|**w +**|**_O_RDWR** (obvykle **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**c**|Žádné|
|**n**|Žádné|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**CCS = kódování UNICODE**|**_O_WTEXT**|
|**CCS = UTF-8**|**_O_UTF8**|
|**CCS = UTF-16LE**|**_O_UTF16**|

Pokud používáte **rb** režimu, nebudete muset přeneste kód a očekávat spoustu soubor a/nebo o výkon sítě, soubory mapované do paměti Win32 může být také možnost.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fopen_s –**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

**c**, **n**, a **t** *režimu* možnosti jsou rozšíření Microsoft pro **fopen_s** a [_fdopen –](fdopen-wfdopen.md) by se neměl používat, kde je žádoucí přenositelnost ANSI.

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

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
