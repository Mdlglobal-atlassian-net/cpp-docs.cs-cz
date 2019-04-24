---
title: _fsopen, _wfsopen
ms.date: 11/04/2016
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
ms.openlocfilehash: 197a4f690a6626edbfec27ea4abef1999b6cedaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287693"
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
Název souboru, který se otevře.

*Režim*<br/>
Typ přístupu povolený.

*shflag*<br/>
Typ sdílení povolené.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na datový proud. Hodnota nulového ukazatele indikuje chybu. Pokud *filename* nebo *režimu* je **NULL** nebo prázdný řetězec, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation ](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **NULL** a nastavte **errno** k **EINVAL**.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Fsopen –** otevře soubor určený parametrem funkce *filename* jako datový proud a připraví soubor pro následující sdílené čtení nebo zápisu, jak je definováno režimu a *shflag*argumenty. **_wfsopen –** je verze širokého znaku **_fsopen –**; *filename* a *režimu* argumenty **_wfsopen –** jsou řetězce širokého znaku. **_wfsopen –** a **_fsopen –** se jinak chovají stejně.

Řetězec znaků *režimu* Určuje typ požadovaného přístupu k souboru, jak je znázorněno v následující tabulce.

|Termín|Definice|
|----------|----------------|
|**"r"**|Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, **_fsopen –** volání selže.|
|**"w"**|Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah zničen.|
|**"a"**|Otevře se pro zápis na konci souboru (připojením); soubor nejdříve vytvoří, pokud neexistuje.|
|**"r +"**|Otevře pro čtení i zápis. (Soubor musí existovat.)|
|**"w +"**|Otevře prázdný soubor pro čtení i zápis. Pokud daný soubor existuje, jeho obsah zničen.|
|**"a +"**|Otevře pro čtení a přidávání soubor nejdříve vytvoří, pokud neexistuje.|

Použití **"w"** a **"w +"** typy opatrně, protože mohou zničit existující soubory.

Při otevření souboru se **"a"** nebo **"a +"** získat přístup k typu, všechny zápisu operace dojít na konci souboru. Ukazatel na soubor lze přesunout pomocí [fseek](fseek-fseeki64.md) nebo [rewind](rewind.md), ale to je vždy přesunut na konec souboru před jakékoli zápisu operace provádí. Žádná existující data proto nemohou být přepsána. Když **"r +"**, **"w +"**, nebo **"a +"** je zadán přístupový typ, je povoleno čtení i zápis (souboru se říká, že otevřen pro úpravy). Ale při přepínání mezi čtení a zápis, musí existovat podílející [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md), nebo [rewind](rewind.md) operace. Aktuální pozici, je možné zadat pro [fsetpos](fsetpos.md) nebo [fseek](fseek-fseeki64.md) operace, v případě potřeby. Kromě výše uvedených hodnot, jeden z následujících znaků může být součástí *režimu* k určení režimu překladu nových řádků a pro správu souborů.

|Termín|Definice|
|----------|----------------|
|**t**|Otevře soubor v textovém (přeloženém) režimu. V tomto režimu return-line návrat na začátek řádku – kombinace informačního kanálu (CR-LF) jsou přeloženy do informačních kanálů jednoho řádku (LF) na vstupu a LF jsou přeloženy na výstupu jako kombinace CR-LF. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo čtení/zápis **_fsopen –** vyhledává CTRL + Z na konci souboru a odstraní ji, pokud je to možné. Toto je provedeno z důvodu použití [fseek](fseek-fseeki64.md) a [ftell –](ftell-ftelli64.md) pro přesun v rámci souboru, který končí CTRL + Z může způsobit, že [fseek](fseek-fseeki64.md) nesprávné chování na konci souboru.|
|**b**|Otevře soubor v binárním (nepřeloženém) režimu; překlady uvedené výše jsou potlačeny.|
|**S**|Určuje, že je mezipaměť optimalizovaná pro, ale nikoliv omezená, sekvenčním přístupem z disku.|
|**R**|Určuje, že je mezipaměť optimalizovaná pro, ale nikoliv omezená, náhodný přístup z disku.|
|**T**|Určuje soubor jako dočasný. Pokud je to možné, není zapsán na disk.|
|**D**|Určuje soubor jako dočasný. Je smazán po uzavření posledního ukazatele na soubor.|

Pokud **t** nebo **b** není uveden v *režimu*, režim překladu definován proměnnou výchozího režimu **_fmode**. Pokud **t** nebo **b** předponou argumentu, funkce selže a vrátí **NULL**. Diskuzi o textovém a binárním režimu, najdete v článku [textového a binárního režimu souboru vstupně-výstupních operací](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Argument *shflag* je konstantní výraz, který se skládá z jednoho z následujících konstant manifestu definovaných v Share.h.

|Termín|Definice|
|----------|----------------|
|**_SH_COMPAT**|Nastaví režim kompatibility pro 16bitové aplikace.|
|**_SH_DENYNO**|Povolí čtení a zápis.|
|**_SH_DENYRD**|Odepřít přístup pro čtení k tomuto souboru.|
|**_SH_DENYRW**|Zakazuje čtení a zápis do souboru.|
|**_SH_DENYWR**|Odepřít přístup pro zápis do souboru.|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Konstanty manifestu pro *shflag* parametru.|
|**_wfsopen**|\<stdio.h > nebo \<wchar.h >|\<share.h><br /><br /> Konstanty manifestu pro *shflag* parametru.|

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

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
