---
title: fopen, _wfopen
ms.date: 11/04/2016
apiname:
- _wfopen
- fopen
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
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
ms.openlocfilehash: 9c7a7fed8eabc38f1a0a67587d495e75ba8fa3d8
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702905"
---
# <a name="fopen-wfopen"></a>fopen, _wfopen

Otevře se soubor. Bezpečnější verze těchto funkcí, které provádějí další parametr ověření a návratové kódy chyb jsou k dispozici. Zobrazit [fopen_s, _wfopen_s](fopen-s-wfopen-s.md).

## <a name="syntax"></a>Syntaxe

```C
FILE *fopen(
   const char *filename,
   const char *mode
);
FILE *_wfopen(
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Název souboru.

*Režim*<br/>
Druh přístupu, který je povolený.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na otevřený soubor. Hodnota nulového ukazatele indikuje chybu. Pokud *filename* nebo *režimu* je **NULL** nebo prázdný řetězec, spustí tyto funkce obslužnou rutinu neplatného parametru, která je popsána v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **NULL** a nastavte **errno** k **EINVAL**.

Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Fopen** funkce otevře soubor, který je určen *filename*. Ve výchozím nastavení, zužte *filename* řetězec je interpretován s použitím znakové stránce ANSI (CP_ACP). V aplikacích Windows Desktop To můžete změnit na znakovou stránku OEM (CP_OEMCP) s použitím [SetFileApisToOEM](/windows/desktop/api/fileapi/nf-fileapi-setfileapistooem) funkce. Můžete použít [AreFileApisANSI](/windows/desktop/api/fileapi/nf-fileapi-arefileapisansi) funkce k určení, zda *filename* je interpretován s použitím ANSI nebo systémová znaková stránka OEM výchozí. **_wfopen –** je verze širokého znaku **fopen**; argumenty, které mají **_wfopen –** jsou širokoznaké řetězce. V opačném případě **_wfopen –** a **fopen** chovají identicky. Použití pouze **_wfopen –** neovlivňuje programovou znakovou sadu, která se používá v souboru datového proudu.

**fopen –** přijímá cesty, které jsou platné v době vykonání; systému souborů **fopen** přijímá cesty UNC a cesty, které vyžadují namapované síťové jednotky jako systém, který spustí kód má přístup ke sdílené složce namapované jednotce v době spuštění. Při vytváření cest pro **fopen**, ujistěte se, že jednotky, cesty nebo síťová úložiště bude k dispozici ve spouštěcím prostředí. Můžete použít buď lomítka (/), nebo zpětná lomítka (\\) jako oddělovač v cestě.

Vždy Zkontrolujte návratovou hodnotu, zda ukazatel je NULL, před provedením jakékoli další operace se souborem. Pokud dojde k chybě, globální proměnnou **errno** nastavena a slouží k získání konkrétní informace o chybě. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="unicode-support"></a>Podpora kódování Unicode

**fopen –** podporuje datové proudy souborů Unicode. Chcete-li otevřít soubor Unicode, předejte **ccs** příznak, který určuje požadované kódování **fopen**, následujícím způsobem.

> **SOUBOR \*fp = fopen ("novýsoubor.txt", "rt + ccs =**_kódování_**");**

Povolené hodnoty parametru *kódování* jsou **UNICODE**, **UTF-8**, a **UTF-16LE**.

Když je soubor otevřen v režimu Unicode, vstupní funkce převede data, která je pro čtení ze souboru o datech UTF-16 uložené jako typ **wchar_t**. Funkce, které se zápis do souboru otevřeném v režimu Unicode očekávat vyrovnávacích pamětí, které obsahují data UTF-16 uložené jako typ **wchar_t**. Pokud soubor zakódován pomocí kódování UTF-8, je při zápisem a kódování UTF-8 obsah souboru je přeložit na UTF-16, když je pro čtení dat UTF-16 přeložit na UTF-8. Pokus o čtení nebo zápisu lichý počet bajtů v kódování Unicode režimu příčiny [ověření parametru](../../c-runtime-library/parameter-validation.md) chyby. Pro čtení nebo zápis dat, která je uložena ve svém programu jako UTF-8, použijte namísto režimu Unicode textová nebo binární režim souboru. Zodpovídáte za všechny požadované kódování překladu.

Pokud soubor již existuje a je otevřen pro čtení nebo zobrazení, Byte pořadí Mark (Kusovníku), pokud je k dispozici v souboru Určuje kódování. BOM kódování má přednost před kódováním, která je zadána **ccs** příznak. **Ccs** kódování se používá pouze při není přítomno BOM nebo soubor je soubor nový.

> [!NOTE]
> BOM detekce je aplikována pouze na soubory, které jsou otevřeny v režimu Unicode (to znamená podle předání **ccs** příznak).

Následující tabulka shrnuje režimy používané pro různé **ccs** příznaky k **fopen** a značky pořadí bajtů v souboru.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Kódování použitá na základě příznaku ccs a BOM

|CCS příznak|Žádný BOM (nebo nový soubor)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**KÓDOVÁNÍ UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Soubory otevřené pro zápis v režimu Unicode mají automaticky zapsaný BOM.

Pokud *režimu* je **", ccs =**_kódování_**"**, **fopen** poprvé pokusí otevřít soubor s použitím oprávnění ke čtení a přístup pro zápis. Pokud se toto povede, přečte funkce BOM pro určení kódování souboru. Když se to nepovede, funkce používá výchozí kódování souboru. V obou případech **fopen** znovu otevře soubor s použitím přístup jen pro zápis. (To platí pro **"a"** režimu pouze, aby **"a +"** režimu.)

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen –**|**fopen –**|**_wfopen**|

Řetězec znaků *režimu* určuje druh přístupu, které jsou požadovány pro soubor, následujícím způsobem.

|*Režim*|Access|
|-|-|
| **"r"** | Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, **fopen** volání selže. |
| **"w"** | Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah zničen. |
| **"a"** | Otevře se pro zápis na konci souboru (přidávání) bez odstranění značky end file (EOF) před zápisem do souboru. Vytvoří soubor, pokud neexistuje. |
| **"r +"** | Otevře pro čtení i zápis. Soubor musí existovat. |
| **"w +"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah zničen. |
| **"a +"** | Otevře pro čtení a připojení. Operace zobrazení zahrnuje odstranění značky EOF před zápisem do souboru. Nedojde k obnovení značky EOF po dokončení zápisu. Vytvoří soubor, pokud neexistuje. |

Když je soubor otevřen pomocí **"a"** získat přístup k typu nebo **"a +"** získat přístup k typu, všechny zápisu operace dojít na konci souboru. Ukazatel na soubor lze přesunout pomocí [fseek](fseek-fseeki64.md) nebo [rewind](rewind.md), ale je vždy přesunut na konec souboru před jakékoli zápisu operace. Existující data proto nemohou být přepsána.

**"A"** režimu neodstraní značku EOF před připojením k souboru. Po připojení došlo k chybě, příkaz MS-DOS TYPE zobrazí pouze data až po původní značku EOF, nikoliv data připojená k souboru. Před připojením k souboru **"a +"** režimu odstranění značky EOF. Po připojení zobrazí příkaz MS-DOS TYPE všechna data v souboru. **"A +"** režim je vyžadován pro připojení k souboru datového proudu, který je přerušen skrze značku EOF CTRL + Z.

Když **"r +"**, **"w +"**, nebo **"a +"** je zadán přístupový typ, je povoleno čtení i zápis (Tento soubor říká, že je otevřen pro "úpravy"). Avšak po přepnutí ze čtení na zápis musí vstupní operace narazit na značku EOF. Pokud není dostupný žádný EOF, musíte použít opětovné volání funkce polohování souboru. Funkce polohování souboru jsou **fsetpos**, [fseek](fseek-fseeki64.md), a [rewind](rewind.md). Po přepnutí ze zápisu na čtení, je nutné použít opětovné volání na buď **fflush –** nebo na funkci polohování souboru.

Kromě předchozích hodnot, tyto znaky lze připojit k *režimu* pro určení režimu překladu pro znaky nového řádku.

|*režim* modifikátor|Režim překladu|
|-|-|
| **t** | Otevřít v textovém (přeloženém) režimu. |
| **b** | Otevřít v binárním (nepřeloženém) režimu; překlady typů návrat na začátek řádku a znak odřádkování jsou potlačeny. |

V textovém režimu CTRL + Z je interpretován jako znak EOF vstup. V souborech, které jsou otevřené pro čtení/zápis pomocí **"a +"**, **fopen** kontroluje CTRL + Z na konci souboru a odebere ji, pokud je to možné. Toto je provedeno z důvodu použití [fseek](fseek-fseeki64.md) a **ftell –** pro přesun v rámci souboru, který končí CTRL + Z může způsobit, že [fseek](fseek-fseeki64.md) neočekávané chování na konci souboru.

V textovém režimu kombinace typu návrat návrat na začátek řádku-jsou přeloženy na vstupu a znaky odřádkování jsou přeloženy na kombinace návratový znak odřádkování návrat na začátek řádku na výstupu. Pokud pracuje funkce datového proudu vstupně-Unicode v textovém režimu (výchozí), zdroj nebo cílový datový proud brán jako sekvence vícebajtových znaků. Proto se funkce vstupním datovým proudem sady Unicode převodu vícebajtových znaků na široké znaky (jako by volání **mbtowc** funkce). Ze stejného důvodu, převést funkce proudem sady Unicode široké znaky na vícebajtové znaky (jako by volání **wctomb –** funkce).

Pokud **t** nebo **b** není uveden v *režimu*, je výchozí režim překladu definován pomocí globální proměnné [_fmode](../../c-runtime-library/fmode.md). Pokud **t** nebo **b** předponou argumentu, funkce selže a vrátí **NULL**.

Další informace o tom, jak použít textové a binární režimy v kódování Unicode a vícebajtových stream vstupně-najdete v tématu [textového a binárního režimu souboru vstupně-výstupních operací](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [vstupně-výstupní Stream kódování Unicode v textovém a binárním režimu](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Tyto možnosti lze připojit k *režimu* zadat další chování.

|*režim* modifikátor|Chování|
|-|-|
| **c** | Povolte příznak pro zápis pro přidružený *filename* tak, aby se obsah vyrovnávací paměti souboru zapsán přímo na disk, pokud **fflush –** nebo **_flushall –** je volána. |
| **n** | Resetovat příznak pro zápis pro přidružený *filename* na "Neukládat." Toto nastavení je výchozí. Přepíše také globální, pokud propojení s COMMODE.OBJ. Výchozí globální příznak je "Neukládat", pokud výslovně nedojde k propojení programu s COMMODE. OBJ (viz [možnosti propojení](../../c-runtime-library/link-options.md)). |
| **N** | Určuje, že soubor není děděný podřízenými procesy. |
| **S** | Určuje, že je mezipaměť optimalizovaná pro, ale nikoliv omezená, sekvenčním přístupem z disku. |
| **R** | Určuje, že je mezipaměť optimalizovaná pro, ale nikoliv omezená, náhodný přístup z disku. |
| **T** | Určuje soubor jako dočasný. Pokud je to možné, není zapsán na disk. |
| **D** | Určuje soubor jako dočasný. Je smazán po uzavření posledního ukazatele na soubor. |
| **ccs=**_encoding_ | Určuje kódovaného znakovou sadu (jeden z **UTF-8**, **UTF-16LE**, nebo **UNICODE**) pro tento soubor. Ponechte nevyplněné, pokud chcete, aby kódování ANSI. |

Platné znaky pro *režimu* řetězec, který se používá v **fopen** a **_fdopen –** odpovídají *oflag* argumenty, které se používají v [_Otevřít](open-wopen.md) a [_sopen](sopen-wsopen.md), následujícím způsobem.

|Znaky v *režimu* řetězec|Ekvivalentní *oflag* hodnota \_otevřít /\_sopen –|
|-------------------------------|----------------------------------------------------|
|**a**|**\_O\_WRONLY** &#124;  **\_O\_APPEND** (obvykle  **\_O\_WRONLY** &#124;  **\_O\_CREAT** &#124;  **\_O\_APPEND**)|
|**a+**|**\_O\_RDWR** &#124;  **\_O\_APPEND** (obvykle  **\_O\_RDWR** &#124;  **\_ O\_APPEND** &#124;  **\_O\_CREAT** )|
|**r**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (obvykle  **\_O\_WRONLY** &#124;  **\_O\_CREAT** &#124;  **\_O\_TRUNC**)|
|**w+**|**\_O\_RDWR** (obvykle  **\_O\_RDWR** &#124;  **\_O\_CREAT** &#124;  **\_ O\_TRUNC**)|
|**b**|**\_O\_BINÁRNÍ**|
|**t**|**\_O\_TEXT**|
|**c**|Žádná|
|**n**|Žádná|
|**S**|**\_O\_SEKVENČNÍ**|
|**R**|**\_O\_RANDOM**|
|**T**|**\_O\_SHORTLIVED**|
|**D**|**\_O\_DOČASNÉ**|
|**ccs=UNICODE**|**\_O\_WTEXT**|
|**ccs=UTF-8**|**\_O\_UTF8**|
|**ccs=UTF-16LE**|**\_O\_UTF16**|

Pokud používáte **rb** režimu, není nutné k portu váš kód a očekávat větší část velkého souboru nebo nejsou obavy o výkon sítě, můžete také zvážit, zda použití paměti soubory typu Win32 namapované jako možnost.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fopen –**|\<stdio.h>|
|**_wfopen**|\<stdio.h > nebo \<wchar.h >|

**_wfopen –** je rozšířením společnosti Microsoft. Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

**c**, **n**, **t**, **S**, **R**, **T**, a **D**  *režimu* možnosti jsou rozšíření Microsoft pro **fopen** a **_fdopen –** by se neměl používat, kde je žádoucí přenositelnost ANSI.

## <a name="example-1"></a>Příklad 1

Následující program otevírá dva soubory.  Používá **fclose –** pro uzavření prvního souboru a **_fcloseall** pro uzavření ostatních souborů.

```C
// crt_fopen.c
// compile with: /W3
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   int numclosed;

   // Open for read (will fail if file "crt_fopen.c" does not exist)
   if( (stream  = fopen( "crt_fopen.c", "r" )) == NULL ) // C4996
   // Note: fopen is deprecated; consider using fopen_s instead
      printf( "The file 'crt_fopen.c' was not opened\n" );
   else
      printf( "The file 'crt_fopen.c' was opened\n" );

   // Open for write
   if( (stream2 = fopen( "data2", "w+" )) == NULL ) // C4996
      printf( "The file 'data2' was not opened\n" );
   else
      printf( "The file 'data2' was opened\n" );

   // Close stream if it is not NULL
   if( stream)
   {
      if ( fclose( stream ) )
      {
         printf( "The file 'crt_fopen.c' was not closed\n" );
      }
   }

   // All other files are closed:
   numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="example-2"></a>Příklad 2

Následující program vytvoří soubor (nebo jedna přepíše, pokud existuje), v textovém režimu, který má kódování sady Unicode.  Následně zapíše dva řetězce do souboru a soubor zavře. Výstupem je soubor pojmenovaný _wfopen_test.xml, který obsahuje data z výstupní sekce.

```C
// crt__wfopen.c
// compile with: /W3
// This program creates a file (or overwrites one if
// it exists), in text mode using Unicode encoding.
// It then writes two strings into the file
// and then closes the file.

#include <stdio.h>
#include <stddef.h>
#include <stdlib.h>
#include <wchar.h>

#define BUFFER_SIZE 50

int main(int argc, char** argv)
{
    wchar_t str[BUFFER_SIZE];
    size_t  strSize;
    FILE*   fileHandle;

    // Create an the xml file in text and Unicode encoding mode.
    if ((fileHandle = _wfopen( L"_wfopen_test.xml",L"wt+,ccs=UNICODE")) == NULL) // C4996
    // Note: _wfopen is deprecated; consider using _wfopen_s instead
    {
        wprintf(L"_wfopen failed!\n");
        return(0);
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"<xmlTag>\n");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"</xmlTag>");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Close the file.
    if (fclose(fileHandle))
    {
        wprintf(L"fclose failed!\n");
    }
    return 0;
}
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
