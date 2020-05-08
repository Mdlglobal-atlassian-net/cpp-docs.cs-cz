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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d468226028928e3edfe67cc7f9b9eec06e06bd56
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914879"
---
# <a name="fopen-_wfopen"></a>fopen, _wfopen

Otevře soubor. Bezpečnější verze těchto funkcí, které provádějí dodatečné ověřování parametrů a návratové kódy chyb, jsou k dispozici. viz [fopen_s, _wfopen_s](fopen-s-wfopen-s.md).

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

*Bitmap*<br/>
Název souboru.

*Mode*<br/>
Druh přístupu, který je povolený.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na otevřený soubor. Hodnota nulového ukazatele označuje chybu. Pokud má parametr *filename* nebo *Mode* **hodnotu null** nebo je prázdný řetězec, tyto funkce aktivují obslužnou rutinu neplatného parametru, která je popsána v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **hodnotu null** a nastaví **errno** na **EINVAL**.

Další informace najdete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **fopen** otevře soubor určený parametrem *filename*. Ve výchozím nastavení je řetězec zužujícího *názvu souboru* interpretován pomocí znakové stránky ANSI (CP_ACP). V aplikacích pro stolní počítače s Windows se dá změnit na znakovou stránku OEM (CP_OEMCP) pomocí funkce [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) . Pomocí funkce [AreFileApisANSI](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi) můžete zjistit, jestli je *název souboru* INTERPRETOVÁN pomocí standardu ANSI nebo výchozí znakové stránky OEM systému. **_wfopen** je **fopen**verze s nejrůznějšími znaky; argumenty **_wfopen** jsou řetězce s libovolným znakem. V opačném případě **_wfopen** a **fopen** se chovají stejně. Pouze použití **_wfopen** nemá vliv na kódované znakové sady, která se používá v datovém proudu souboru.

**fopen** akceptuje cesty, které jsou platné v systému souborů v okamžiku provedení; **fopen** přijímá cesty a cesty UNC, které zahrnují mapované síťové jednotky, pokud systém, který spouští kód, má přístup ke sdílené složce nebo mapované jednotce v době spuštění. Když vytváříte cesty pro **fopen**, ujistěte se, že jednotky, cesty nebo sdílené síťové složky budou k dispozici v prostředí pro spuštění. Jako oddělovače adresářů v cestě můžete použít buď lomítka (/),\\nebo zpětná lomítka ().

Před provedením dalších operací se souborem vždy zkontrolujte vrácenou hodnotu, abyste viděli, zda má ukazatel hodnotu NULL. Pokud dojde k chybě, globální proměnná **errno** je nastavena a lze ji použít k získání konkrétních informací o chybě. Další informace najdete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="unicode-support"></a>Podpora kódování Unicode

**fopen** podporuje datové proudy souborů Unicode. Chcete-li otevřít soubor Unicode, předejte příznak **CCS** , který určuje požadované kódování pro **fopen**, následovně.

> **SOUBOR \*fp = fopen ("NewFile. txt"; "RT +; CCS =**_Encoding_**");**

Povolené hodnoty *kódování* jsou **Unicode**, **UTF-8**a **UTF-16LE**.

Když se soubor otevře v režimu Unicode, vstupní funkce převede data načtená ze souboru do dat UTF-16 uložených jako typ **wchar_t**. Funkce, které zapisují do souboru otevřeného v režimu Unicode, očekávají vyrovnávací paměti, které obsahují data UTF-16 uložená jako typ **wchar_t**. Pokud je soubor kódovaný jako UTF-8, data UTF-16 se při zápisu přeloží na UTF-8 a obsah zakódovaný v kódování UTF-8 se převede na UTF-16 při čtení. Při pokusu o čtení nebo zápis lichého počtu bajtů v režimu Unicode dojde k chybě [ověření parametru](../../c-runtime-library/parameter-validation.md) . Chcete-li číst nebo zapisovat data uložená v programu jako UTF-8, místo režimu Unicode použijte textový nebo binární souborový režim. Zodpovídáte za všechny požadované překlady kódování.

Pokud soubor již existuje a je otevřen pro čtení nebo připojení, znak pořadí bajtů (BOM), pokud je v souboru přítomen, určuje kódování. Kódování kusovníku má přednost před kódováním, které je určeno příznakem **CCS** . Kódování **CCS** se používá pouze v případě, že není k dispozici žádný kusovník nebo je soubor novým souborem.

> [!NOTE]
> Zjišťování kusovníku platí pouze pro soubory, které jsou otevřeny v režimu Unicode (tj. předáním příznaku **CCS** ).

Následující tabulka shrnuje režimy, které se používají pro různé příznaky **CCS** předané **fopen** a označení pořadí bajtů v souboru.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Kódování použitá na základě příznaku CCS a kusovníku

|příznak CCS|Žádný kusovník (nebo nový soubor)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**SADY**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Soubory otevřené pro zápis do režimu Unicode mají automaticky zapsaného kusovníku.

Pokud *mode* je režim **"a, CCS =**_Encoding_**"**, **fopen** se nejprve pokusí otevřít soubor pomocí přístupu pro čtení i zápis. Pokud je to úspěšné, funkce přečte BOM a určí kódování souboru; Pokud se to nepovede, funkce použije výchozí kódování souboru. V obou případech bude **fopen** znovu otevřít soubor pomocí přístupu jen pro zápis. (Tato možnost se vztahuje pouze na režim **"a** +", nikoli na režim **"a +"** .)

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

*Režim* řetězce znaků Určuje typ přístupu, který je požadován pro soubor, následovně.

|*Mode*|Access|
|-|-|
| **í** | Otevře se pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, volání **fopen** se nezdařilo. |
| **w** | Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah je zničen. |
| **určitého** | Otevře se pro zápis na konci souboru (přidávání) bez odebrání označení konec souboru (EOF) před zápisem nových dat do souboru. Vytvoří soubor, pokud neexistuje. |
| **"r +"** | Otevře se pro čtení i zápis. Soubor musí existovat. |
| **"w +"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah se zničí. |
| **"a +"** | Otevře se pro čtení a připojení. Operace připojení zahrnuje odstranění značky EOF před zápisem nových dat do souboru. Po dokončení zápisu se značka EOF neobnoví. Vytvoří soubor, pokud neexistuje. |

Když se soubor otevře pomocí přístupového typu **"a"** nebo typu **"a +"** , na konci souboru se objeví všechny operace zápisu. Ukazatel na soubor lze změnit pomocí [fseek](fseek-fseeki64.md) nebo [Rewind](rewind.md), ale je vždy přesunut zpět na konec souboru před provedením jakékoli operace zápisu. Stávající data proto nelze přepsat.

Režim **"a"** neodstraní značku EOF před připojením k souboru. Po navázání připojení příkaz Typ MS-DOS zobrazuje pouze data do původní značky EOF a ne data připojena k souboru. Před připojením k souboru odebere režim **"a +"** značku EOF. Po připojení se v příkazu typ MS-DOS zobrazí všechna data v souboru. Režim **"a +"** se vyžaduje pro připojení k souboru datového proudu, který je ukončený pomocí značky EOF CTRL + Z.

Je-li zadán typ přístupu **"r +"**, **"w +"** nebo **"a +"** , jsou povoleny čtení i zápis (soubor je označován jako otevřený pro "aktualizaci"). Pokud však přepnete ze čtení na zápis, musí vstupní operace narazit na značku EOF. Pokud není k dispozici žádný znak EOF, je nutné použít volání do funkce umístění souboru. Funkce umístění souborů jsou **fsetpos**, [fseek](fseek-fseeki64.md)a [Rewind](rewind.md). Když přepnete ze zápisu na čtení, je nutné použít volání do **fflush** nebo do funkce umístění souboru.

Kromě předchozích hodnot lze do *režimu* připojit následující znaky a určit tak režim překladu pro znaky nového řádku.

|Modifikátor *režimu*|Režim překladu|
|-|-|
| **š** | Otevřít v textovém (přeloženém) režimu. |
| **b** | Otevřít v binárním (nepřeloženém) režimu; překlady týkající se znaků návratového znaku a znaku čárového kanálu jsou potlačeny. |

V textovém režimu CTRL + Z je interpretována jako znak EOF při vstupu. V souborech, které jsou otevřeny pro čtení a zápis pomocí **"a +"**, **fopen** zkontroluje kombinaci kláves CTRL + Z na konci souboru a odebere jej, pokud je to možné. K tomu je potřeba, protože použití [fseek](fseek-fseeki64.md) a **ftell** k přesunu v souboru, který končí kombinací kláves CTRL + Z, může způsobit, že se [fseek](fseek-fseeki64.md) chová nesprávně na konci souboru.

V textovém režimu jsou kombinace kanálů návratového řádku překládány na vstupní kanály na vstupu a znaky kanálu čáry jsou přeloženy na kombinace kanálů návratového řádku na výstupu. Pokud funkce vstupně-výstupních streamů v kódování Unicode funguje v textovém režimu (ve výchozím nastavení), předpokládá se, že zdrojový nebo cílový datový proud je sekvence vícebajtových znaků. Proto funkce vstupního streamu Unicode převádí vícebajtové znaky na velké znaky (jako by bylo volání funkce **mbtowc** ). Ze stejného důvodu funkce výstupní datové proudy Unicode převádějí velké znaky na vícebajtové znaky (jako při volání funkce **wctomb** ).

Pokud **t** nebo **b** není uveden v *režimu*, výchozí režim překladu je definován globální proměnnou [_fmode](../../c-runtime-library/fmode.md). Pokud je **t** nebo **b** předpona argumentu, funkce se nezdařila a vrátí **hodnotu null**.

Další informace o tom, jak používat textové a binární režimy v kódování Unicode a vícebajtových vstupně-výstupních operacích, najdete v textu [a v binárním režimu vstupně-výstupních](../../c-runtime-library/text-and-binary-mode-file-i-o.md) operací a [datových proudech Unicode v textových a binárních](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)režimech.

Následující možnosti lze připojit k *režimu* pro určení dalšího chování.

|Modifikátor *režimu*|Chování|
|-|-|
| **r** | Povolte příznak potvrzení pro přidružený *název souboru* , aby se obsah vyrovnávací paměti souboru zapsal přímo na disk, pokud je zavolána buď **fflush** nebo **_flushall** . |
| **n** | Obnovte příznak potvrzení pro přidružený *název souboru* na "bez potvrzení". Toto nastavení je výchozí. Také přepisuje příznak globálního potvrzení, Pokud propojíte program s COMMODE. OBJ. Pokud explicitně nepřipojíte program k COMMODE, je výchozí hodnota příznak pro globální potvrzování nepotvrzená. OBJ (viz [možnosti propojení](../../c-runtime-library/link-options.md)). |
| **N** | Určuje, že soubor není děděn podřízenými procesy. |
| **S** | Určuje, že ukládání do mezipaměti je optimalizované pro, ale ne omezené na, sekvenční přístup z disku. |
| **R** | Určuje, že ukládání do mezipaměti je optimalizované pro, ale ne omezené na, náhodný přístup z disku. |
| **T** | Určuje soubor jako dočasný. Pokud je to možné, nezaprázdní na disk. |
| **Trojrozměrné** | Určuje soubor jako dočasný. Odstraní se po zavření posledního ukazatele na soubor. |
| **CCS =**_kódování_ | Určuje znakovou sadu kódovanou jako použitou pro tento soubor (jednu z **UTF-8**, **UTF-16LE**nebo **Unicode**). Pokud chcete kódování ANSI, ponechte nespecifikovanou. |

Platné znaky pro řetězec *režimu* , který je použit v **fopen** a **_fdopen** odpovídají argumentům *oflag* , které se používají v [_open](open-wopen.md) a [_sopen](sopen-wsopen.md), jak je znázorněno níže.

|Znaky v řetězci *režimu*|Ekvivalentní hodnota *oflag* pro \_Open/\_sopen|
|-------------------------------|----------------------------------------------------|
|**určitého**|**\_O\_WRONLY** &#124; ** \_o\_připojení** (obvykle ** \_o\_WRONLY** &#124; ** \_o\_** vytvoření &#124; ** \_o\_připojení**)|
|**a +**|**\_O\_RDWR** &#124; ** \_o\_připojení** (obvykle ** \_o\_RDWR** &#124; ** \_o\_připojení** &#124; ** \_o\_** vytvořit)|
|**í**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (obvykle ** \_o\_WRONLY** &#124; ** \_o\_** vytvoření &#124; ** \_o\_TRUNC –**)|
|**w +**|**\_O\_RDWR** (obvykle ** \_o\_RDWR** &#124; ** \_o\_** vytvoření &#124; ** \_o\_TRUNC –**)|
|**b**|**\_O\_binárním souboru**|
|**š**|**\_O\_-text**|
|**r**|Žádné|
|**n**|Žádné|
|**S**|**\_O\_sekvenčním**|
|**R**|**\_O\_náhodných**|
|**T**|**\_O\_SHORTLIVED**|
|**Trojrozměrné**|**\_O\_dočasnou**|
|**CCS = UNICODE**|**\_O\_WTEXT**|
|**CCS = UTF-8**|**\_O\_UTF8**|
|**CCS = UTF-16LE**|**\_O\_UTF16**|

Pokud používáte režim **RB** , nemusíte port používat, a pokud očekáváte, že budete číst většinu velkých souborů nebo nemáte obavy o výkon sítě, můžete také zvážit, zda použít soubory Win32 mapované paměti jako možnosti.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fopen**|\<stdio. h>|
|**_wfopen**|\<stdio. h> nebo \<WCHAR. h>|

**_wfopen** je rozšířením společnosti Microsoft. Další informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

Možnosti v *režimu* **c**, **n**, **t**, **S**, **R**, **t**a **D** jsou rozšířeními Microsoftu pro **fopen** a **_fdopen** a neměla by se používat tam, kde je žádoucí přenositelnost ANSI.

## <a name="example-1"></a>Příklad 1

Následující program otevírá dva soubory.  K zavření prvního souboru používá **fclose** a **_fcloseall** k zavření všech zbývajících souborů.

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

Následující program vytvoří soubor (nebo přepíše jeden, pokud existuje) v textovém režimu, který má kódování Unicode.  Pak zapíše dva řetězce do souboru a soubor zavře. Výstupem je soubor s názvem _wfopen_test. XML, který obsahuje data z výstupní části.

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
