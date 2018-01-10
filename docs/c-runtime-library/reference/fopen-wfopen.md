---
title: "fopen –, _wfopen – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
caps.latest.revision: "56"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 01558dfa6b28f10746c1487384bad44768b5877e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fopen-wfopen"></a>fopen, _wfopen
Otevře soubor. Bezpečnější verze těchto funkcí, které provádět další parametr ověření a návratové kódy chyb jsou k dispozici. v tématu [fopen_s, _wfopen_s](../../c-runtime-library/reference/fopen-s-wfopen-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FILE *fopen(   
   const char *filename,  
   const char *mode   
);  
FILE *_wfopen(   
   const wchar_t *filename,  
   const wchar_t *mode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Název souboru.  
  
 `mode`  
 Druh přístupu, který je povolený.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrací ukazatel na otevření souboru. Hodnota ukazatele null znamená chybu. Pokud `filename` nebo `mode` je `NULL` nebo prázdný řetězec, tyto funkce aktivovat obslužné rutiny neplatný parametr, který je popsaný v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `NULL` a nastavte `errno` k `EINVAL`.  
  
 Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `fopen` Funkce otevře soubor, který je zadán `filename`. Ve výchozím nastavení, úzké `filename` řetězec interpretována pomocí codepage ANSI (CP_ACP). V aplikacích Windows Desktop toto můžete změnit na znakovou stránku OEM (CP_OEMCP) pomocí [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534\(v=vs.85\).aspx) funkce. Můžete použít [AreFileApisANSI](https://msdn.microsoft.com/library/windows/desktop/aa363781\(v=vs.85\).aspx) funkce, která má-li určit, zda `filename` interpretována pomocí ANSI nebo systémová znaková stránka výchozí OEM. `_wfopen`široká charakterová verze `fopen`; argumenty, které mají `_wfopen` jsou široká charakterová řetězce. V opačném `_wfopen` a `fopen` chovají stejně jako. Právě pomocí `_wfopen` nemá vliv na programové znaková sada, která se používá v datový proud souboru.  
  
 `fopen`přijímá cesty, které jsou platné v systému souborů v okamžiku spuštění; `fopen` přijímá UNC cesty a cesty, které zahrnují mapované síťové jednotky, dokud systém, který spustí kód má přístup ke sdílené složce nebo mapované jednotky v době spuštění. Když vytvoříte cesty pro `fopen`, ujistěte se, že jednotky, cesty nebo sdílené síťové složky budou dostupné v prostředí pro spuštění. Můžete použít buď lomítka (/) nebo zpětná lomítka (\\) jako oddělovače adresáře v cestě.  
  
 Vždy Zkontrolujte návratovou hodnotu zobrazíte, zda má ukazatel hodnotu NULL, před provedením jakékoli další operace na souboru. Pokud dojde k chybě, globální proměnná `errno` nastavena a může sloužit k získat informace o konkrétní chybě. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="unicode-support"></a>Podpora kódování Unicode  
 `fopen`podporuje kódování Unicode souborů datových proudů. Otevřete soubor Unicode, předávání `ccs` příznak, který určuje požadovanou kódování `fopen`, a to takto.  
  
 `FILE *fp = fopen("newfile.txt", "rt+, ccs=encoding");`  
  
 Povolené hodnoty `encoding` jsou `UNICODE`, `UTF-8`, a `UTF-16LE`.  
  
 Po otevření souboru v režimu Unicode vstupní funkce převede data, která je pro čtení ze souboru do UTF-16 data uložená jako typ `wchar_t`. Funkce, které zapisovat do souboru otevřeného v režimu Unicode očekávat vyrovnávací paměti, které obsahují data ve formátu UTF-16 uložené jako typ `wchar_t`. Pokud soubor zakódován pomocí kódování UTF-8, je při je zapsán a kódování UTF-8 obsah souboru je přeložit na UTF-16, když je pro čtení dat ve formátu UTF-16 přeložit na UTF-8. Pokus o čtení nebo zápisu lichý počet bajtů v režimu příčiny kódování Unicode [ověření parametru](../../c-runtime-library/parameter-validation.md) chyby. Číst nebo zapisovat data, která je uložená v programu jako UTF-8, použijte místo režim Unicode režim textových nebo binárních souborů. Jste zodpovědní za jakékoli požadované kódování překlad.  
  
 Pokud soubor již existuje a je otevřen pro čtení nebo připojením, bajtů pořadí značky (Kusovníku), pokud je k dispozici v souboru Určuje kódování. Kódování BOM má přednost před přes kódování, která je zadána `ccs` příznak. `ccs` Kódování se používá pouze pokud je k dispozici žádné BOM nebo že soubor byl nový soubor.  
  
> [!NOTE]
>  Detekce BOM platí jenom pro soubory, které jsou otevřeny v režimu Unicode (tedy pomocí předání `ccs` příznak).  
  
 Následující tabulka shrnuje režimů, které se používají pro různé `ccs` příznaky zadané `fopen` a značky pořadí bajtů v souboru.  
  
### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Použít na základě kódování ccs příznak a BOM  
  
|`ccs`Příznak|Žádné BOM (nebo nový soubor)|BOM: UTF-8|BOM: UTF-16|  
|----------------|----------------------------|-----------------|------------------|  
|`UNICODE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
|`UTF-8`|`UTF-8`|`UTF-8`|`UTF-16LE`|  
|`UTF-16LE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
  
 Soubory otevřena pro zápis v režimu Unicode mají Kusovník zapisovat do nich automaticky.  
  
 Pokud `mode` je "`a, ccs=<encoding>`", `fopen` poprvé pokusí otevřít soubor pomocí pro čtení i zápis. Pokud to úspěšné, funkce přečte BOM určete kódování pro soubor; Pokud se to nezdaří, využívá funkce výchozí kódování pro soubor. V obou případech `fopen` se pak znovu otevřete soubor pomocí přístup jen pro zápis. (To se vztahuje na `a` režimu pouze tak, aby `a+` režimu.)  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfopen`|`fopen`|`fopen`|`_wfopen`|  
  
 Řetězec znaků `mode` Určuje typ přístupu, který je požadovaný pro soubor, následujícím způsobem.  
  
 `"r"`  
 Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, `fopen` volání selže.  
  
 `"w"`  
 Otevře se prázdný soubor pro zápis. Pokud je daný soubor existuje, její obsah se způsobem zničena.  
  
 `"a"`  
 Otevře pro zápis na konec souboru (připojení) bez odebrání značky end souboru (EOF) před nová data jsou zapsána do souboru. Pokud neexistuje, vytvoří soubor.  
  
 `"r+"`  
 Otevře pro čtení i zápis. Soubor musí existovat.  
  
 `"w+"`  
 Otevře se prázdný soubor pro čtení i zápis. Pokud soubor existuje, její obsah se způsobem zničena.  
  
 `"a+"`  
 Otevře pro čtení a připojením. Připojování operaci zahrnuje odebrání značky EOF před nová data jsou zapsána do souboru. Po dokončení zápisu, nedojde k obnovení EOF značky. Pokud neexistuje, vytvoří soubor.  
  
 Při otevření souboru s použitím `"a"` přistupovat typu nebo `"a+"` přístup k typu, všechny zápisu operace probíhají na konci souboru. Ukazatele souboru můžete změnit jejich umístění pomocí `fseek` nebo `rewind`, ale je vždy přesunuta zpět na konec souboru před všechny zápisu operace. Proto nelze přepsat stávající data.  
  
 `"a"` Režimu neodebere EOF značky, než se připojí k souboru. Po připojení došlo k chybě, MS-DOS typ příkazu se zobrazí pouze data až původní EOF značky a není žádná data připojen k souboru. Předtím, než se připojí k souboru `"a+"` režimu odebrat konce souboru značky. Po připojení, zobrazí příkaz MS-DOS typ všechna data v tomto souboru. `"a+"` Režim je vyžadován pro připojení do datového proudu souboru, který je byla ukončena s CTRL + Z EOF značky.  
  
 Když `"r+"`, `"w+"`, nebo `"a+"` byl zadán typ přístupu, je povoleno čtení i zápis (soubor říká, že je třeba otevřít pro "update"). Ale po přepnutí z čtení pro zápis vstupní operaci dojde EOF značky. Pokud není k dispozici žádné konce souboru, je nutné použít použité volání funkce umístění souboru. Funkce umísťovací souboru jsou `fsetpos`, `fseek`, a `rewind`. Po přepnutí z zápis do čtení, je nutné použít použité volání buď `fflush` nebo do souboru umístění funkce.  
  
 Kromě předchozích hodnoty, tyto znaky můžete připojit k `mode` k určení režim překladu pro znaky nového řádku.  
  
 `t`  
 Otevřete v textu (přeložit) režimu. V tomto režimu CTRL + Z interpretována jako znak EOF na vstup. V souborech, které jsou otevřené pro čtení/zápis pomocí `"a+"`, `fopen` kontroluje CTRL + Z na konci souboru a odstraní ji, pokud je to možné. To je provést, protože používá `fseek` a `ftell` v souboru, který může způsobit, že na konci CTRL + Z přesuňte `fseek` chovat nesprávně blíží konec souboru.  
  
 V režimu textových znaků CR vrátit-konce řádku kombinace jsou převedeny do jednoho přečtené na vstup a znaky konce řádku jsou převedeny na kombinace znaků CR vrátit-konce řádku na výstup. Pokud funkce datového proudu I/O Unicode funguje v režimu textových (výchozí), zdroj nebo cílový datový proud předpokládá se, že posloupnosti vícebajtových znaků. Proto funkce vstupního datového proudu Unicode převést více-bajtové znaky na široké znaky (jako Pokud voláním `mbtowc` funkce). Ze stejného důvodu, funkce výstup datového proudu Unicode převést více-bajtové znaky široké znaky (jako Pokud voláním `wctomb` funkce).  
  
 `b`  
 Otevřete v binárním režimu (nepřeložený); jsou potlačovány překlady zahrnující znaky CR a konce řádku.  
  
 Pokud `t` nebo `b` není uveden v `mode`, je výchozí režim překladu definované globální proměnná [_fmode –](../../c-runtime-library/fmode.md). Pokud `t` nebo `b` je předponou argument, funkce selže a vrátí `NULL`.  
  
 Další informace o tom, jak používat textovém a binárním režimu v kódování Unicode a vícebajtové datového proudu I/O najdete v tématu [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [vstupně-výstupní datový proud Unicode v textovém a binárním režimu](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).  
  
 `c`  
 Povolit příznak potvrzení pro přidruženého `filename` tak, aby obsah souboru vyrovnávací paměti je zapsán přímo na disk v případě buď `fflush` nebo `_flushall` je volána.  
  
 `n`  
 Resetujte příznak potvrzení pro přidruženého `filename` na "Ne potvrzováním." Toto nastavení je výchozí. Pokud jste váš program s COMMODE.OBJ také přepisuje příznak globálního potvrzení. Globální potvrzení příznak výchozí hodnota je "Ne potvrzováním" Pokud explicitně propojit váš program s COMMODE. OBJ (viz [možnosti odkazů](../../c-runtime-library/link-options.md)).  
  
 `N`  
 Určuje, že soubor není zděděna podřízené procesy.  
  
 `S`  
 Určuje, že ukládání do mezipaměti je optimalizovaná pro, ale není omezen na, sekvenční přístup z disku.  
  
 `R`  
 Určuje, že ukládání do mezipaměti je optimalizovaná pro, ale není omezena na náhodný přístup z disku.  
  
 `T`  
 Určuje soubor jako dočasnou. Pokud je to možné, není vyprázdněných na disk.  
  
 `D`  
 Určuje soubor jako dočasnou. Odstraní se při zavření posledního ukazatele souboru.  
  
 `ccs=ENCODING`  
 Určuje programové znakové sady (`UTF-8`, `UTF-16LE`, nebo `UNICODE`) pro tento soubor. Ponechejte neurčené, pokud chcete kódování ANSI.  
  
 Platné znaky pro `mode` řetězec, který se používá v `fopen` a `_fdopen` odpovídají `oflag` argumenty, které se používají v [_Otevřít](../../c-runtime-library/reference/open-wopen.md) a [_sopen –](../../c-runtime-library/reference/sopen-wsopen.md), a to takto.  
  
|Znaky v řetězci režimu|Ekvivalentní `oflag` hodnota`_open`/`_sopen`|  
|-------------------------------|----------------------------------------------------|  
|`a`|`_O_WRONLY &#124; _O_APPEND`(obvykle `_O_WRONLY &#124; _O_CREAT &#124; _O_APPEND`)|  
|`a+`|`_O_RDWR &#124; _O_APPEND`(obvykle `_O_RDWR &#124; _O_APPEND &#124; _O_CREAT` )|  
|`r`|`_O_RDONLY`|  
|`r+`|`_O_RDWR`|  
|`w`|`_O_WRONLY`(obvykle `_O_WRONLY &#124; _O_CREAT &#124; _O_TRUNC`)|  
|`w+`|`_O_RDWR`(obvykle `_O_RDWR &#124; _O_CREAT &#124; _O_TRUNC`)|  
|`b`|`_O_BINARY`|  
|`t`|`_O_TEXT`|  
|`c`|Žádné|  
|`n`|Žádné|  
|`S`|`_O_SEQUENTIAL`|  
|`R`|`_O_RANDOM`|  
|`T`|`_O_SHORTLIVED`|  
|`D`|`_O_TEMPORARY`|  
|`ccs=UNICODE`|`_O_WTEXT`|  
|`ccs=UTF-8`|`_O_UTF8`|  
|`ccs=UTF-16LE`|`_O_UTF16`|  
  
 Pokud používáte `rb` režimu, není nutné portu kódu a očekávají čtení většinu velký soubor, nebo nejsou zajímá výkon sítě, můžete také zvážit, zda použití paměti mapovat soubory Win32 jako možnost.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`fopen`|\<stdio.h >|  
|`_wfopen`|\<stdio.h > nebo \<wchar.h >|  
  
 `_wfopen`představuje rozšíření Microsoft. Další informace o kompatibilitě najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
 `c`, `n`, `t`, `S`, `R`, `T`, A `D` `mode` možnosti jsou rozšíření Microsoft pro `fopen` a `_fdopen` a kde by se neměla používat Přenositelnost ANSI se požaduje.  
  
## <a name="example"></a>Příklad  
 Následující program otevře dva soubory.  Používá `fclose` zavřete první soubor a `_fcloseall` zavřete všechny zbývající soubory.  
  
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
  
## <a name="example"></a>Příklad  
 Následující program vytvoří soubor (nebo jeden přepíše, pokud existuje), v textovém režimu s kódování Unicode.  Pak zapíše dva řetězce do souboru a zavře soubor. Výstup je soubor s názvem _wfopen_test.xml, který obsahuje data z části výstup.  
  
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
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [fclose –, _fcloseall –](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen –, _wfdopen –](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [ferror –](../../c-runtime-library/reference/ferror.md)   
 [_fileno –](../../c-runtime-library/reference/fileno.md)   
 [freopen –, _wfreopen –](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode –](../../c-runtime-library/reference/setmode.md)   
 [_sopen, _wsopen](../../c-runtime-library/reference/sopen-wsopen.md)