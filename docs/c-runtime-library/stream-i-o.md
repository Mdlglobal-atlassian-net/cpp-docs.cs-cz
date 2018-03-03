---
title: Stream I-O | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- I/O routines, stream I/O
- I/O [CRT], stream
- stream I/O
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6a0c3fe1a85028f4b4220f8e2f111afa1012121
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="stream-io"></a>I/O proudu
Tyto funkce zpracovávat data v různých velikostí a formátů z jedné znaky na velké datové struktury. Obsahují taky ukládání do vyrovnávací paměti, což může zlepšit výkon. Výchozí velikost vyrovnávací paměti datového proudu je 4 kB. Tyto rutiny ovlivní pouze vyrovnávací paměti vytvořené rutiny běhové knihovny a mít žádný vliv na vyrovnávací paměti vytvořené operačního systému.  
  
### <a name="stream-io-routines"></a>Datový proud vstupně-výstupní rutiny  
  
|Rutina|Použití|  
|-------------|---------|  
|[clearerr –](../c-runtime-library/reference/clearerr.md), [clearerr_s –](../c-runtime-library/reference/clearerr-s.md)|Označení chyb zrušte pro datový proud|  
|[fclose –](../c-runtime-library/reference/fclose-fcloseall.md)|Zavřít datový proud|  
|[_fcloseall –](../c-runtime-library/reference/fclose-fcloseall.md)|Zavřete všechny otevřené datové proudy s výjimkou `stdin`, `stdout`, a`stderr`|  
|[_fdopen –, wfdopen –](../c-runtime-library/reference/fdopen-wfdopen.md)|Datový proud přidružit popisovače souborů otevřete souboru|  
|[feof](../c-runtime-library/reference/feof.md)|Test pro konec souboru na datový proud|  
|[ferror](../c-runtime-library/reference/ferror.md)|Test došlo k chybě v proudu|  
|[fflush](../c-runtime-library/reference/fflush.md)|Vyprázdnění datového proudu do vyrovnávací paměti nebo zařízení úložiště|  
|[fgetc, fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|Číst znak z datového proudu (funkce verze `getc` a `getwc`)|  
|[_fgetchar, _fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|Čtení znaků z `stdin` (funkce verze `getchar` a `getwchar`)|  
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|Získat označení pozice datového proudu|  
|[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)|Řetězec pro čtení z datového proudu|  
|[_fileno](../c-runtime-library/reference/fileno.md)|Získání popisovače souborů, které jsou přidružené k datového proudu|  
|[_flushall](../c-runtime-library/reference/flushall.md)|Vyprázdnit všechny datové proudy pro vyrovnávací paměť nebo úložiště zařízení|  
|[fopen –, _wfopen –](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Otevřít datový proud|  
|[fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fprintf_s –, _fprintf_s_l –, fwprintf_s –, _fwprintf_s_l –](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|Zápis formátovaných dat do datového proudu|  
|[fputc, fputwc](../c-runtime-library/reference/fputc-fputwc.md)|Zápis do datového proudu znak (funkce verze `putc` a `putwc`)|  
|[_fputchar, _fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|Zápis znaků do `stdout` (funkce verze `putchar` a `putwchar`)|  
|[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)|Zápis řetězců do datového proudu|  
|[fread](../c-runtime-library/reference/fread.md)|Číst neformátovaná data z datového proudu|  
|[freopen –, _wfreopen –](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s –, _wfreopen_s –](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Přiřazení `FILE` datového proudu ukazatel na nový soubor nebo zařízení|  
|[fscanf –, fwscanf –](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [fscanf_s –, _fscanf_s_l –, fwscanf_s –, _fwscanf_s_l –](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|Čtení formátovaných dat z datového proudu|  
|[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|Pozice souboru přesunout na zadané umístění|  
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|Označení pozice sadu datového proudu|  
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Otevřít datový proud s sdílení souborů|  
|[ftell, _ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|Získat aktuální pozice souboru|  
|[fwrite](../c-runtime-library/reference/fwrite.md)|Zápis položky neformátovaná data do datového proudu|  
|[getc, getwc](../c-runtime-library/reference/getc-getwc.md)|Číst znak z datového proudu (verze makro `fgetc` a `fgetwc`)|  
|[getchar, getwchar](../c-runtime-library/reference/getc-getwc.md)|Čtení znaků z `stdin` (verze makro `fgetchar` a `fgetwchar`)|  
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|Vrátí počet současně otevřených souborů, které jsou v úrovni vstupně-výstupní datový proud.|  
|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|Načíst řádek z`stdin`|  
|[_getw](../c-runtime-library/reference/getw.md)|Číst binární `int` z datového proudu|  
|[printf _printf_l –, wprintf, _wprintf_l –](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),[printf_s –, _printf_s_l –, wprintf_s –, _wprintf_s_l –](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|Zápis formátovaných dat do`stdout`|  
|[putc, putwc](../c-runtime-library/reference/putc-putwc.md)|Zápis znaků do datového proudu (verze makro `fputc` a `fputwc`)|  
|[putchar, putwchar](../c-runtime-library/reference/putc-putwc.md)|Zápis znaků do `stdout` (verze makro `fputchar` a `fputwchar`)|  
|[puts, _putws](../c-runtime-library/reference/puts-putws.md)|Zapsat řádek do datového proudu|  
|[_putw](../c-runtime-library/reference/putw.md)|Zápis binární `int` do datového proudu|  
|[rewind](../c-runtime-library/reference/rewind.md)|Přesun pozice souboru začátek datového proudu|  
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|Odeberte dočasné soubory vytvořené serverem`tmpfile`|  
|[scanf, _scanf_l –, wscanf, _wscanf_l –](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),[scanf_s –, _scanf_s_l –, wscanf_s –, _wscanf_s_l –](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|Čtení formátovaných dat z`stdin`|  
|[setbuf](../c-runtime-library/reference/setbuf.md)|Ovládací prvek datového proudu do vyrovnávací paměti|  
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|Nastavte maximální počet současně otevřených souborů na vstupně-výstupní datový proud úroveň.|  
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|Ovládací prvek datového proudu do vyrovnávací paměti a velikost vyrovnávací paměti|  
|[_snprintf –, _snwprintf –](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), [_snprintf_s –, _snprintf_s_l –, _snwprintf_s –, _snwprintf_s_l –](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|Zápis formátovaných dat zadané délky řetězce|  
|[_snscanf –, _snwscanf –](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md), [_snscanf_s –, _snscanf_s_l –, _snwscanf_s –, _snwscanf_s_l –](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|Čtení formátovaných dat o zadané délce z standardní vstupní proud.|  
|[sprintf, swprintf –](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), [sprintf_s –, _sprintf_s_l –, swprintf_s –, _swprintf_s_l –](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|Zápis formátovaných dat do řetězce|  
|[sscanf –, swscanf –](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md), [sscanf_s –, _sscanf_s_l –, swscanf_s –, _swscanf_s_l –](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|Čtení formátovaných dat z řetězce|  
|[_tempnam –, _wtempnam –](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|Generovat dočasný název souboru v zadané adresáře|  
|[tmpfile –](../c-runtime-library/reference/tmpfile.md), [tmpfile_s –](../c-runtime-library/reference/tmpfile-s.md)|Vytvořit dočasný soubor|  
|[tmpnam –, _wtmpnam –](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md), [tmpnam_s –, _wtmpnam_s –](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|Generovat dočasný název souboru|  
|[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|Znak nabízené zpět do datového proudu|  
|[_vcprintf –, _vcwprintf –](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md), [_vcprintf_s –, _vcprintf_s_l –, _vcwprintf_s –, _vcwprintf_s_l –](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|Zápis formátovaných dat do konzoly.|  
|[vfprintf –, vfwprintf –](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vfprintf_s –, _vfprintf_s_l –, vfwprintf_s –, _vfwprintf_s_l –](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|Zápis formátovaných dat do datového proudu|  
|[vprintf –, vwprintf –](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), [vprintf_s –, _vprintf_s_l –, vwprintf_s –, _vwprintf_s_l –](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|Zápis formátovaných dat do`stdout`|  
|[_vsnprintf –, _vsnwprintf –](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md), [vsnprintf_s –, _vsnprintf_s –, _vsnprintf_s_l –, _vsnwprintf_s –, _vsnwprintf_s_l –](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|Formátovaná data o zadané délce zapsat do vyrovnávací paměti|  
|[vsprintf –, vswprintf –](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md), [vsprintf_s –, _vsprintf_s_l –, vswprintf_s –, _vswprintf_s_l –](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|Formátovaná data zapsat do vyrovnávací paměti|  
  
 Pokud program zahájí spuštění, spuštění kódu automaticky otevře několik datových proudů: standardní vstup (na kterou odkazuje `stdin`), standardního výstupního (na kterou odkazuje `stdout`) a standardní cíl chybové (na kterou odkazuje `stderr`). Tyto datové proudy jsou směrované do konzoly (klávesnice a obrazovky) ve výchozím nastavení. Použití `freopen` přesměrování `stdin`, `stdout`, nebo `stderr` soubor na disku nebo do zařízení.  
  
 Soubory otevřené pomocí rutiny datového proudu jsou ve výchozím nastavení do vyrovnávací paměti. `stdout` a `stderr` funkce jsou vyprázdněny, vždy, když jsou úplné nebo, pokud píšete znak zařízení po každém volání knihovny. Pokud program ukončí neobvyklým způsobem, výstupní vyrovnávací paměti nesmí vyprázdněna, což vede ke ztrátě dat. Použití `fflush` nebo `_flushall` zajistit, že je spojené s zadaný soubor vyrovnávací paměti nebo vyrovnávací paměti, všechny otevřené vyprazdňuje na operační systém, který může ukládat do mezipaměti dat před zápisem na disk. Funkce potvrzení na disku zajišťuje, že obsah vyprázdněn vyrovnávací nebyly ztraceny v případě selhání systému.  
  
 Existují dva způsoby, jak zapsat obsah vyrovnávací paměti na disk:  
  
-   Propojit se souborem COMMODE. OBJ k nastavení příznaku globálního potvrzení. Je výchozí nastavení pro globální příznak `n`, "potvrzení č."  
  
-   Nastavte příznak režimu na `c` s `fopen` nebo `_fdopen`.  
  
 Všechny soubory otevřené konkrétně se buď `c` nebo `n` příznak chová podle příznak, bez ohledu na stav příznak globální potvrzení a ne potvrdit.  
  
 Pokud váš program není explicitně Zavřít datový proud, do datového proudu je automaticky uzavřít, když program ukončí. Ale zavřete datový proud po dokončení vašeho programu s ním, jako je omezený počet datových proudů, které může být najednou otevřený. V tématu [_setmaxstdio –](../c-runtime-library/reference/setmaxstdio.md) informace na toto omezení.  
  
 Vstup můžete postupovat podle výstup přímo pouze s použité volání `fflush` nebo funkci umístění souboru (`fseek`, `fsetpos`, nebo `rewind`). Výstupu můžete podle vstup bez použité volání funkce umístění souboru, pokud vstupní operaci zaznamená konec souboru.  
  
## <a name="see-also"></a>Viz také  
 [Vstup a výstup](../c-runtime-library/input-and-output.md)   
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)