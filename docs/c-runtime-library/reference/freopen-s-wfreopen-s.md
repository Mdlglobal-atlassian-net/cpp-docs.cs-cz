---
title: freopen_s, _wfreopen_s
ms.date: 11/04/2016
api_name:
- _wfreopen_s
- freopen_s
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
- freopen_s
- _tfreopen_s
- _wfreopen_s
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
ms.openlocfilehash: 30cd1612045a9f9a69e6ac856a601bac3101467f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956702"
---
# <a name="freopen_s-_wfreopen_s"></a>freopen_s, _wfreopen_s

Znovu přiřadí ukazatel souboru. Tyto verze [freopen, _wfreopen](freopen-wfreopen.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t freopen(
   FILE** pFile,
   const char *path,
   const char *mode,
   FILE *stream
);
errno_t _wfreopen(
   FILE** pFile,
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Ukazatel na ukazatel souboru poskytnutý voláním.

*Cesta*<br/>
Cesta k novému souboru.

*Mode*<br/>
Typ povoleného přístupu.

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací kód chyby. Dojde-li k chybě, je původní soubor uzavřen.

## <a name="remarks"></a>Poznámky

Funkce **freopen_s** zavře soubor, který je aktuálně přidružený ke *streamu* , a znovu přiřadí *datový proud* k souboru určenému *cestou*. **_wfreopen_s** je **_freopen_s**verze s velkým znakem; argumenty *cesty* a *režimu* , které mají být **_wfreopen_s** , jsou řetězce s libovolným znakem. **_wfreopen_s** a **_freopen_s** se chovají stejně jinak.

Pokud má některý *z pFile*, *cesta*, *režim*nebo *datový proud* **hodnotu null**nebo je-li *cesta* prázdný řetězec, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s** se obvykle používá k přesměrování předem otevřených souborů **stdin**, **stdout**a **stderr** do souborů zadaných uživatelem. Nový soubor přidružený ke *streamu* se otevře s *režimem*, což je řetězec znaků určující typ přístupu požadovaný pro soubor, a to takto:

|*Mode*|Access|
|-|-|
| **í** | Otevře se pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, volání **freopen_s** se nezdařilo. |
| **"w"** | Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah je zničen. |
| **určitého** | Otevře se pro zápis na konci souboru (přidávání) bez odebrání označení konec souboru (EOF) před zápisem nových dat do souboru. Vytvoří soubor, pokud neexistuje. |
| **"r +"** | Otevře se pro čtení i zápis. Soubor musí existovat. |
| **"w +"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah se zničí. |
| **"a +"** | Otevře se pro čtení a připojení. Operace připojení zahrnuje odstranění značky EOF před zápisem nových dat do souboru. Po dokončení zápisu se značka EOF neobnoví. Vytvoří soubor, pokud neexistuje. |

Používejte typy **"w"** a **"w +"** se opatrně, protože mohou zničit stávající soubory.

Když je soubor otevřen s typem přístupu **"a"** nebo **"a +"** , všechny operace zápisu se provádějí na konci souboru. I když lze ukazatel na soubor přesunout pomocí [fseek](fseek-fseeki64.md) nebo Rewind [](rewind.md), ukazatel na soubor je vždy přesunut zpět na konec souboru před provedením jakékoli operace zápisu. Žádná existující data proto nemohou být přepsána.

Režim **"a"** neodstraní značku EOF před připojením k souboru. Po navázání připojení příkaz Typ MS-DOS zobrazuje pouze data do původní značky EOF a ne data připojena k souboru. Režim **"a +"** odstraní značku EOF před připojením k souboru. Po připojení se v příkazu typ MS-DOS zobrazí všechna data v souboru. Režim **"a +"** se vyžaduje pro připojení k souboru datového proudu, který je ukončený pomocí značky EOF CTRL + Z.

Je-li zadán typ přístupu **"r +"** , **"w +"** nebo **"a +"** , jsou povoleny čtení i zápis (soubor je označován jako otevřený pro "aktualizaci"). Pokud však přepínáte mezi čtením a zápisem, musí se jednat o [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)nebo [Rewind](rewind.md) operaci. V případě potřeby lze zadat aktuální pozici pro operaci [fsetpos](fsetpos.md) nebo [fseek](fseek-fseeki64.md) . Kromě výše uvedených hodnot může být jeden z následujících znaků obsažen v řetězci *režimu* pro určení režimu překladu pro nové řádky.

|Modifikátor *režimu*|Režim překladu|
|-|-|
| **t** | Otevřít v textovém (přeloženém) režimu. |
| **b** | Otevřít v binárním (nepřeloženém) režimu; překlady týkající se znaků návratového znaku a znaku čárového kanálu jsou potlačeny. |

V textovém (překládaném) režimu se kombinace návratového kanálu (CR-LF) přeloží na vstupní znaky LF (line feed). Znaky LF jsou na výstupu přeloženy na kombinace znaků CR-LF. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo pro zápis a čtení pomocí **"a +"** spouští běhová knihovna CTRL + Z na konci souboru a pokud je to možné, odstraní ho. Důvodem je, že použití [fseek](fseek-fseeki64.md) a [ftell](ftell-ftelli64.md) k přesunu v rámci souboru může způsobit, že se [fseek](fseek-fseeki64.md) chová nesprávně na konci souboru. Možnost **t** je rozšíření společnosti Microsoft, které by nemělo být použito tam, kde je žádoucí přenositelnost ANSI.

Pokud **t** nebo **b** není uveden v *režimu*, výchozí režim překladu je definován globální proměnnou [_fmode](../../c-runtime-library/fmode.md). Pokud je **t** nebo **b** předpona argumentu, funkce se nezdařila a vrátí **hodnotu null**.

Diskuzi o textu a binárních režimech najdete v tématu [vstupně-výstupní operace se soubory textového a binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio. h > nebo \<WCHAR. h >|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_freopen_s.c
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   errno_t err;
   // Reassign "stderr" to "freopen.out":
   err = freopen_s( &stream, "freopen.out", "w", stderr );

   if( err != 0 )
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

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
