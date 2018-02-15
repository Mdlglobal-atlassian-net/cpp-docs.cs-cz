---
title: "freopen –, _wfreopen – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- freopen
- _wfreopen
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
- _wfreopen
- _tfreopen
- freopen
dev_langs:
- C++
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 49f1e2cd11606d2ebe53281a9d2f1d27533b4068
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="freopen-wfreopen"></a>freopen, _wfreopen
Znovu přiřadí ukazatel souboru. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [freopen_s –, _wfreopen_s –](../../c-runtime-library/reference/freopen-s-wfreopen-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FILE *freopen(   
   const char *path,  
   const char *mode,  
   FILE *stream   
);  
FILE *_wfreopen(   
   const wchar_t *path,  
   const wchar_t *mode,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `path`  
 Cesta k novému souboru.  
  
 `mode`  
 Typ přístupu povolena.  
  
 `stream`  
 Ukazatel na `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrací ukazatel na nově otevřený soubor. Pokud dojde k chybě, původní soubor se zavře a funkce vrátí hodnotu `NULL` hodnota ukazatele s hodnotou. Pokud `path`, `mode`, nebo `stream` je ukazatel s hodnotou null, nebo pokud `filename` je prázdný řetězec, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí `NULL`.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.  
  
## <a name="remarks"></a>Poznámky  
 Bezpečnější verzích tyto funkce neexistuje, najdete v části [freopen_s –, _wfreopen_s –](../../c-runtime-library/reference/freopen-s-wfreopen-s.md).  
  
 `freopen` Funkce zavře soubor aktuálně přidružen `stream` a znovu přidělí `stream` do souboru určeného `path`. `_wfreopen` široká charakterová verze `_freopen`; `path` a `mode` argumenty, které mají `_wfreopen` jsou široká charakterová řetězce. `_wfreopen` a `_freopen` chovat jinak shodně.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfreopen`|`freopen`|`freopen`|`_wfreopen`|  
  
 Funkce `freopen` obvykle slouží k přesměrování dříve otevřených souborů `stdin`, `stdout` a `stderr` na soubory zadané uživatelem. Nový soubor přidružený k `stream` je otevřen s `mode`, což je řetězec znaků určující typ přístupu, které jsou požadované pro soubor, následujícím způsobem:  
  
 `"r"`  
 Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, `freopen` volání selže.  
  
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
  
 Když `"r+"`, `"w+"`, nebo `"a+"` byl zadán typ přístupu, jsou povoleny pro čtení i zápis (soubor říká, že je třeba otevřít pro "update"). Ale při přepínání mezi čtení a zápis, musí být uplynulého [fsetpos –](../../c-runtime-library/reference/fsetpos.md), [fseek](../../c-runtime-library/reference/fseek-fseeki64.md), nebo [rewind](../../c-runtime-library/reference/rewind.md) operaci. Podle potřeby lze určit aktuální pozici operace `fsetpos` nebo `fseek`. Kromě výše uvedených hodnot může být pro určení režimu překladu nových řádků do řetězce `mode` zahrnut jeden z následujících znaků.  
  
 `t`  
 Otevřete v textu (přeložit) režimu; kombinace znaků CR vrátit-nový řádek (CR-LF) jsou převedeny do jednoho nový řádek (LF) znaků na vstup; LF znaky jsou převedeny na znaky CR LF kombinace na výstup. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo pro zápis a pro čtení s `"a+"` vyhledá knihovna runtime příkazy CTRL+Z na konci souboru, a pokud je to možné, odstraní je. Toto je provedeno z důvodu použití `fseek` a `ftell` pro přesun v rámci souboru, což může způsobit nesprávné chování `fseek` v blízkosti konce souboru. Možnost `t` je rozšíření aplikace Microsoft, které by nemělo být použito při požadavku na přenositelnost ANSI.  
  
 `b`  
 Otevřete v binárním (nepřeloženém) režimu. Překlady uvedené výše jsou potlačeny.  
  
 Pokud `t` nebo `b` není uveden v `mode`, je výchozí režim překladu definované globální proměnná [_fmode –](../../c-runtime-library/fmode.md). Pokud `t` nebo `b` je předponou argument, funkce selže a vrátí `NULL`.  
  
 Informace o textovém a binárním režimu, najdete v části [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`freopen`|\<stdio.h>|  
|`_wfreopen`|\<stdio.h > nebo \<wchar.h >|  
  
 Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –`stdin`, `stdout`, a `stderr`– C běhové funkce mohli používat v aplikacích pro UPW, musí být přesměrována. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_freopen.c  
// compile with: /W3  
// This program reassigns stderr to the file  
// named FREOPEN.OUT and writes a line to that file.  
#include <stdio.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int main( void )  
{  
   // Reassign "stderr" to "freopen.out":   
   stream = freopen( "freopen.out", "w", stderr ); // C4996  
   // Note: freopen is deprecated; consider using freopen_s instead  
  
   if( stream == NULL )  
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
 [fclose –, _fcloseall –](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen, _wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [_fileno](../../c-runtime-library/reference/fileno.md)   
 [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)