---
title: fopen_s, _wfopen_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "41"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 49a884b8ae4ea34c02a0ca57563077add4d9d6fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fopens-wfopens"></a>fopen_s, _wfopen_s
Otevře soubor. Tyto verze nástroje [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 [out]`pFile`  
 Ukazatel na ukazatele souboru, který se zobrazí ukazatel na otevřený soubor.  
  
 [v]`filename`  
 Název souboru.  
  
 [v]`mode`  
 Typ přístupu povolena.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěšného; Kód chyby při selhání. V tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o tyto kódy chyb.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`pFile`|`filename`|`mode`|Návratová hodnota|Obsah`pFile`|  
|-------------|----------------|------------|------------------|------------------------|  
|`NULL`|všechny|všechny|`EINVAL`|Beze změny|  
|všechny|`NULL`|všechny|`EINVAL`|Beze změny|  
|všechny|všechny|NULL|`EINVAL`|Beze změny|  
  
## <a name="remarks"></a>Poznámky  
 Soubory, které jsou otevřené podle `fopen_s` a `_wfopen_s` nejsou lze sdílet. Pokud budete vyžadovat, aby byl soubor lze sdílet, použijte [_fsopen –, _wfsopen –](../../c-runtime-library/reference/fsopen-wfsopen.md) s příslušnou sdílení konstanta režimu – například `_SH_DENYNO` pro sdílení pro čtení a zápis.  
  
 `fopen_s` Funkce otevře soubor, který je zadán `filename`. `_wfopen_s`široká charakterová verze `fopen_s`; argumenty, které mají `_wfopen_s` jsou široká charakterová řetězce. `_wfopen_s`a `fopen_s` chovat jinak shodně.  
  
 `fopen_s`přijímá cesty, které jsou platné v systému souborů v okamžiku spuštění; Přijal UNC cesty a cesty, které zahrnují namapované síťové jednotky `fopen_s` tak dlouho, dokud systém, který spouští kód má přístup ke sdílené složce nebo namapované síťové jednotky při spuštění. Když vytvoříte cesty pro `fopen_s`, nevytvářejte předpoklady o dostupnosti jednotek, cesty, nebo síťové sdílené složky v prostředí pro spuštění. Můžete použít buď lomítka (/) nebo zpětná lomítka (\\) jako oddělovače adresáře v cestě.  
  
 Tyto funkce ověřit jejich parametrů. Pokud `pFile`, `filename`, nebo `mode` je ukazatel s hodnotou null, tyto funkce vygeneruje výjimka neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).  
  
 Vždy Zkontrolujte návratovou hodnotu chcete zobrazit, pokud bylo úspěšné funkce před provedením jakékoli další operace na souboru. Pokud dojde k chybě, je vrácen kód chyby a globální proměnné `errno` nastavena. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="unicode-support"></a>Podpora kódování Unicode  
 `fopen_s`podporuje kódování Unicode souborů datových proudů. Chcete-li otevřít nové nebo existující souboru Unicode, předat `ccs` příznak, který určuje požadovanou kódování `fopen_s`:  
  
 `fopen_s(&fp, "newfile.txt", "rw, ccs=`*kódování*`");`  
  
 Povolené hodnoty *kódování* jsou `UNICODE`, `UTF-8`, a `UTF-16LE`. Pokud existuje není zadaná žádná hodnota pro *kódování*, `fopen_s` používá kódování ANSI.  
  
 Pokud soubor již existuje a je otevřen pro čtení nebo připojením, bajtů pořadí značky (Kusovníku), pokud je k dispozici v souboru Určuje kódování. Kódování BOM má přednost před přes kódování, která je zadána `ccs` příznak. `ccs` Kódování je použít pouze v případě žádné BOM je přítomen nebo pokud je soubor nový soubor.  
  
> [!NOTE]
>  Detekce BOM platí jenom pro soubory, které jsou otevřeny v režimu Unicode; To znamená, službou předávání `ccs` příznak.  
  
 Následující tabulka shrnuje pro různé režimy `ccs` příznaky, které jsou uvedeny k `fopen_s` a značky pořadí bajtů v souboru.  
  
### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Použít na základě kódování ccs příznak a BOM  
  
|`ccs`Příznak|Žádné BOM (nebo nový soubor)|BOM: UTF-8|BOM: UTF-16|  
|----------------|----------------------------|-----------------|------------------|  
|`UNICODE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
|`UTF-8`|`UTF-8`|`UTF-8`|`UTF-16LE`|  
|`UTF-16LE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
  
 Soubory, které jsou otevřené pro zápis v režimu Unicode mají Kusovník zapisovat do nich automaticky.  
  
 Pokud `mode` je "a, ccs =*kódování*", `fopen_s` poprvé pokusí otevřít soubor s přístupem pro čtení i zápis. V případě úspěšného funkce přečte BOM určete kódování pro soubor; Pokud je úspěšné, funkce používá výchozí kódování pro soubor. V obou případech `fopen_s` znovu otevře soubor s přístupem jen pro zápis. (To se vztahuje na `a` jen není režimu `a+`.)  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfopen_s`|`fopen_s`|`fopen_s`|`_wfopen_s`|  
  
 Řetězec znaků `mode` Určuje typ přístupu, který je požadovaný pro soubor, následujícím způsobem.  
  
 `"r"`  
 Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, `fopen_s` volání selže.  
  
 `"w"`  
 Otevře se prázdný soubor pro zápis. Pokud soubor existuje, její obsah se způsobem zničena.  
  
 `"a"`  
 Otevře pro zápis na konec souboru (připojení) bez odebrání značky EOF před zápisem nová data do souboru. Pokud neexistuje, vytvoří soubor.  
  
 `"r+"`  
 Otevře pro čtení i zápis. (Soubor musí existovat.)  
  
 `"w+"`  
 Otevře se prázdný soubor pro čtení i zápis. Pokud soubor existuje, její obsah se způsobem zničena.  
  
 `"a+"`  
 Otevře pro čtení a připojením. Připojování operaci zahrnuje odebrání značky EOF před nová data jsou zapsána do souboru a značky EOF obnovení po dokončení zápisu. Pokud neexistuje, vytvoří soubor.  
  
 Při otevření souboru s použitím `"a"` nebo `"a+"` přístup k typu, všechny zápisu operace probíhají na konci souboru. Ukazatele souboru můžete změnit jejich umístění pomocí `fseek` nebo `rewind`, ale je vždy přesunuta zpět na konec souboru před všechny zápisu operace se provádí tak, aby existující data nelze přepsat.  
  
 `"a"` Režimu neodebere značky EOF před připojením k souboru. Po připojení došlo k chybě, MS-DOS typ příkazu se zobrazí pouze data až původní EOF značky a není žádná data, která je připojena k souboru. `"a+"` Režimu odebrat značky EOF před připojením k souboru. Po připojení, zobrazí příkaz MS-DOS typ všechna data v tomto souboru. `"a+"` Režim je vyžadován pro připojení do datového proudu souboru, který je ukončen pomocí kombinace kláves CTRL + Z EOF značky.  
  
 Když `"r+"`, `"w+",` nebo `"a+"` byl zadán typ přístupu, jsou povoleny pro čtení i zápis. (Soubor říká, že je třeba otevřít pro "update".) Ale po přepnutí z čtení pro zápis vstupní operaci dojde EOF značky. Pokud není k dispozici žádné konce souboru, je nutné použít použité volání funkce umístění souboru. Umístění souboru funkce jsou `fsetpos`, `fseek`, a `rewind`. Po přepnutí z zápis do čtení, je nutné použít použité volání buď `fflush` nebo funkci umístění souboru.  
  
 Kromě výše uvedené hodnoty můžou být součástí následující znaky `mode` k určení režim překladu pro znaky nového řádku:  
  
 `t`  
 Otevřete v textu (přeložit) režimu. V tomto režimu CTRL + Z interpretována jako znak end souboru na vstup. V souborech otevřít pro čtení/zápis s `"a+"`, `fopen_s` kontroluje CTRL + Z na konci souboru a odstraní ji, pokud je to možné. To je provést, protože používá `fseek` a `ftell` v souboru, který může způsobit, že na konci CTRL + Z, přesuňte `fseek` chovat nesprávně blíží konec souboru.  
  
 Také v režimu textových znaků CR vrátit-konce řádku kombinace jsou převedeny do jednoho přečtené na vstup a znaky konce řádku jsou převedeny na kombinace znaků CR vrátit-konce řádku na výstup. Pokud funkce datového proudu I/O Unicode funguje v režimu textových (výchozí), zdroj nebo cílový datový proud předpokládá se, že posloupnosti vícebajtových znaků. Proto funkce vstupního datového proudu Unicode převést více-bajtové znaky na široké znaky (jako Pokud voláním `mbtowc` funkce). Ze stejného důvodu, funkce výstup datového proudu Unicode převést více-bajtové znaky široké znaky (jako Pokud voláním `wctomb` funkce).  
  
 `b`  
 Otevřete v binárním režimu (nepřeložený); jsou potlačovány překlady zahrnující znaky CR a konce řádku.  
  
 Pokud `t` nebo `b` není uveden v `mode`, je výchozí režim překladu definované globální proměnná [_fmode –](../../c-runtime-library/fmode.md). Pokud `t` nebo `b` je předponou argument, funkce selže a vrátí `NULL`.  
  
 Další informace o používání textovém a binárním režimu v kódování Unicode a vícebajtové datového proudu I/O najdete v tématu [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [vstupně-výstupní datový proud Unicode v textovém a binárním režimu](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).  
  
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
 Zadejte programové znakovou sadu pro tento soubor používat (ve formátu UTF-8, UTF-16LE a UNICODE). Nechte toto tento parametr zadán, pokud chcete kódování ANSI.  
  
 Platné znaky pro `mode` řetězec použitý v `fopen_s` a `_fdopen` odpovídají `oflag` argumenty použité v [_Otevřít](../../c-runtime-library/reference/open-wopen.md) a [_sopen –](../../c-runtime-library/reference/sopen-wsopen.md), a to takto.  
  
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
  
 Pokud používáte `rb` režimu, nebudete muset portu kódu a očekávají čtení spoustu soubor a/nebo nezáleží výkon sítě, soubory mapované paměti Win32 může být také možnost.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`fopen_s`|\<stdio.h >|  
|`_wfopen_s`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
 `c`, `n`, A `t` `mode` možnosti jsou rozšíření Microsoft pro `fopen_s` a `_fdopen` a neměl by se používat, kde je žádoucí přenositelnost ANSI.  
  
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
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fclose –, _fcloseall –](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen –, _wfdopen –](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [ferror –](../../c-runtime-library/reference/ferror.md)   
 [_fileno –](../../c-runtime-library/reference/fileno.md)   
 [freopen –, _wfreopen –](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode –](../../c-runtime-library/reference/setmode.md)