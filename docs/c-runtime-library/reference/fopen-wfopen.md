---
title: fopen, _wfopen
ms.date: 4/2/2020
api_name:
- _wfopen
- fopen
- _o__wfopen
- _o_fopen
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 4b9fa6542996b2c16128a841e2611b85e995be2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346412"
---
# <a name="fopen-_wfopen"></a>fopen, _wfopen

Otevře soubor. K dispozici jsou bezpečnější verze těchto funkcí, které provádějí další ověřovací a návratové chybové kódy. viz [fopen_s, _wfopen_s](fopen-s-wfopen-s.md).

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

*Název_souboru*<br/>
Název souboru.

*Režimu*<br/>
Druh přístupu, který je povolen.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí ukazatel na otevřený soubor. Hodnota ukazatele null označuje chybu. Pokud je *název souboru* nebo *režim* **null** nebo prázdný řetězec, tyto funkce aktivují neplatnou obslužnou rutinu parametru, která je popsána v části [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce vrátí **null** a nastavit **errno** **eINVAL**.

Další informace naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **fopen** otevře soubor určený *názvem souboru*. Ve výchozím nastavení je řetězec úzkého *názvu souboru* interpretován pomocí znakové stránky ANSI (CP_ACP). V aplikacích pro Windows Desktop to lze změnit na znakovou stránku OEM (CP_OEMCP) pomocí funkce [SetFileApisToOEM.](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) Pomocí funkce [AreFileApisANSI](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi) můžete určit, zda je *název souboru* interpretován pomocí znakové stránky ANSI nebo výchozího systémového oem. **_wfopen** je širokoznaková verze **fopen**; argumenty, které mají **_wfopen,** jsou řetězce s širokými znaky. V opačném případě **se _wfopen** a **fopen** chovají stejně. Použití **_wfopen** nemá vliv na kódovnou znakovou sadu, která se používá v datovém proudu souborů.

**fopen** přijímá cesty, které jsou platné v systému souborů v místě spuštění; **fopen** přijímá cesty UNC a cesty, které zahrnují namapované síťové jednotky, pokud systém, který spustí kód, má přístup ke sdílené nebo mapované jednotce v době spuštění. Při vytváření cest pro **fopen**, ujistěte se, že jednotky, cesty nebo sdílené síťové sdílené složky budou k dispozici v prostředí provádění. Jako oddělovače adresářů v cestě můžete\\použít lomítka (/) nebo zpětná lomítka ( ).

Před provedením dalších operací se souborem vždy zkontrolujte vrácenou hodnotu, zda je ukazatel null. Pokud dojde k chybě, globální proměnná **errno** je nastavena a může být použita k získání konkrétních informací o chybě. Další informace naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="unicode-support"></a>Podpora kódování Unicode

**fopen** podporuje datové proudy souborů Unicode. Chcete-li otevřít soubor Unicode, předejte příznak **ccs,** který určuje požadované kódování pro **fopen**, následujícím způsobem.

> **SOUBOR \*fp = fopen("newfile.txt", "rt+, ccs=**_kódování_**");**

Povolené hodnoty *kódování* jsou **UNICODE**, **UTF-8**a **UTF-16LE**.

Při otevření souboru v režimu Unicode překládají vstupní funkce data, která jsou ze souboru přečtena, do dat UTF-16 uložených jako typ **wchar_t**. Funkce, které zapisují do souboru otevřeného v režimu Unicode, očekávají vyrovnávací paměti, které obsahují data UTF-16 uložená jako typ **wchar_t**. Pokud je soubor kódován jako UTF-8, pak UTF-16 data je přeložen do UTF-8, když je zapsán, a soubor uTF-8 kódovaný obsah je přeložen do UTF-16 při čtení. Pokus o čtení nebo zápis lichého počtu bajtů v režimu Unicode způsobí chybu [ověření parametru.](../../c-runtime-library/parameter-validation.md) Chcete-li číst nebo zapisovat data uložená v programu jako UTF-8, použijte místo režimu Unicode textový nebo binární režim souborů. Nesete odpovědnost za veškerý požadovaný překlad kódování.

Pokud soubor již existuje a je otevřen pro čtení nebo připojení, určuje kódování značka bajtového pořadí (BOM), pokud je v souboru přítomen. Kódování kusovníku má přednost před kódováním, které je určeno příznakem **ccs.** Kódování **ccs** se používá pouze v případě, že není k dispozici žádný kusovník nebo je soubor nový soubor.

> [!NOTE]
> Detekce kusovníku se vztahuje pouze na soubory, které jsou otevřeny v režimu Unicode (to znamená předáním příznaku **ccs).**

Následující tabulka shrnuje režimy, které se používají pro různé **ccs** příznaky dané **fopen** a Byte objednávky v souboru.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Použitá kódování na základě příznaku ccs a kusovníku

|ccs vlajka|Žádný kusovník (nebo nový soubor)|KUS: UTF-8|KUS: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**Unicode**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Soubory otevřené pro zápis v režimu Unicode mají zápisník napsaný automaticky.

Pokud je *režim* **"a, ccs=**_encoding_**"**, **fopen** nejprve se pokusí otevřít soubor pomocí přístupu pro čtení i zápis. Pokud se to podaří, funkce přečte kusovník k určení kódování pro soubor; Pokud se to nezdaří, funkce použije výchozí kódování pro soubor. V obou případech **fopen** znovu otevře soubor pomocí přístupu pouze pro zápis. (To platí pouze pro režim **"a",** nikoli pro režim **"a+".)**

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**Fopen**|**Fopen**|**_wfopen**|

*Režim* řetězce znaků určuje druh přístupu, který je požadován pro soubor, a to následujícím způsobem.

|*Režimu*|Access|
|-|-|
| **"r"** | Otevírá se pro čtení. Pokud soubor neexistuje nebo jej nelze najít, volání **fopen** se nezdaří. |
| **"w"** | Otevře prázdný soubor pro psaní. Pokud daný soubor existuje, jeho obsah je zničen. |
| **"a"** | Otevře se pro zápis na konci souboru (připojení) bez odebrání značky konce souboru (EOF) před zápisem nových dat do souboru. Vytvoří soubor, pokud neexistuje. |
| **"r+"** | Otevírá se pro čtení i psaní. Soubor musí existovat. |
| **"w+"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah je zničen. |
| **"a+"** | Otevírá se pro čtení a připojení. Operace připojení zahrnuje odebrání značky EOF před zápisem nových dat do souboru. Značka EOF není obnovena po dokončení zápisu. Vytvoří soubor, pokud neexistuje. |

Při otevření souboru pomocí typu **přístupu "a"** nebo **typu přístupu "a+",** všechny operace zápisu dojít na konci souboru. Ukazatel souboru lze přemístit pomocí [fseek](fseek-fseeki64.md) nebo [převíjení zpět](rewind.md), ale je vždy přesunuta zpět na konec souboru před provedením jakékoli operace zápisu. Proto existující data nelze přepsat.

Režim **"a"** neodebere značku EOF před připojením k souboru. Po připojení došlo k ms-dos typ příkazu zobrazí pouze data až do původní značky EOF a žádná data připojená k souboru. Před připojením k souboru režim **"a+"** odstraní značku EOF. Po připojení se v příkazu MS-DOS TYPE zobrazí všechna data v souboru. Režim **"a+"** je vyžadován pro připojení k souboru datového proudu, který je ukončen značkou CTRL+Z EOF.

Pokud je zadán typ přístupu **"r+"**, **"w+"** nebo **"a+",** je povoleno čtení i zápis (soubor je údajně otevřený pro "aktualizovat"). Však při přepnutí ze čtení na zápis, vstupní operace musí dojít značky EOF. Pokud neexistuje žádný EOF, musíte použít zasahující volání funkce umístění souboru. Funkce umístění souborů jsou **fsetpos**, [fseek](fseek-fseeki64.md)a [rewind](rewind.md). Při přechodu z zápisu na čtení, musíte použít zasahující volání buď **fflush** nebo funkce umístění souboru.

Kromě dřívějších hodnot lze do *režimu* připojit následující znaky, které určují režim překladu znaků nového řádku.

|*modifikátor režimu*|Režim překladu|
|-|-|
| **t** | Otevřít v textovém (přeloženém) režimu. |
| **B** | Otevřít v binárním (nepřeloženém) režimu; překlady zahrnující znaky carriage-return a line feed jsou potlačeny. |

V textovém režimu je ctrl+z interpretován jako znak EOF na vstupu. V souborech, které jsou otevřeny pro čtení/ zápis pomocí **"a+"**, **fopen** zkontroluje CTRL + Z na konci souboru a odstraní ji, pokud je to možné. Důvodem je, že pomocí [fseek](fseek-fseeki64.md) a **ftell** přesunout v rámci souboru, který končí CTRL + Z může způsobit [fseek](fseek-fseeki64.md) chovat nesprávně blízko konce souboru.

V textovém režimu jsou kombinace podávání řádků přeloženy do jednoho řádkového podávání na vstupu a znaky posuvu řádků jsou přeloženy do kombinací posuvu řádku na výstupu. Pokud funkce vstupně-videa/videa Unicode pracuje v textovém režimu (výchozí), zdrojový nebo cílový datový proud se považuje za posloupnost vícebajtových znaků. Proto funkce vstupu datového proudu Unicode převádějí vícebajtové znaky na široké znaky (jako by voláním funkce **mbtowc).** Ze stejného důvodu unicode stream-output funkce převést široké znaky vícebajtové znaky (jako by volání **wctomb** funkce).

Pokud **t** nebo **b** není uveden v *režimu*, výchozí režim překladu je definován globální proměnnou [_fmode](../../c-runtime-library/fmode.md). Pokud **t** nebo **b** je předponou argument, funkce se nezdaří a vrátí **NULL**.

Další informace o použití textového a binárního režimu v režimech Unicode a vícebajtových datových proudech vi/v naleznete v [tématu Text a binární režim V/O souboru](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [Unicode Stream I/O v režimu Text a binární režimy](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Následující možnosti lze připojit do *režimu* určit další chování.

|*modifikátor režimu*|Chování|
|-|-|
| **C** | Povolte příznak potvrzení pro přidružený *název souboru,* aby byl obsah vyrovnávací paměti souboru zapsán přímo na disk, pokud je volána **fflush** nebo **_flushall.** |
| **N** | Obnovte příznak potvrzení pro přidružený *název souboru* na "no-commit". Toto nastavení je výchozí. Také přepíše příznak globálního potvrzení, pokud propojíte program s COMMODE.OBJ. Výchozí hodnota příznaku globálního potvrzení je "no-commit", pokud explicitně nepropojíte program s COMMODE. OBJ (viz [Možnosti odkazu](../../c-runtime-library/link-options.md)). |
| **N** | Určuje, že soubor není zděděn podřízenými procesy. |
| **S** | Určuje, že ukládání do mezipaměti je optimalizováno pro sekvenční přístup z disku, ale není omezen na něj. |
| **R** | Určuje, že ukládání do mezipaměti je optimalizováno pro náhodný přístup z disku, ale není omezeno na něj. |
| **T** | Určuje soubor jako dočasný. Pokud je to možné, není vyprázdněna na disk. |
| **D** | Určuje soubor jako dočasný. Odstraní se při zavření ukazatele posledního souboru. |
| **ccs =**_kódování_ | Určuje kódovku znakovou sadu, která má být pro tento soubor používána (jedna z **UTF-8**, **UTF-16LE**nebo **UNICODE).** Pokud chcete kódování ANSI, ponechejte nespecifikované. |

Platné znaky pro řetězec *režimu,* který se používá v **fopen** a **_fdopen** odpovídají *argumentům oflag,* které se používají v [_open](open-wopen.md) a [_sopen](sopen-wsopen.md), následujícím způsobem.

|Znaky v *řetězci režimu*|Ekvivalentní hodnota *oflag* \_\_pro otevření/ otevření|
|-------------------------------|----------------------------------------------------|
|**A**|**\_O\_WRONLY** &#124; ** \_O\_APPEND** (obvykle ** \_O\_WRONLY** &#124; ** \_O\_CREAT** &#124; ** \_O\_APPEND)**|
|**a+**|**\_O\_RDWR** &#124; ** \_O\_APPEND** (obvykle ** \_O\_RDWR** &#124; ** \_O\_APPEND** &#124; ** \_O\_CREAT)**|
|**R**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**W**|**\_O\_WRONLY** (obvykle ** \_\_O WRONLY** &#124; ** \_\_O CREAT** &#124; ** \_O\_TRUNC)**|
|**w+**|**\_O\_RDWR** (obvykle ** \_\_O RDWR** &#124; ** \_\_O CREAT** &#124; ** \_O\_TRUNC)**|
|**B**|**\_O\_BINÁRNÍ**|
|**t**|**\_O\_TEXT**|
|**C**|Žádný|
|**N**|Žádný|
|**S**|**\_O\_SEKVENČNÍ**|
|**R**|**\_O\_NÁHODNÉ**|
|**T**|**\_O\_SHORTŽIL**|
|**D**|**\_O\_DOČASNÉ**|
|**ccs=UNICODE**|**\_O\_WTEXT**|
|**ccs=UTF-8**|**\_O\_UTF8**|
|**ccs=UTF-16LE**|**\_O\_UTF16**|

Pokud používáte **režim rb,** není třeba přepojit kód a pokud očekáváte, že budete číst většinu velkého souboru nebo se neobáváte výkonu sítě, můžete také zvážit, zda použít paměťové soubory Win32 jako možnost.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**Fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> \<nebo wchar.h>|

**_wfopen** je rozšíření společnosti Microsoft. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

Možnosti *režimu* **c,** **n**, **t**, **S**, **R**, **T**a **D** jsou rozšířeními společnosti Microsoft pro **fopen** a **_fdopen** a neměly by být používány tam, kde je požadována přenositelnost ANSI.

## <a name="example-1"></a>Příklad 1

Následující program otevře dva soubory.  Používá **fclose** zavřít první soubor a **_fcloseall** zavřít všechny zbývající soubory.

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

Následující program vytvoří soubor (nebo přepíše jeden, pokud existuje), v textovém režimu, který má kódování Unicode.  Potom zapíše dva řetězce do souboru a zavře soubor. Výstupem je soubor s názvem _wfopen_test.xml, který obsahuje data z výstupního oddílu.

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

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
