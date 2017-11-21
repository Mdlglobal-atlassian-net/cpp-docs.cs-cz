---
title: "_fdopen –, _wfdopen – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fdopen
- _wfdopen
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
apitype: DLLExport
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
dev_langs: C++
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bacc1decd25c5c7291295a9e97eeacb35d55662c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fdopen-wfdopen"></a>_fdopen, _wfdopen
Přidruží datového proudu souboru, který byl dříve otevřen pro nižší úroveň vstupně-výstupní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FILE *_fdopen(    
   int fd,  
   const char *mode   
);  
FILE *_wfdopen(   
   int fd,  
   const wchar_t *mode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Soubor popisovače otevření souboru.  
  
 `mode`  
 Typ přístup k souborům.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrací ukazatel na Otevřít datový proud. Hodnota ukazatele null znamená chybu. Když dojde k chybě, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` nastavený buď na `EBADF`, což naznačuje popisovač chybného souboru, nebo `EINVAL`, což znamená, že `mode` byl ukazatele null.  
  
 Další informace o těchto a dalších kódy chyb najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_fdopen` Funkce přidruží vstupně-výstupní datový proud souboru, která je identifikovaná `fd`a proto umožňuje soubor, který je otevřen pro nižší úroveň vstupně-výstupní vyrovnávací paměti a formátu. `_wfdopen`široká charakterová verze `_fdopen`; `mode` argument `_wfdopen` je široká charakterová řetězec. `_wfdopen`a `_fdopen` jinak chovají stejně jako.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfdopen`|`_fdopen`|`_fdopen`|`_wfdopen`|  
  
 `mode` Řetězec znaků určuje typ souboru a přístup k souborům.  
  
 Řetězec znaků `mode` Určuje typ přístupu, které jsou požadované pro soubor, jak je znázorněno v následující tabulce.  
  
 `"r"`  
 Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, `fopen` volání selže.  
  
 `"w"`  
 Otevře se prázdný soubor pro zápis. Pokud je daný soubor existuje, její obsah se způsobem zničena.  
  
 `"a"`  
 Otevře pro zápis na konec souboru (připojení). Pokud neexistuje, vytvoří soubor.  
  
 `"r+"`  
 Otevře pro čtení i zápis. (Soubor musí existovat.)  
  
 `"w+"`  
 Otevře se prázdný soubor pro čtení i zápis. Pokud je daný soubor existuje, její obsah se způsobem zničena.  
  
 `"a+"`  
 Otevře pro čtení a připojením. Pokud neexistuje, vytvoří soubor.  
  
 Při otevření souboru s `"a"` nebo `"a+"` přístup k typu, všechny zápisu operace probíhají na konci souboru. Ukazatele souboru můžete změnit jejich umístění pomocí `fseek` nebo `rewind`, ale je vždy přesunuta zpět na konec souboru před všechny zápisu operace provádí. Žádná existující data proto nemohou být přepsána. Když `"r+"`, `"w+"`, nebo `"a+"` byl zadán typ přístupu, jsou povoleny pro čtení i zápis (soubor říká, že je třeba otevřít pro "update"). Ale při přepínání mezi čtení a zápis, musí být uplynulého `fflush`, `fsetpos`, `fseek`, nebo `rewind` operaci. Můžete zadat pro aktuální pozici `fsetpos` nebo `fseek` operace, pokud chcete.  
  
 Kromě výše uvedené hodnoty následující znaky mohou být i součástí `mode` k určení režim překladu pro znaky nového řádku.  
  
 `t`  
 Otevřete v textu (přeložit) režimu. V tomto režimu kombinace znaků CR vrátit LF (CR-LF) jsou převedeny do informačních kanálů jednořádkové (LF) na vstupu a LF znaky jsou převedeny na znaky CR LF kombinace na výstup. Také Ctrl + Z interpretována jako znak end souboru na vstup. V souborech otevřít pro čtení/zápis `fopen` kontroluje Ctrl + Z na konci souboru a odstraní ji, pokud je to možné. To je provést, protože používá `fseek` a `ftell` funkce v souboru, který končí Ctrl + Z přesuňte může způsobit `fseek` chovat nesprávně blíží konec souboru.  
  
 `b`  
 Otevřete v binárním režimu (nepřeložený). Překlady z `t` jsou potlačovány režimu.  
  
 `c`  
 Povolit příznak potvrzení pro přidruženého `filename` tak, aby obsah souboru vyrovnávací paměti je zapsán přímo na disk v případě buď `fflush` nebo `_flushall` je volána.  
  
 `n`  
 Resetujte příznak potvrzení pro přidruženého `filename` na "Ne potvrzováním." Toto nastavení je výchozí. Pokud jste váš program s Commode.obj také přepisuje příznak globálního potvrzení. Globální potvrzení příznak výchozí hodnota je "Ne potvrzováním" Pokud explicitně propojit váš program s Commode.obj.  
  
 `t`, `c`, A `n` `mode` možnosti jsou rozšíření Microsoft pro `fopen` a `_fdopen`. Nepoužívejte je, pokud chcete zachovat přenositelnost ANSI.  
  
 Pokud `t` nebo `b` není uveden v `mode`, je výchozí režim překladu definované globální proměnná [_fmode –](../../c-runtime-library/fmode.md). Pokud `t` nebo `b` je předponou argument, funkce selže a vrátí `NULL`. Informace o textovém a binárním režimu, najdete v části [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
 Platné znaky pro `mode` řetězec použitý v `fopen` a `_fdopen` odpovídají `oflag` argumenty použité v [_Otevřít](../../c-runtime-library/reference/open-wopen.md) a [_sopen –](../../c-runtime-library/reference/sopen-wsopen.md), a to takto.  
  
|Znaky v `mode` řetězec|Ekvivalentní `oflag` hodnota`_open`/`_sopen`|  
|---------------------------------|---------------------------------------------------|  
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
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fdopen`|\<stdio.h >|  
|`_wfdopen`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_fdopen.c  
// This program opens a file by using low-level  
// I/O, then uses _fdopen to switch to stream  
// access. It counts the lines in the file.  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <fcntl.h>  
#include <io.h>  
#include <share.h>  
  
int main( void )  
{  
   FILE *stream;  
   int  fd, count = 0;  
   char inbuf[128];  
  
   // Open a file.  
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )  
      exit( 1 );  
  
   // Get stream from file descriptor.  
   if( (stream = _fdopen( fd, "r" )) == NULL )  
      exit( 1 );  
  
   while( fgets( inbuf, 128, stream ) != NULL )  
      count++;  
  
   // After _fdopen, close by using fclose, not _close.  
   fclose( stream );  
   printf( "Lines in file: %d\n", count );  
}  
```  
  
## <a name="input-crtfdopentxt"></a>Vstup: crt_fdopen.txt  
  
```  
Line one  
Line two  
```  
  
### <a name="output"></a>Výstup  
  
```  
Lines in file: 2  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [_dup –, _dup2 –](../../c-runtime-library/reference/dup-dup2.md)   
 [fclose –, _fcloseall –](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen –, _wfreopen –](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)