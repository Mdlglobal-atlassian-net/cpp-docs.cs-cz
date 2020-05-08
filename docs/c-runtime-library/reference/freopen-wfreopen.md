---
title: freopen, _wfreopen
ms.date: 4/2/2020
api_name:
- freopen
- _wfreopen
- _o__wfreopen
- _o_freopen
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wfreopen
- _tfreopen
- freopen
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
ms.openlocfilehash: 435211b246f9943588aeef2005e501a9eac59c6b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916342"
---
# <a name="freopen-_wfreopen"></a>freopen, _wfreopen

Znovu přiřadí ukazatel souboru. K dispozici jsou bezpečnější verze těchto funkcí; viz [freopen_s, _wfreopen_s](freopen-s-wfreopen-s.md).

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*dílčí*<br/>
Cesta k novému souboru.

*Mode*<br/>
Typ povoleného přístupu.

*Stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na nově otevřený soubor. Pokud dojde k chybě, původní soubor je zavřen a funkce vrátí hodnotu ukazatele s **hodnotou null** . Pokud je *cesta*, *režim*nebo *datový proud* ukazatel s hodnotou null, nebo pokud je *název souboru* prázdným řetězcem, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí **hodnotu null**.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Existují bezpečnější verze těchto funkcí naleznete v tématu [freopen_s, _wfreopen_s](freopen-s-wfreopen-s.md).

Funkce **freopen** zavře soubor, který je aktuálně přidružený ke *streamu* , a znovu přiřadí *datový proud* k souboru určenému *cestou*. **_wfreopen** je verze **_freopen**s velkým znakem; argumenty *cesty* a *režimu* , které se mají **_wfreopen** , jsou řetězce s velkým znakem. **_wfreopen** a **_freopen** se chovají identicky jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen**|**freopen**|**freopen**|**_wfreopen**|

**freopen** se obvykle používá k přesměrování předem otevřených souborů **stdin**, **stdout**a **stderr** do souborů zadaných uživatelem. Nový soubor přidružený ke *streamu* se otevře s *režimem*, což je řetězec znaků určující typ přístupu požadovaný pro soubor, a to takto:

|*Mode*|Access|
|-|-|
| **í** | Otevře se pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, volání **freopen** se nezdařilo. |
| **w** | Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah je zničen. |
| **určitého** | Otevře se pro zápis na konci souboru (přidávání) bez odebrání označení konec souboru (EOF) před zápisem nových dat do souboru. Vytvoří soubor, pokud neexistuje. |
| **"r +"** | Otevře se pro čtení i zápis. Soubor musí existovat. |
| **"w +"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah se zničí. |
| **"a +"** | Otevře se pro čtení a připojení. Operace připojení zahrnuje odstranění značky EOF před zápisem nových dat do souboru. Po dokončení zápisu se značka EOF neobnoví. Vytvoří soubor, pokud neexistuje. |

Používejte typy **"w"** a **"w +"** se opatrně, protože mohou zničit stávající soubory.

Když je soubor otevřen s typem přístupu **"a"** nebo **"a +"** , všechny operace zápisu se provádějí na konci souboru. I když lze ukazatel na soubor přesunout pomocí [fseek](fseek-fseeki64.md) nebo [Rewind](rewind.md), ukazatel na soubor je vždy přesunut zpět na konec souboru před provedením jakékoli operace zápisu. Existující data proto nelze přepsat.

Režim **"a"** neodstraní značku EOF před připojením k souboru. Po navázání připojení příkaz Typ MS-DOS zobrazuje pouze data do původní značky EOF a ne data připojena k souboru. Režim **"a +"** odstraní značku EOF před připojením k souboru. Po připojení se v příkazu typ MS-DOS zobrazí všechna data v souboru. Režim **"a +"** se vyžaduje pro připojení k souboru datového proudu, který je ukončený pomocí značky EOF CTRL + Z.

Je-li zadán typ přístupu **"r +"**, **"w +"** nebo **"a +"** , jsou povoleny čtení i zápis (soubor je označován jako otevřený pro "aktualizaci"). Pokud však přepínáte mezi čtením a zápisem, musí se jednat o [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)nebo [Rewind](rewind.md) operaci. V případě potřeby lze zadat aktuální pozici pro operaci [fsetpos](fsetpos.md) nebo [fseek](fseek-fseeki64.md) . Kromě výše uvedených hodnot může být jeden z následujících znaků obsažen v řetězci *režimu* pro určení režimu překladu pro nové řádky.

|Modifikátor *režimu*|Režim překladu|
|-|-|
| **š** | Otevřít v textovém (přeloženém) režimu. |
| **b** | Otevřít v binárním (nepřeloženém) režimu; překlady týkající se znaků návratového znaku a znaku čárového kanálu jsou potlačeny. |

V textovém (překládaném) režimu se kombinace návratového kanálu (CR-LF) přeloží na vstupní znaky LF (line feed). Znaky LF jsou na výstupu přeloženy na kombinace znaků CR-LF. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo pro zápis a čtení pomocí **"a +"** spouští běhová knihovna CTRL + Z na konci souboru a pokud je to možné, odstraní ho. Důvodem je, že použití [fseek](fseek-fseeki64.md) a [ftell](ftell-ftelli64.md) k přesunu v rámci souboru může způsobit, že se [fseek](fseek-fseeki64.md) chová nesprávně na konci souboru. Možnost **t** je rozšíření společnosti Microsoft, které by nemělo být použito tam, kde je žádoucí přenositelnost ANSI.

Pokud **t** nebo **b** není uveden v *režimu*, výchozí režim překladu je definován globální proměnnou [_fmode](../../c-runtime-library/fmode.md). Pokud je **t** nebo **b** předpona argumentu, funkce se nezdařila a vrátí **hodnotu null**.

Diskuzi o textu a binárních režimech najdete v tématu [vstupně-výstupní operace se soubory textového a binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**freopen**|\<stdio. h>|
|**_wfreopen**|\<stdio. h> nebo \<WCHAR. h>|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
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

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
