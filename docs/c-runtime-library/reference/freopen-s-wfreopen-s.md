---
title: "freopen_s –, _wfreopen_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wfreopen_s
- freopen_s
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
- freopen_s
- _tfreopen_s
- _wfreopen_s
dev_langs: C++
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2276de6c4539dffe4456c18fdeff88f852a44c2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="freopens-wfreopens"></a>freopen_s, _wfreopen_s
Znovu přiřadí ukazatel souboru. Tyto verze nástroje [freopen –, _wfreopen –](../../c-runtime-library/reference/freopen-wfreopen.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t freopen(   
   FILE** pFile,  
   const char *path,  
   const char *mode,  
   FILE *stream   
);  
errno_t _wfreopen(   
   FILE** pFile,  
   const wchar_t *path,  
   const wchar_t *mode,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pFile`  
 Ukazatel na ukazatel souboru poskytnutý voláním.  
  
 [v]`path`  
 Cesta k novému souboru.  
  
 [v]`mode`  
 Typ přístupu povolena.  
  
 [v]`stream`  
 Ukazatel na `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrací kód chyby. Dojde-li k chybě, je původní soubor uzavřen.  
  
## <a name="remarks"></a>Poznámky  
 `freopen_s` Funkce zavře soubor aktuálně přidružen `stream` a znovu přidělí `stream` do souboru určeného `path.` `_wfreopen_s` je verze široká charakterová `_freopen_s`; `path` a `mode` argumenty, které mají `_wfreopen_s` jsou široká charakterová řetězce. `_wfreopen_s`a `_freopen_s` chovat jinak shodně.  
  
 Pokud platí jedna z `pFile`, `path`, `mode`, nebo `stream` jsou `NULL`, nebo pokud `path` je prázdný řetězec, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfreopen_s`|`freopen_s`|`freopen_s`|`_wfreopen_s`|  
  
 Funkce `freopen_s` obvykle slouží k přesměrování dříve otevřených souborů `stdin`, `stdout` a `stderr` na soubory zadané uživatelem. Nový soubor přidružený k `stream` je otevřen s `mode`, což je řetězec znaků určující typ přístupu, které jsou požadované pro soubor, následujícím způsobem:  
  
 `"r"`  
 Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, `freopen_s` volání selže.  
  
 `"w"`  
 Otevře se prázdný soubor pro zápis. Pokud je daný soubor existuje, její obsah se způsobem zničena.  
  
 `"a"`  
 Otevře se pro zápis na konci souboru (přidávání) bez odstranění značky EOF před zápisem nových dat do souboru. Soubor nejdříve vytvoří, pokud již neexistuje.  
  
 `"r+"`  
 Otevře pro čtení i zápis. (Soubor musí existovat.)  
  
 `"w+"`  
 Otevře se prázdný soubor pro čtení i zápis. Pokud je daný soubor existuje, její obsah se způsobem zničena.  
  
 `"a+"`  
 Otevře se pro čtení a přidávání. Operace přidávání zahrnuje odstranění značky EOF před zápisem nových dat do souboru a obnovení značky EOF po dokončení zápisu. Soubor nejdříve vytvoří, pokud již neexistuje.  
  
 Typy `"w"` a `"w+"` je třeba používat opatrně, protože mohou zničit existující soubory.  
  
 Pokud je soubor otevřen použitím přístupového typu `"a"` nebo `"a+"`, objeví se všechny operace zápisu na konci souboru. Přestože lze ukazatel na soubor přesunout pomocí `fseek` nebo `rewind`, je ukazatel na soubor vždy přesunut na konec souboru před vykonáním jakékoli operace zápisu. Žádná existující data proto nemohou být přepsána.  
  
 `"a"` Režimu neodebere značky EOF před připojením k souboru. Po připojení došlo k chybě, MS-DOS typ příkazu se zobrazí pouze data až původní EOF značky a není žádná data připojen k souboru. `"a+"` Režimu odebrat značky EOF před připojením k souboru. Po připojení, zobrazí příkaz MS-DOS typ všechna data v tomto souboru. `"a+"` Režim je vyžadován pro připojení do datového proudu souboru, který je byla ukončena s CTRL + Z EOF značky.  
  
 Když `"r+"`, `"w+",` nebo `"a+"` byl zadán typ přístupu, jsou povoleny pro čtení i zápis (soubor říká, že je třeba otevřít pro "update"). Ale při přepínání mezi čtení a zápis, musí být uplynulého [fsetpos –](../../c-runtime-library/reference/fsetpos.md), [fseek](../../c-runtime-library/reference/fseek-fseeki64.md), nebo [rewind](../../c-runtime-library/reference/rewind.md) operaci. Podle potřeby lze určit aktuální pozici operace `fsetpos` nebo `fseek`. Kromě výše uvedených hodnot může být pro určení režimu překladu nových řádků do řetězce `mode` zahrnut jeden z následujících znaků.  
  
 `t`  
 Otevřete v textu (přeložit) režimu; kombinace znaků CR vrátit-nový řádek (CR-LF) jsou převedeny do jednoho nový řádek (LF) znaků na vstup; LF znaky jsou převedeny na znaky CR LF kombinace na výstup. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo pro zápis a pro čtení s `"a+"` vyhledá knihovna runtime příkazy CTRL+Z na konci souboru, a pokud je to možné, odstraní je. Toto je provedeno z důvodu použití `fseek` a `ftell` pro přesun v rámci souboru, což může způsobit nesprávné chování `fseek` v blízkosti konce souboru. Možnost `t` je rozšíření aplikace Microsoft, které by nemělo být použito při požadavku na přenositelnost ANSI.  
  
 `b`  
 Otevřete v binárním (nepřeloženém) režimu. Překlady uvedené výše jsou potlačeny.  
  
 Pokud `t` nebo `b` není uveden v `mode`, je výchozí režim překladu definované globální proměnná [_fmode –](../../c-runtime-library/fmode.md). Pokud `t` nebo `b` je předponou argument, funkce selže a vrátí `NULL`.  
  
 Informace o textovém a binárním režimu, najdete v části [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`freopen_s`|\<stdio.h >|  
|`_wfreopen_s`|\<stdio.h > nebo \<wchar.h >|  
  
 Konzole není podporována v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –`stdin`, `stdout`, a `stderr`– C běhové funkce je mohli používat, musí být přesměrována [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_freopen_s.c  
// This program reassigns stderr to the file  
// named FREOPEN.OUT and writes a line to that file.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int main( void )  
{  
   errno_t err;  
   // Reassign "stderr" to "freopen.out":   
   err = freopen_s( &stream, "freopen.out", "w", stderr );  
  
   if( err != 0 )  
      fprintf( stdout, "error on freopen\n" );  
   else  
   {  
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );  
      fprintf( stream, "This will go to the file 'freopen.out'\n" );  
      fclose( stream );  
   }  
   system( "type freopen.out" );  
}  
```  
  
```Output  
successfully reassigned  
This will go to the file 'freopen.out'  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [freopen –, _wfreopen –](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [fclose –, _fcloseall –](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen –, _wfdopen –](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [_fileno –](../../c-runtime-library/reference/fileno.md)   
 [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)