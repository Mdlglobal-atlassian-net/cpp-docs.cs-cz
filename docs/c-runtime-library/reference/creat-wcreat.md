---
title: "_creat –, _wcreat – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _creat
- _wcreat
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
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
dev_langs:
- C++
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0355f28ada6313e201b8d761813767135ee3cbf8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="creat-wcreat"></a>_creat, _wcreat
Vytvoří nový soubor. `_creat` a `_wcreat` jsou zastaralé; použít [_sopen_s –, _wsopen_s –](../../c-runtime-library/reference/sopen-s-wsopen-s.md) místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _creat(   
   const char *filename,  
   int pmode   
);  
int _wcreat(   
   const wchar_t *filename,  
   int pmode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Název nového souboru.  
  
 `pmode`  
 Nastavení oprávnění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tyto funkce v případě úspěchu vrátí popisovače souborů k vytvoření souboru. Jinak, funkce vrátí hodnotu -1 a nastavte `errno` jak je znázorněno v následující tabulce.  
  
|`errno` Nastavení|Popis|  
|---------------------|-----------------|  
|`EACCES`|`filename` Určuje existující jen pro čtení soubor nebo adresář místo souboru.|  
|`EMFILE`|Nejsou k dispozici žádné další popisovače souborů.|  
|`ENOENT`|Zadaný soubor nebyl nalezen.|  
  
 Pokud `filename` má hodnotu NULL, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí hodnotu -1.  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_creat` Funkce vytvoří nový soubor nebo otevře a zkrátí některého ze stávajících. `_wcreat` široká charakterová verze `_creat`; `filename` argument `_wcreat` je široká charakterová řetězec. `_wcreat` a `_creat` chovat jinak shodně.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcreat`|`_creat`|`_creat`|`_wcreat`|  
  
 Pokud soubor Určuje `filename` neexistuje, nový soubor je vytvořen s nastavením dané oprávnění a je otevřena pro zápis. Pokud soubor již existuje a jeho nastavení oprávnění umožňuje zápis, `_creat` zkrátí souboru, který se má délku 0, zničení předchozí obsah a otevře ji pro zápis. Nastavení oprávnění `pmode`, týká se pouze nově vytvořený souborů. Nový soubor obdrží nastavení zadané oprávnění po prvním je uzavřený. Celočíselný výraz `pmode` obsahuje jeden nebo oba manifestu konstanty `_S_IWRITE` a `_S_IREAD`, definované v SYS\Stat.h. Pokud jsou zadány oba konstanty, jsou spojeny s bitové hodnotě `OR` – operátor ( **&#124;** ). `pmode` Parametr je nastaven na jednu z následujících hodnot.  
  
|Hodnota|Definice|  
|-----------|----------------|  
|`_S_IWRITE`|Zápis povolen.|  
|`_S_IREAD`|Čtení povolené.|  
|`_S_IREAD &#124; _S_IWRITE`|Čtení a zápis povolen.|  
  
 Není-li oprávnění k zápisu, soubor je jen pro čtení. Všechny soubory budou vždy čitelný; není možné udělit oprávnění jen pro zápis. Režimy `_S_IWRITE` a `_S_IREAD | _S_IWRITE` jsou pak ekvivalentní. Soubory otevřené pomocí `_creat` jsou vždy otevřít v režimu kompatibility (viz [_sopen –](../../c-runtime-library/reference/sopen-wsopen.md)) s `_SH_DENYNO`.  
  
 `_creat` použije aktuální maska souboru oprávnění k `pmode` před nastavením oprávnění (viz [_umask –](../../c-runtime-library/reference/umask.md)). `_creat` je k dispozici kvůli kompatibilitě s předchozí knihovny. Volání `_open` s `_O_CREAT` a `_O_TRUNC` v `oflag` parametr je ekvivalentní `_creat` a je vhodnější pro nový kód.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_creat`|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|  
|`_wcreat`|\<IO.h > nebo \<wchar.h >|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_creat.c  
// compile with: /W3  
// This program uses _creat to create  
// the file (or truncate the existing file)  
// named data and open it for writing.  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int fh;  
  
   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996  
   // Note: _creat is deprecated; use _sopen_s instead  
   if( fh == -1 )  
      perror( "Couldn't create data file" );  
   else  
   {  
      printf( "Created data file.\n" );  
      _close( fh );  
   }  
}  
```  
  
```Output  
Created data file.  
```  
  
## <a name="see-also"></a>Viz také  
 [I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)   
 [_chmod, _wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_chsize](../../c-runtime-library/reference/chsize.md)   
 [_close –](../../c-runtime-library/reference/close.md)   
 [_dup, _dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_sopen, _wsopen](../../c-runtime-library/reference/sopen-wsopen.md)   
 [_umask](../../c-runtime-library/reference/umask.md)