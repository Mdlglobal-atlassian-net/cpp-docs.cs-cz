---
title: fopen_s, _wfopen_s
ms.date: 4/2/2020
api_name:
- _wfopen_s
- fopen_s
- _o__wfopen_s
- _o_fopen_s
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
- fopen_s
- _tfopen_s
- _wfopen_s
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
ms.openlocfilehash: 80d04e75637cfab9795bf5dfb9da9786cf4ebd71
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346495"
---
# <a name="fopen_s-_wfopen_s"></a>fopen_s, _wfopen_s

Otevře soubor. Tyto verze [fopen, _wfopen](fopen-wfopen.md) mají vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*pSoubor*<br/>
Ukazatel na ukazatel souboru, který obdrží ukazatel na otevřený soubor.

*Název_souboru*<br/>
Název_souboru.

*Režimu*<br/>
Typ přístupu povolen.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; kód chyby při selhání. Další informace o těchto kódech chyb naleznete v [tématu errno, _doserrno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

### <a name="error-conditions"></a>Chybové stavy

|*pSoubor*|*Název_souboru*|*Režimu*|Návratová hodnota|Obsah *souboru pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**Null**|jakékoli|jakékoli|**EINVAL**|Nezměněn|
|jakékoli|**Null**|jakékoli|**EINVAL**|Nezměněn|
|jakékoli|jakékoli|**Null**|**EINVAL**|Nezměněn|

## <a name="remarks"></a>Poznámky

Soubory, které jsou otevřeny **fopen_s** a **_wfopen_s,** nejsou sharable. Pokud požadujete, aby byl soubor dělitelný, použijte [_fsopen, _wfsopen](fsopen-wfsopen.md) s příslušnou konstantou režimu sdílení – například **_SH_DENYNO** pro sdílení pro čtení a zápis.

Funkce **fopen_s** otevře soubor určený *názvem souboru*. **_wfopen_s** je širokoznaková verze **fopen_s**; argumenty, které mají **_wfopen_s,** jsou řetězce s širokými znaky. **_wfopen_s** a **fopen_s** se chovají stejně jinak.

**fopen_s** přijímá cesty, které jsou platné v systému souborů v místě spuštění; Cesty UNC a cesty, které zahrnují namapované síťové jednotky jsou přijímány **fopen_s** tak dlouho, dokud systém, který je provádění kódu má přístup ke sdílené nebo mapované síťové jednotky v době spuštění. Při vytváření cest pro **fopen_s**nevytvářejte předpoklady o dostupnosti jednotek, cest nebo síťových sdílených složek v prostředí provádění. Jako oddělovače adresářů v cestě můžete\\použít lomítka (/) nebo zpětná lomítka ( ).

Tyto funkce ověřují jejich parametry. Pokud je *pFile*, *název souboru*nebo *režim* ukazatelem null, tyto funkce generují neplatnou výjimku parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md).

Vždy zkontrolujte vrácenou hodnotu a zjistěte, zda byla funkce úspěšná před provedením dalších operací se souborem. Pokud dojde k chybě, je vrácen kód chyby a je nastavena globální proměnná **errno.** Další informace naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="unicode-support"></a>Podpora unicode

**fopen_s** podporuje datové proudy souborů Unicode. Chcete-li otevřít nový nebo existující soubor Unicode, předejte příznak *ccs,* který určuje požadované kódování, které **má fopen_s**:

**fopen_s (&fp, "newfile.txt", "rw, ccs=**_kódování_**");**

Povolené hodnoty *kódování* jsou **UNICODE**, **UTF-8**a **UTF-16LE**. Pokud pro *kódování*není zadána žádná hodnota , **fopen_s** používá kódování ANSI.

Pokud soubor již existuje a je otevřen pro čtení nebo připojení, určuje kódování značka bajtového pořadí (BOM), pokud je v souboru přítomen. Kódování kusovníku má přednost před kódováním, které je určeno příznakem *ccs.* Kódování *ccs* se používá pouze v případě, že není k dispozici žádný kusovník nebo pokud je soubor nový soubor.

> [!NOTE]
> Detekce kusovníku se vztahuje pouze na soubory, které jsou otevřeny v režimu Unicode; to znamená, že předáním *ccs vlajky.*

Následující tabulka shrnuje režimy pro různé ccs příznaky, které jsou *uvedeny* **na fopen_s** a pro bajt ové značky v souboru.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Použitá kódování na základě příznaku ccs a kusovníku

|ccs vlajka|Žádný kusovník (nebo nový soubor)|KUS: UTF-8|KUS: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**Unicode**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Soubory, které jsou otevřeny pro zápis v režimu Unicode, mají zápisník napsaný automaticky.

Pokud je *režim* **"a, ccs=**_encoding_**"**, **fopen_s** nejprve pokusí otevřít soubor s přístupem pro čtení i přístupem pro zápis. V případě úspěchu funkce přečte kusovník a určí kódování souboru; Pokud se nepodaří, funkce používá výchozí kódování pro soubor. V obou případech **fopen_s** pak znovu otevře soubor s přístupem pouze pro zápis. (To platí pouze **pro** režim, **nikoli+**.)

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

*Režim* řetězce znaků určuje druh přístupu, který je požadován pro soubor, a to následujícím způsobem.

|*Režimu*|Access|
|-|-|
| **"r"** | Otevírá se pro čtení. Pokud soubor neexistuje nebo jej nelze najít, **volání fopen_s** se nezdaří. |
| **"w"** | Otevře prázdný soubor pro psaní. Pokud daný soubor existuje, jeho obsah je zničen. |
| **"a"** | Otevře se pro zápis na konci souboru (připojení) bez odebrání značky konce souboru (EOF) před zápisem nových dat do souboru. Vytvoří soubor, pokud neexistuje. |
| **"r+"** | Otevírá se pro čtení i psaní. Soubor musí existovat. |
| **"w+"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah je zničen. |
| **"a+"** | Otevírá se pro čtení a připojení. Operace připojení zahrnuje odebrání značky EOF před zápisem nových dat do souboru. Značka EOF není obnovena po dokončení zápisu. Vytvoří soubor, pokud neexistuje. |

Při otevření souboru pomocí typu přístupu **"a"** nebo **"a+",** všechny operace zápisu dojít na konci souboru. Ukazatel souboru lze přemístit pomocí [fseek](fseek-fseeki64.md) nebo [převinout zpět](rewind.md), ale je vždy přesunuta zpět na konec souboru před provedením jakékoli operace zápisu tak, aby existující data nelze přepsat.

Režim **"a"** neodebere značku EOF před připojením k souboru. Po připojení došlo k ms-dos TYP příkaz zobrazí pouze data až do původní značky EOF a nikoli všechna data, která je připojena k souboru. Režim **"a+"** odebere značku EOF před připojením k souboru. Po připojení se v příkazu MS-DOS TYPE zobrazí všechna data v souboru. Režim **"a+"** je vyžadován pro připojení k souboru datového proudu, který je ukončen pomocí značky CTRL+Z EOF.

Pokud je zadán typ přístupu **"r+"**, **"w+"** nebo **"a+",** je povoleno čtení i zápis. (Soubor je řekl, aby byl otevřen pro "update".) Však při přepnutí ze čtení na zápis, vstupní operace musí dojít značky EOF. Pokud neexistuje žádný EOF, musíte použít zasahující volání funkce umístění souboru. Funkce umístění souborů jsou **fsetpos**, [fseek](fseek-fseeki64.md)a [rewind](rewind.md). Při přechodu z zápisu na čtení, je nutné použít zasahující volání buď **fflush** nebo funkce umístění souboru.

Kromě výše uvedených hodnot mohou být v *režimu* zahrnuty následující znaky pro určení režimu překladu znaků nového řádku:

|*modifikátor režimu*|Režim překladu|
|-|-|
| **t** | Otevřít v textovém (přeloženém) režimu. |
| **B** | Otevřít v binárním (nepřeloženém) režimu; překlady zahrnující znaky carriage-return a line feed jsou potlačeny. |

V režimu textu (přeloženo) je ctrl+z interpretován jako znak konce souboru na vstupu. V souborech otevřených pro čtení/zápis s **"a+"** **fopen_s** kontroly ctrl+ z na konci souboru a odstraní ji, pokud je to možné. Důvodem je, že pomocí [fseek](fseek-fseeki64.md) a **ftell** přesunout v rámci souboru, který končí CTRL + Z, může způsobit [fseek](fseek-fseeki64.md) chovat nesprávně blízko konce souboru.

Také v textovém režimu jsou kombinace podávání řádků přeloženy do jednoho řádkového podávání na vstupu a znaky podávání řádků jsou přeloženy do kombinací posuvu zpětného řádku vozíku na výstupu. Pokud funkce vstupně-videa/videa Unicode pracuje v textovém režimu (výchozí), zdrojový nebo cílový datový proud se považuje za posloupnost vícebajtových znaků. Proto funkce vstupu datového proudu Unicode převádějí vícebajtové znaky na široké znaky (jako by voláním funkce **mbtowc).** Ze stejného důvodu unicode stream-output funkce převést široké znaky vícebajtové znaky (jako by volání **wctomb** funkce).

Pokud **t** nebo **b** není uveden v *režimu*, výchozí režim překladu je definován globální proměnnou [_fmode](../../c-runtime-library/fmode.md). Pokud **t** nebo **b** je předponou argument, funkce se nezdaří a vrátí **NULL**.

Další informace o používání režimů textu a binárních režimů v režimech Unicode a vícebajtových datových proudech vi/v naleznete v [tématu Text a binární režim V/O souboru](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [V. a V. v režimu Text a Binární režimy](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|*modifikátor režimu*|Chování|
|-|-|
| **C** | Povolte příznak potvrzení pro přidružený *název souboru,* aby byl obsah vyrovnávací paměti souboru zapsán přímo na disk, pokud je volána **fflush** nebo **_flushall.** |
| **N** | Obnovte příznak potvrzení pro přidružený *název souboru* na "no-commit". Toto nastavení je výchozí. Také přepíše příznak globálního potvrzení, pokud propojíte program s COMMODE.OBJ. Výchozí hodnota příznaku globálního potvrzení je "no-commit", pokud explicitně nepropojíte program s COMMODE. OBJ (viz [Možnosti odkazu](../../c-runtime-library/link-options.md)). |
| **N** | Určuje, že soubor není zděděn podřízenými procesy. |
| **S** | Určuje, že ukládání do mezipaměti je optimalizováno pro sekvenční přístup z disku, ale není omezen na něj. |
| **R** | Určuje, že ukládání do mezipaměti je optimalizováno pro náhodný přístup z disku, ale není omezeno na něj. |
| **T** | Určuje soubor jako dočasný. Pokud je to možné, není vyprázdněna na disk. |
| **D** | Určuje soubor jako dočasný. Odstraní se při zavření ukazatele posledního souboru. |
| **ccs =**_kódování_ | Určuje kódovku znakovou sadu, která má být pro tento soubor používána (jedna z **UTF-8**, **UTF-16LE**nebo **UNICODE).** Pokud chcete kódování ANSI, ponechejte nespecifikované. |

Platné znaky pro řetězec *režimu* použitý v **fopen_s** a [_fdopen](fdopen-wfdopen.md) odpovídají argumentům *oflag* použitým v [_open](open-wopen.md) a [_sopen](sopen-wsopen.md), a to následovně.

|Znaky v *řetězci režimu*|Ekvivalentní hodnota *opříznaku* pro _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**A**|**_O_APPEND &#124; _O_WRONLY** (obvykle &#124; &#124; _O_CREAT &#124; _O_APPEND**)_O_WRONLY &#124; **_O_APPEND** (obvykle **_O_WRONLY &#124;** **_O_CREAT** _O_APPEND**)|
|**a+**|**_O_RDWR** **&#124; _O_APPEND** (obvykle **_O_RDWR** _O_CREAT **_O_RDWR _O_APPEND &#124;** &#124;) **_O_CREAT**|
|**R**|**_O_RDONLY**|
|**r+**|**_O_RDWR**|
|**W**|**_O_WRONLY** (obvykle **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_TRUNC**)|
|**w+**|**_O_RDWR** (obvykle **_O_RDWR &#124; &#124;** **_O_CREAT** **&#124; _O_TRUNC)**|
|**B**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**C**|Žádný|
|**N**|Žádný|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs=UNICODE**|**_O_WTEXT**|
|**ccs=UTF-8**|**_O_UTF8**|
|**ccs=UTF-16LE**|**_O_UTF16**|

Pokud používáte **režim rb,** nebudete muset přenést kód a očekáváte, že budete číst hodně souboru a / nebo se nestaráte o výkon sítě, paměťmapované soubory Win32 mohou být také možností.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

Možnosti *režimu* **c**, **n**a **t** jsou rozšíření společnosti Microsoft pro **fopen_s** a [_fdopen](fdopen-wfdopen.md) a neměly by být používány tam, kde je požadována přenositelnost ANSI.

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

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
