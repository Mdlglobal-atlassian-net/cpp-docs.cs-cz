---
title: _fsopen, _wfsopen
ms.date: 4/2/2020
api_name:
- _wfsopen
- _fsopen
- _o__fsopen
- _o__wfsopen
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 49907808729375e3bea18a5f4bbf204852e0072a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345703"
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

*Název_souboru*<br/>
Název souboru, který chcete otevřít.

*Režimu*<br/>
Typ přístupu povolen.

*švaho*<br/>
Typ sdílení povolen.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí ukazatel datového proudu. Hodnota ukazatele null označuje chybu. Pokud je *název souboru* nebo *režim* **null** nebo prázdný řetězec, tyto funkce vyvolávají neplatnou obslužnou rutinu parametru, jak je popsáno v části [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce vrátí **null** a nastavit **errno** **eINVAL**.

Další informace o těchto a dalších kódech chyb naleznete [v tématu _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_fsopen** otevře soubor určený *názvem souboru* jako datový proud a připraví soubor pro následné sdílené čtení nebo zápis, jak je definováno argumenty mode a *shflag.* **_wfsopen** je širokoznaková verze **_fsopen**; *argumenty název souboru* a *režimu,* které **mají _wfsopen,** jsou řetězce s širokými znaky. **_wfsopen** a **_fsopen** se chovají stejně jinak.

*Režim* řetězce znaků určuje typ přístupu požadovaného pro soubor, jak je znázorněno v následující tabulce.

|Označení|Definice|
|----------|----------------|
|**"r"**|Otevírá se pro čtení. Pokud soubor neexistuje nebo jej nelze najít, **volání _fsopen** se nezdaří.|
|**"w"**|Otevře prázdný soubor pro psaní. Pokud daný soubor existuje, jeho obsah je zničen.|
|**"a"**|Otevře se pro zápis na konci souboru (připojení); vytvoří soubor jako první, pokud neexistuje.|
|**"r+"**|Otevírá se pro čtení i psaní. (Soubor musí existovat.)|
|**"w+"**|Otevře prázdný soubor pro čtení i zápis. Pokud daný soubor existuje, jeho obsah je zničen.|
|**"a+"**|Otevírá se pro čtení a připojení; vytvoří soubor jako první, pokud neexistuje.|

Používejte typy **"w"** a **"w+"** opatrně, protože mohou zničit existující soubory.

Při otevření souboru s typem přístupu **"a"** nebo **"a+",** všechny operace zápisu dojít na konci souboru. Ukazatel souboru lze přemístit pomocí [fseek](fseek-fseeki64.md) nebo [převinout zpět](rewind.md), ale je vždy přesunuta zpět na konec souboru před provedením jakékoli operace zápisu. Existující data tedy nelze přepsat. Pokud je zadán typ přístupu **"r+"**, **"w+"** nebo **"a+",** je povoleno čtení i zápis (soubor je údajně otevřený pro aktualizaci). Při přepínání mezi čtením a zápisem však musí existovat zasahující [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)nebo [převíjení zpět.](rewind.md) Aktuální pozice může být určena pro [fsetpos](fsetpos.md) nebo [fseek](fseek-fseeki64.md) operace, pokud je to žádoucí. Kromě výše uvedených hodnot může být v *režimu* zahrnut jeden z následujících znaků, který určuje režim překladu pro nové řádky a pro správu souborů.

|Označení|Definice|
|----------|----------------|
|**t**|Otevře soubor v textovém (přeloženém) režimu. V tomto režimu jsou kombinace zpětného posuvu vozíku (CR-LF) přeloženy do jednoho řádkového podávání (LF) na vstupu a lf znaky jsou přeloženy do kombinací CR-LF na výstupu. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo čtení / zápis **_fsopen** kontroly pro CTRL + Z na konci souboru a odstraní ji, pokud je to možné. Důvodem je, že pomocí [fseek](fseek-fseeki64.md) a [ftell](ftell-ftelli64.md) přesunout v rámci souboru, který končí CTRL + Z může způsobit [fseek](fseek-fseeki64.md) chovat nesprávně blízko konce souboru.|
|**B**|Otevře soubor v binárním (nepřeloženém) režimu; výše uvedené překlady jsou potlačeny.|
|**S**|Určuje, že ukládání do mezipaměti je optimalizováno pro sekvenční přístup z disku, ale není omezen na něj.|
|**R**|Určuje, že ukládání do mezipaměti je optimalizováno pro náhodný přístup z disku, ale není omezeno na něj.|
|**T**|Určuje soubor jako dočasný. Pokud je to možné, není vyprázdněna na disk.|
|**D**|Určuje soubor jako dočasný. Odstraní se při zavření ukazatele posledního souboru.|

Není-li **b** **režim překladu** uveden v *režimu*, je režim překladu definován proměnnou výchozího režimu **_fmode**. Pokud **t** nebo **b** je předponou argument, funkce se nezdaří a vrátí **NULL**. Diskuse o texta a binární režimy naleznete [v tématu Text a binární režim soubor V/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Argument *shflag* je konstantní výraz skládající se z jedné z následujících konstant manifestu definovaných v souboru Share.h.

|Označení|Definice|
|----------|----------------|
|**_SH_COMPAT**|Nastavuje režim kompatibility pro 16bitové aplikace.|
|**_SH_DENYNO**|Umožňuje přístup ke čtení a zápisu.|
|**_SH_DENYRD**|Odepře přístup pro čtení k souboru.|
|**_SH_DENYRW**|Odepře přístup k souboru pro čtení a zápis.|
|**_SH_DENYWR**|Odepře přístup k souboru pro zápis.|

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Pro konstantu manifestu pro parametr *shflag.*|
|**_wfsopen**|\<stdio.h> \<nebo wchar.h>|\<share.h><br /><br /> Pro konstantu manifestu pro parametr *shflag.*|

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

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
