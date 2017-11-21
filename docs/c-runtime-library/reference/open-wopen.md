---
title: "_Otevřít _wopen – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _open
- _wopen
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
- _wopen
- _topen
- _open
dev_langs: C++
helpviewer_keywords:
- opening files, for file I/O
- topen function
- _open function
- _topen function
- _wopen function
- files [C++], opening
- wopen function
- open function
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b2362db1db1686bcf87cb171b3f29da48226d54b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="open-wopen"></a>_open, _wopen
Otevře soubor. Tyto funkce jsou zastaralé, protože bezpečnější verze jsou k dispozici. v tématu [_sopen_s –, _wsopen_s –](../../c-runtime-library/reference/sopen-s-wsopen-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _open(  
   const char *filename,  
   int oflag [,  
   int pmode]   
);  
int _wopen(  
   const wchar_t *filename,  
   int oflag [,  
   int pmode]   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Název souboru.  
  
 `oflag`  
 Druh operace povoleny.  
  
 `pmode`  
 Režim oprávnění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí, vrátí se popisovač souboru pro otevřený soubor. Vrácená hodnota -1 označuje chybu; v takovém případě `errno` nastaven na jednu z následujících hodnot.  
  
 `EACCES`  
 Se pokusil otevřít jen pro čtení souboru pro zápis souboru režimu sdílení neumožňuje zadané operace, nebo zadaná cesta je adresář.  
  
 `EEXIST`  
 `_O_CREAT`a `_O_EXCL` příznaků zadaných, ale `filename` již existuje.  
  
 `EINVAL`  
 Neplatný `oflag` nebo `pmode` argument.  
  
 `EMFILE`  
 Žádné další popisovače souborů, které jsou k dispozici (je otevřeno příliš mnoho souborů).  
  
 `ENOENT`  
 Soubor nebo cesta nebyla nalezena.  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_open` Funkce otevře soubor určený touto `filename` a připraví ho pro čtení nebo zápisu podle specifikace `oflag`. `_wopen`široká charakterová verze `_open`; `filename` argument `_wopen` je široká charakterová řetězec. `_wopen`a `_open` chovat jinak shodně.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_topen`|`_open`|`_open`|`_wopen`|  
  
 `oflag`výraz celého čísla je vytvořen z jedné nebo více následujících manifestu konstanty nebo konstantní kombinace, které jsou definovány v \<fcntl.h >.  
  
 `_O_APPEND`  
 Přesune ukazatele souboru na konec souboru před každou operaci zápisu.  
  
 `_O_BINARY`  
 Soubor se otevře v binárním režimu (nepřeložený). (Viz [fopen –](../../c-runtime-library/reference/fopen-wfopen.md) popis binárního režimu.)  
  
 `_O_CREAT`  
 Soubor se vytvoří a otevře ji pro zápis. Nemá vliv, pokud soubor určeného `filename` existuje. `pmode` Argument je požadován při `_O_CREAT` je zadán.  
  
 `_O_CREAT` &#124; `_O_SHORT_LIVED`  
 Vytvoří soubor jako dočasné a pokud je to možné není vyprázdnit na disk. `pmode` Argument je požadován při `_O_CREAT` je zadán.  
  
 `_O_CREAT` &#124; `_O_TEMPORARY`  
 Vytvoří soubor jako dočasné; soubor je odstraněn při zavření posledního popisovače souborů. `pmode` Argument je požadován při `_O_CREAT` je zadán.  
  
 `_O_CREAT` &#124; `_O_EXCL`  
 Vrací hodnotu chyby, pokud soubor určeného `filename` existuje. Platí pouze při použití s `_O_CREAT`.  
  
 `_O_NOINHERIT`  
 Brání vytváření sdílený soubor popisovače.  
  
 `_O_RANDOM`  
 Určuje, že ukládání do mezipaměti je optimalizovaná pro, ale není omezena na náhodný přístup z disku.  
  
 `_O_RDONLY`  
 Otevře se soubor jen pro čtení. Nelze zadat u `_O_RDWR` nebo `_O_WRONLY`.  
  
 `_O_RDWR`  
 Otevře soubor pro čtení i zápis. Nelze zadat u `_O_RDONLY` nebo `_O_WRONLY`.  
  
 `_O_SEQUENTIAL`  
 Určuje, že ukládání do mezipaměti je optimalizovaná pro, ale není omezen na, sekvenční přístup z disku.  
  
 `_O_TEXT`  
 Otevře soubor v režimu textových (přeložit). (Další informace najdete v tématu [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [fopen –](../../c-runtime-library/reference/fopen-wfopen.md).)  
  
 `_O_TRUNC`  
 Otevře soubor a zkrátí ho nule length; soubor musí mít oprávnění k zápisu. Nelze zadat u `_O_RDONLY`. `_O_TRUNC`použít s `_O_CREAT` otevře existující soubor nebo soubor se vytvoří.  
  
> [!NOTE]
>  `_O_TRUNC` Příznak zničí obsah zadaného souboru.  
  
 `_O_WRONLY`  
 Otevře soubor pro zápis pouze. Nelze zadat u `_O_RDONLY` nebo `_O_RDWR`.  
  
 `_O_U16TEXT`  
 Soubor se otevře v režimu Unicode UTF-16.  
  
 `_O_U8TEXT`  
 Soubor se otevře v režimu Unicode UTF-8.  
  
 `_O_WTEXT`  
 Soubor se otevře v režimu Unicode.  
  
 Pokud chcete nastavit režim souboru přístup, je nutné zadat buď `_O_RDONLY`, `_O_RDWR`, nebo `_O_WRONLY`. Neexistuje žádná výchozí hodnota pro režim přístupu.  
  
 Pokud `_O_WTEXT` slouží k otevření souboru pro čtení, `_open` čte na začátek souboru a kontroluje značka pořadí bajtů (BOM). Pokud je Kusovník, soubor je považována za UTF-8 nebo UTF-16LE, v závislosti na Kusovníku. Pokud je k dispozici žádné BOM, soubor je považována za ANSI. Při otevření souboru pro zápis pomocí `_O_WTEXT`, použije se ve formátu UTF-16. Bez ohledu na to žádné předchozí nastavení nebo bajt pořadí značky, pokud `_O_U8TEXT` se používá, vždy otevření souboru ve formátu UTF-8; Pokud `_O_U16TEXT` se používá, soubor se vždy otevře jako UTF-16.  
  
 Při otevření souboru v režimu Unicode pomocí `_O_WTEXT`, `_O_U8TEXT`, nebo `_O_U16TEXT`, vstupní funkce převede data, která je pro čtení ze souboru do UTF-16 data uložená jako typ `wchar_t`. Funkce, které zapisovat do souboru otevřeného v režimu Unicode očekávat vyrovnávací paměti, které obsahují data ve formátu UTF-16 uložené jako typ `wchar_t`. Pokud soubor zakódován pomocí kódování UTF-8, je při je zapsán a kódování UTF-8 obsah souboru je přeložit na UTF-16, když je pro čtení dat ve formátu UTF-16 přeložit na UTF-8. Pokus o čtení nebo zápisu lichý počet bajtů v režimu Unicode způsobí, že chyba ověření parametru. Číst nebo zapisovat data, která je uložená v programu jako UTF-8, použijte místo režim Unicode režim textových nebo binárních souborů. Jste zodpovědní za jakékoli požadované kódování překlad.  
  
 Pokud `_open` je volán s `_O_WRONLY|_O_APPEND` (režim připojení) a `_O_WTEXT`, `_O_U16TEXT`, nebo `_O_U8TEXT`, nejprve se pokusí otevřít soubor pro čtení a zápis, přečtěte si Kusovníku a pak ho znovu otevřít pro zápis pouze. Pokud otevírání souboru pro čtení a zápis selže, otevře soubor pro zápis pouze a používá výchozí hodnota pro nastavení režimu kódování Unicode.  
  
 Při použití dvou nebo více manifestu konstanty do formuláře `oflag` argument, konstanty spolu se operátoru bitové operace OR ( `|` ). Informace z binárního souboru a text režimů, naleznete v [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
 `pmode` Se vyžaduje jenom v případě `_O_CREAT` je zadán. Pokud soubor již existuje, `pmode` je ignorována. V opačném `pmode` určuje nastavení oprávnění souborů, které lze nastavit při zavření první nový soubor. `_open`použije aktuální maska souboru oprávnění k `pmode` předtím, než jsou oprávnění nastavena. (Další informace najdete v tématu [_umask –](../../c-runtime-library/reference/umask.md).) `pmode` je použit celočíselný výraz, který obsahuje jedno nebo obě následující manifestu konstanty, které jsou definovány v \<sys\stat.h >.  
  
 `_S_IREAD`  
 Pouze čtení povolené.  
  
 `_S_IWRITE`  
 Zápis povolen. (Ve skutečnosti povoluje čtení a zápis.)  
  
 `_S_IREAD`  `|`  `_S_IWRITE`  
 Čtení a zápis povolen.  
  
 Pokud jsou zadány oba konstanty, jsou spojeny pomocí operátoru bitové operace OR ( `|` ). V systému Windows jsou všechny soubory čitelný; oprávnění jen pro zápis není k dispozici. Proto režimů `_S_IWRITE` a `_S_IREAD` `|` `_S_IWRITE` odpovídají.  
  
 Pokud hodnota než některých kombinací `_S_IREAD` a `_S_IWRITE` je zadán pro `pmode`– i v případě, že by zadejte platný `pmode` v jiném operačním systému – nebo pokud je některá hodnota jiné než povolené maximum `oflag` je zadané hodnoty, funkce generuje kontrolní výrazy v režimu ladění a vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, funkce vrátí hodnotu -1 a nastaví je povoleno spuštění `errno` k `EINVAL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_open`|\<IO.h >|\<fcntl.h >, \<sys\types.h >, \<sys\stat.h >|  
|`_wopen`|\<IO.h > nebo \<wchar.h >|\<fcntl.h >, \<sys\types.h >, \<sys\stat.h >|  
  
 `_open`a `_wopen` jsou rozšíření Microsoft. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_open.c  
// compile with: /W3  
/* This program uses _open to open a file  
 * named CRT_OPEN.C for input and a file named CRT_OPEN.OUT  
 * for output. The files are then closed.  
 */  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int fh1, fh2;  
  
   fh1 = _open( "CRT_OPEN.C", _O_RDONLY ); // C4996  
   // Note: _open is deprecated; consider using _sopen_s instead  
   if( fh1 == -1 )  
      perror( "Open failed on input file" );  
   else  
   {  
      printf( "Open succeeded on input file\n" );  
      _close( fh1 );  
   }  
  
   fh2 = _open( "CRT_OPEN.OUT", _O_WRONLY | _O_CREAT, _S_IREAD |   
                            _S_IWRITE ); // C4996  
   if( fh2 == -1 )  
      perror( "Open failed on output file" );  
   else  
   {  
      printf( "Open succeeded on output file\n" );  
      _close( fh2 );  
   }  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
Open succeeded on input file  
Open succeeded on output file  
```  
  
## <a name="see-also"></a>Viz také  
 [I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)   
 [_chmod –, _wchmod –](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_close –](../../c-runtime-library/reference/close.md)   
 [_creat –, _wcreat –](../../c-runtime-library/reference/creat-wcreat.md)   
 [_dup –, _dup2 –](../../c-runtime-library/reference/dup-dup2.md)   
 [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_sopen –, _wsopen –](../../c-runtime-library/reference/sopen-wsopen.md)