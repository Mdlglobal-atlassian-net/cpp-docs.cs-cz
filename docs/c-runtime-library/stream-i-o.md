---
title: I/O proudu
ms.date: 11/04/2016
helpviewer_keywords:
- I/O routines, stream I/O
- I/O [CRT], stream
- stream I/O
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
ms.openlocfilehash: 0fc49d4cd26593cb02a2ff05c3205cc630ef848c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444617"
---
# <a name="stream-io"></a>I/O proudu

Tyto funkce zpracovávají data v různých velikostech a formátech od jednotlivých znaků až po velké datové struktury. Poskytují také ukládání do vyrovnávací paměti, což může zlepšit výkon. Výchozí velikost vyrovnávací paměti datového proudu je 4K. Tyto rutiny ovlivňují pouze vyrovnávací paměti vytvořené rutinami běhové knihovny a nemají žádný vliv na vyrovnávací paměti vytvořené operačním systémem.

## <a name="stream-io-routines"></a>Rutiny v/v streamování

|Rutina|Použití|
|-------------|---------|
|[clearerr](../c-runtime-library/reference/clearerr.md), [clearerr_s](../c-runtime-library/reference/clearerr-s.md)|Vymazat indikátor chyb pro Stream|
|[fclose](../c-runtime-library/reference/fclose-fcloseall.md)|Zavřít Stream|
|[_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)|Zavřít všechny otevřené streamy kromě **vstupu**, **stdout**a **stderr**|
|[_fdopen, wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Přidružit datový proud k popisovači souborů otevřeného souboru|
|[feof](../c-runtime-library/reference/feof.md)|Test na konec souboru v datovém proudu|
|[ferror](../c-runtime-library/reference/ferror.md)|Testování chyby streamování|
|[fflush](../c-runtime-library/reference/fflush.md)|Vyprázdnit datový proud do vyrovnávací paměti nebo úložného zařízení|
|[fgetc, fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|Přečíst znak z datového proudu (verze funkcí **getc –** a **getwc**)|
|[_fgetchar, _fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|Přečíst znak ze **standardního vstupu** (verze funkce **GetChar** a **getwchar**)|
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|Získat indikátor pozice datového proudu|
|[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)|Přečíst řetězec ze streamu|
|[_fileno](../c-runtime-library/reference/fileno.md)|Získat popisovač souboru přidružený ke streamu|
|[_flushall](../c-runtime-library/reference/flushall.md)|Vyprázdnit všechny streamy do vyrovnávací paměti nebo úložného zařízení|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Otevřít Stream|
|[fprintf –, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|Zápis formátovaných dat do streamu|
|[fputc, fputwc](../c-runtime-library/reference/fputc-fputwc.md)|Zápis znaku do datového proudu (verze funkcí **putc** a **putwc**)|
|[_fputchar, _fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|Zápis znaku do **stdout** (verze funkcí **putchar** a **putwchar**)|
|[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)|Zapsat řetězec do streamu|
|[fread](../c-runtime-library/reference/fread.md)|Čtení neformátovaných dat ze streamu|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md) [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Změna přiřazení ukazatele datového proudu **souboru** do nového souboru nebo zařízení|
|[Fscanf, fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [fscanf_s, _fscanf_s_l, fwscanf_s _fwscanf_s_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|Čtení formátovaných dat ze streamu|
|[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|Přesunout pozici souboru do daného umístění|
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|Nastavit indikátor pozice datového proudu|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Otevření streamu se sdílením souborů|
|[ftell, _ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|Získat aktuální pozici souboru|
|[fwrite](../c-runtime-library/reference/fwrite.md)|Zápis neformátovaných datových položek do streamu|
|[getc, getwc](../c-runtime-library/reference/getc-getwc.md)|Přečíst znak ze streamu (verze makra **fgetc** a **fgetwc**)|
|[getchar, getwchar](../c-runtime-library/reference/getc-getwc.md)|Přečíst znak ze **standardního vstupu** (verze makra **fgetchar** a **fgetwchar**)|
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|Vrátí počet současně otevřených souborů povolených na úrovni vstupu a výstupu datového proudu.|
|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|Načíst řádek ze **standardního vstupu**|
|[_getw](../c-runtime-library/reference/getw.md)|Číst binární **celé číslo** ze streamu|
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|Zápis formátovaných dat do **stdout**|
|[putc, putwc](../c-runtime-library/reference/putc-putwc.md)|Zápis znaku do datového proudu (verze makra **fputc** a **fputwc**)|
|[putchar, putwchar](../c-runtime-library/reference/putc-putwc.md)|Zapsat znak do **stdout** (verze makra **fputchar** a **fputwchar**)|
|[puts, _putws](../c-runtime-library/reference/puts-putws.md)|Zapsat řádek do streamu|
|[_putw](../c-runtime-library/reference/putw.md)|Zapsat binární **celé číslo** do proudu|
|[rewind](../c-runtime-library/reference/rewind.md)|Přesunout pozici souboru na začátek streamu|
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|Odebrat dočasné soubory vytvořené nástrojem **tmpfile**|
|[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|Čtení formátovaných dat ze **standardního vstupu**|
|[setbuf](../c-runtime-library/reference/setbuf.md)|Řízení vyrovnávací paměti datového proudu|
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|Nastavte maximální počet současně otevřených souborů na úrovni vstupu a výstupu datového proudu.|
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|Velikost vyrovnávací paměti datového proudu a vyrovnávací paměti pro řízení|
|[_snprintf, _snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), [_snprintf_s, _snprintf_s_l, _snwprintf_s](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md) _snwprintf_s_l|Zapsat naformátovaná data o zadané délce do řetězce|
|[_snscanf, _snwscanf](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md), [_snscanf_s, _snscanf_s_l, _snwscanf_s](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md) _snwscanf_s_l|Čtení formátovaných dat o zadané délce ze standardního vstupního streamu.|
|[sprintf –, swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), [sprintf_s, _sprintf_s_l, swprintf_s _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|Zápis formátovaných dat do řetězce|
|[sscanf, swscanf](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md), [sscanf_s, _sscanf_s_l, swscanf_s _swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|Čtení formátovaných dat z řetězce|
|[_tempnam _wtempnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|Vygenerovat dočasný název souboru v daném adresáři|
|[tmpfile](../c-runtime-library/reference/tmpfile.md), [tmpfile_s](../c-runtime-library/reference/tmpfile-s.md)|Vytvořit dočasný soubor|
|[tmpnam, _wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [tmpnam_s, _wtmpnam_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|Generovat dočasný název souboru|
|[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|Zpětné vložení znaku do streamu|
|[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md), [_vcprintf_s, _vcprintf_s_l, _vcwprintf_s](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md) _vcwprintf_s_l|Zapište formátovaná data do konzoly.|
|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vfprintf_s, _vfprintf_s_l, vfwprintf_s _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|Zápis formátovaných dat do streamu|
|[vprintf –, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), [vprintf_s, _vprintf_s_l, vwprintf_s _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|Zápis formátovaných dat do **stdout**|
|[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md), [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|Zapsat naformátovaná data o zadané délce do vyrovnávací paměti|
|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md), [vsprintf_s, _vsprintf_s_l, vswprintf_s _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|Zápis formátovaných dat do vyrovnávací paměti|

Když se program začne spouštět, spouštěcí kód automaticky otevře několik datových proudů: standardní vstup (odkazoval na **stdin**), standardní výstup (odkazoval na **stdout**) a standardní chybu (odkazovalo na **stderr**). Tyto streamy se ve výchozím nastavení přesměrují do konzoly (klávesnice a obrazovky). Pomocí **freopen** můžete přesměrovat **stdin**, **stdout**nebo **stderr** na soubor na disku nebo zařízení.

Soubory otevřené pomocí rutin streamování se ve výchozím nastavení uloží do vyrovnávací paměti. Funkce **stdout** a **stderr** jsou vyprázdněny pokaždé, když jsou úplné nebo, pokud píšete do znakového zařízení, po každém volání knihovny. Pokud se program neobvykle ukončí, výstupní vyrovnávací paměti nemusí být vyprázdněny, což vede ke ztrátě dat. Pomocí **fflush** nebo **_flushall** zajistěte, aby byla vyrovnávací paměť přidružená k zadanému souboru nebo všechny otevřené vyrovnávací paměti vyprázdněna v operačním systému, který může ukládat data do mezipaměti před jejich zápisem na disk. Funkce potvrzení na disk zajišťuje, že obsah vyprázdněné vyrovnávací paměti nebude ztracen v případě selhání systému.

Existují dva způsoby, jak zapsat obsah vyrovnávací paměti na disk:

- Připojte se k souboru COMMODE. OBJ pro nastavení globálního příznaku potvrzení. Výchozí nastavení globálního příznaku je **n**pro možnost bez potvrzení.

- Nastavte příznak Mode na **c** s **fopen** nebo **_fdopen**.

Každý soubor, který se konkrétně otevřel buď pomocí příznaku **c** , nebo **n** , se chová podle příznaku bez ohledu na stav příznaku globálního potvrzení/nepotvrzení.

Pokud program neukončí explicitně datový proud, je datový proud automaticky uzavřen při ukončení programu. Měli byste ale zavřít Stream, když se s ním dokončí program, protože počet datových proudů, které se dají otevřít najednou, je omezený. Informace o tomto limitu najdete v tématu [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) .

Vstup může sledovat výstup přímo pouze s přidaným voláním **fflush** nebo do funkce umísťování souborů (**fseek**, **fsetpos**nebo **Rewind**). Výstup může následovat za vstup bez započetí volání funkce umístění souboru, pokud vstupní operace narazí na konec souboru.

## <a name="see-also"></a>Viz také

[Vstup a výstup](../c-runtime-library/input-and-output.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
