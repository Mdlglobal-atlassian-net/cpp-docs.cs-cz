---
title: _fsopen, _wfsopen
ms.date: 11/04/2016
api_name:
- _wfsopen
- _fsopen
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
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
ms.openlocfilehash: 1ffc3aa5801ff2ed63ecf815f3351e4d7a8cf459
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956485"
---
# <a name="_fsopen-_wfsopen"></a>_fsopen, _wfsopen

Otevře datový proud se sdílením souborů.

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

*Bitmap*<br/>
Název souboru, který se má otevřít

*Mode*<br/>
Typ povoleného přístupu.

*shflag*<br/>
Typ sdílení je povolený.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na datový proud. Hodnota nulového ukazatele označuje chybu. Pokud je *název souboru* nebo *režim* **null** nebo prázdný řetězec, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **hodnotu null** a nastaví **errno** na **EINVAL**.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_fsopen** otevře soubor určený parametrem *filename* jako datový proud a připraví soubor pro následné sdílené čtení nebo zápis, jak jsou definovány argumenty Mode a *Shflag* . **_wfsopen** je **_fsopen**verze s velkým znakem; argumenty *filename* a *Mode* pro **_wfsopen** jsou řetězce s libovolným znakem. **_wfsopen** a **_fsopen** se chovají stejně jinak.

*Režim* řetězce znaků Určuje typ přístupu požadovaný pro soubor, jak je znázorněno v následující tabulce.

|Termín|Definice|
|----------|----------------|
|**í**|Otevře se pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, volání **_fsopen** se nezdařilo.|
|**"w"**|Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah je zničen.|
|**určitého**|Otevře se pro zápis na konci souboru (přidávání); Vytvoří soubor jako první, pokud neexistuje.|
|**"r +"**|Otevře se pro čtení i zápis. (Soubor musí existovat.)|
|**"w +"**|Otevře prázdný soubor pro čtení i zápis. Pokud daný soubor existuje, jeho obsah je zničen.|
|**"a +"**|Otevře se pro čtení a připojení; Vytvoří soubor jako první, pokud neexistuje.|

Používejte typy **"w"** a **"w +"** se opatrně, protože mohou zničit stávající soubory.

Když se soubor otevře s typem přístupu **"a"** nebo **"a +"** , na konci souboru se objeví všechny operace zápisu. Ukazatel na soubor lze přemístit pomocí [fseek](fseek-fseeki64.md) nebo [Rewind](rewind.md), ale je vždy přesunut zpět na konec souboru před provedením jakékoli operace zápisu. Žádná existující data proto nemohou být přepsána. Je-li zadán typ přístupu **"r +"** , **"w +"** nebo **"a +"** , jsou povoleny čtení i zápis (soubor je označován jako otevřený pro aktualizaci). Při přepínání mezi čtením a zápisem však musí být [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)nebo [Rewind](rewind.md) operace. V případě potřeby lze zadat aktuální pozici pro operaci [fsetpos](fsetpos.md) nebo [fseek](fseek-fseeki64.md) . Kromě výše uvedených hodnot může být jeden z následujících znaků zahrnut do *režimu* pro určení režimu překladu pro nové řádky a pro správu souborů.

|Termín|Definice|
|----------|----------------|
|**t**|Otevře soubor v textovém (přeloženém) režimu. V tomto režimu jsou kombinace pro návrat vozíku z řádku (CR-LF) přeloženy na vstupní kanály (LF) na vstupu a znaky LF jsou přeloženy na výstup do kombinací znaků CR-LF. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo čtení/zápis **_fsopen** vyhledá na konci souboru CTRL + Z a pokud je to možné, odstraní ho. Důvodem je, že použití [fseek](fseek-fseeki64.md) a [ftell](ftell-ftelli64.md) k přesunu v souboru, který končí kombinací kláves CTRL + Z, může způsobit, že se [fseek](fseek-fseeki64.md) nesprávně chová na konci souboru.|
|**b**|Otevře soubor v binárním (nepřeloženém) režimu. výše uvedené překlady jsou potlačeny.|
|**S**|Určuje, že ukládání do mezipaměti je optimalizované pro, ale ne omezené na, sekvenční přístup z disku.|
|**R**|Určuje, že ukládání do mezipaměti je optimalizované pro, ale ne omezené na, náhodný přístup z disku.|
|**T**|Určuje soubor jako dočasný. Pokud je to možné, nezaprázdní na disk.|
|**D**|Určuje soubor jako dočasný. Odstraní se po zavření posledního ukazatele na soubor.|

Pokud **t** nebo **b** není uveden v *režimu*, je režim překladu definován pomocí proměnné ve výchozím režimu **_fmode**. Pokud je **t** nebo **b** předpona argumentu, funkce se nezdařila a vrátí **hodnotu null**. Diskuzi o textu a binárních režimech najdete v tématu [vstupně-výstupní operace se soubory textového a binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Argument *Shflag* je konstantní výraz skládající se z jedné z následujících konstant manifestu, které jsou definovány v Share. h.

|Termín|Definice|
|----------|----------------|
|**_SH_COMPAT**|Nastaví režim kompatibility pro 16bitové aplikace.|
|**_SH_DENYNO**|Povolí přístup pro čtení a zápis.|
|**_SH_DENYRD**|Odepře přístup pro čtení k souboru.|
|**_SH_DENYRW**|Zakazuje přístup pro čtení a zápis k souboru.|
|**_SH_DENYWR**|Zakazuje přístup pro zápis do souboru.|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Pro konstantu manifestu pro parametr *Shflag* .|
|**_wfsopen**|\<stdio. h > nebo \<WCHAR. h >|\<share.h><br /><br /> Pro konstantu manifestu pro parametr *Shflag* .|

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

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
