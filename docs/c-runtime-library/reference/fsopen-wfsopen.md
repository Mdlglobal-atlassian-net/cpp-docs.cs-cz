---
title: _fsopen –, _wfsopen – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wfsopen
- _fsopen
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
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
dev_langs:
- C++
helpviewer_keywords:
- opening files, streams
- fsopen function
- tfsopen function
- wfsopen function
- _fsopen function
- files [C++], opening
- _tfsopen function
- _wfsopen function
- file sharing [C++]
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ce69c6789ba65f61c54957dde3dfa6965bc32e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405150"
---
# <a name="fsopen-wfsopen"></a>_fsopen, _wfsopen

Otevře se datový proud s sdílení souborů.

## <a name="syntax"></a>Syntaxe

```C
FILE *_fsopen(
   const char *filename,
   const char *mode,
   int shflag
);
FILE *_wfsopen(
   const wchar_t *filename,
   const wchar_t *mode,
   int shflag
);
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Název souboru, který se otevřít.

*Režim*<br/>
Typ přístupu povolena.

*shflag*<br/>
Typ sdílení povoleno.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí ukazatel vrátí do datového proudu. Hodnota ukazatele null znamená chybu. Pokud *filename* nebo *režimu* je **NULL** nebo prázdný řetězec, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru ](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **NULL** a nastavte **errno** k **einval –**.

Další informace o těchto a dalších kódy chyb najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Fsopen –** funkce otevře soubor určený touto *filename* jako datový proud a připraví soubor pro následné sdílené čtení nebo zápisu, podle definice v režimu a *shflag*argumenty. **_wfsopen –** je verze široká charakterová **_fsopen –**; *filename* a *režimu* argumenty, které mají **_wfsopen –** jsou široká charakterová řetězce. **_wfsopen –** a **_fsopen –** chovat jinak shodně.

Řetězec znaků *režimu* Určuje typ přístupu, které jsou požadované pro soubor, jak je znázorněno v následující tabulce.

|Termín|Definice|
|----------|----------------|
|**"r"**|Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, **_fsopen –** volání selže.|
|**"w"**|Otevře se prázdný soubor pro zápis. Pokud je daný soubor existuje, její obsah se způsobem zničena.|
|**"a"**|Otevře pro zápis na konec souboru (připojení); nejprve vytvoří soubor, pokud neexistuje.|
|**"r +"**|Otevře pro čtení i zápis. (Soubor musí existovat.)|
|**"w +"**|Otevře se prázdný soubor pro čtení i zápis. Pokud je daný soubor existuje, její obsah se způsobem zničena.|
|**"+"**|Otevře pro čtení a připojením algoritmu; nejprve vytvoří soubor, pokud neexistuje.|

Použití **"w"** a **"w +"** typy opatrně, protože zničí existující soubory.

Při otevření souboru s **"a"** nebo **"+"** přístup k typu, všechny zápisu operace probíhají na konci souboru. Ukazatele souboru můžete změnit jejich umístění pomocí [fseek](fseek-fseeki64.md) nebo [rewind](rewind.md), ale je vždy přesunuta zpět na konec souboru před všechny zápisu operace provádí. Žádná existující data proto nemohou být přepsána. Když **"r +"**, **"w +"**, nebo **"+"** byl zadán typ přístupu, jsou povoleny pro čtení i zápis (soubor říká, že je třeba otevřít pro aktualizaci). Ale při přepínání mezi čtení a zápis, musí být uplynulého [fsetpos –](fsetpos.md), [fseek](fseek-fseeki64.md), nebo [rewind](rewind.md) operaci. Aktuální pozice lze [fsetpos –](fsetpos.md) nebo [fseek](fseek-fseeki64.md) operace, v případě potřeby. Kromě výše uvedené hodnoty, jednu z následujících znaků může být součástí *režimu* k určení režim překladu pro nové řádky a správa souborů.

|Termín|Definice|
|----------|----------------|
|**t**|Otevře soubor v režimu textových (přeložit). V tomto režimu znaků CR vrátí řádek informačního kanálu (CR-LF) kombinace jsou přeložit na jeden řádek kanály (LF) na vstupu a LF znaky jsou převedeny na znaky CR LF kombinace na výstup. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřít pro čtení nebo čtení/zápis **_fsopen –** kontroluje CTRL + Z na konci souboru a odstraní ji, pokud je to možné. To je provést, protože používá [fseek](fseek-fseeki64.md) a [ftell –](ftell-ftelli64.md) v souboru, který může způsobit elementů end s CTRL + Z přesuňte [fseek](fseek-fseeki64.md) chovat nesprávně blíží konec souboru.|
|**b**|Otevře soubor v binárním režimu (nepřeložený); výše uvedené překlady jsou potlačovány.|
|**S**|Určuje, že ukládání do mezipaměti je optimalizovaná pro, ale není omezen na, sekvenční přístup z disku.|
|**R**|Určuje, že ukládání do mezipaměti je optimalizovaná pro, ale není omezena na náhodný přístup z disku.|
|**T**|Určuje soubor jako dočasnou. Pokud je to možné, není vyprázdněných na disk.|
|**D**|Určuje soubor jako dočasnou. Odstraní se při zavření posledního ukazatele souboru.|

Pokud **t** nebo **b** není uveden v *režimu*, režim překladu je definovanou proměnnou výchozí režim **_fmode –**. Pokud **t** nebo **b** předponou argument, funkce selže a vrátí je **NULL**. Informace o textovém a binárním režimu, najdete v části [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Argument *shflag* je konstantní výraz, který se skládá z jedné z následujících manifestu konstant definované v Share.h.

|Termín|Definice|
|----------|----------------|
|**_SH_COMPAT –**|Nastaví režim kompatibility pro 16bitové aplikace.|
|**_SH_DENYNO –**|Povolí přístup čtení a zápisu.|
|**_SH_DENYRD –**|Odepře přístup pro čtení k souboru.|
|**_SH_DENYRW –**|Odmítne oprávnění ke čtení a zápisu do souboru.|
|**_SH_DENYWR –**|Odepře přístup k zápisu do souboru.|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen –**|**_fsopen –**|**_fsopen –**|**_wfsopen –**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|--------------|---------------------|----------------------|
|**_fsopen –**|\<stdio.h>|\<share.h><br /><br /> Pro manifest konstanta pro *shflag* parametr.|
|**_wfsopen –**|\<stdio.h > nebo \<wchar.h >|\<share.h><br /><br /> Pro manifest konstanta pro *shflag* parametr.|

## <a name="example"></a>Příklad

```C
// crt_fsopen.c

#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   FILE *stream;

   // Open output file for writing. Using _fsopen allows us to
   // ensure that no one else writes to the file while we are
   // writing to it.
    //
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )
   {
      fprintf( stream, "No one else in the network can write "
                       "to this file until we are done.\n" );
      fclose( stream );
   }
   // Now others can write to the file while we read it.
   system( "type outfile" );
}
```

```Output
No one else in the network can write to this file until we are done.
```

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
