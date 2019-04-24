---
title: freopen_s, _wfreopen_s
ms.date: 11/04/2016
apiname:
- _wfreopen_s
- freopen_s
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
ms.openlocfilehash: 2cdc16f21882c32933868000c6fd1d66accc74b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332998"
---
# <a name="freopens-wfreopens"></a>freopen_s, _wfreopen_s

Znovu přiřadí ukazatel souboru. Tyto verze [freopen, _wfreopen](freopen-wfreopen.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Režim*<br/>
Typ přístupu povolený.

*stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací kód chyby. Dojde-li k chybě, je původní soubor uzavřen.

## <a name="remarks"></a>Poznámky

**Freopen_s –** funkce zavře soubor, který aktuálně přiřazen k *stream* a znovu přiřadí *stream* do souboru určeného *cesta* . **_wfreopen_s –** je verze širokého znaku **_freopen_s**; *cesta* a *režimu* argumenty **_wfreopen_s –** jsou řetězce širokého znaku. **_wfreopen_s –** a **_freopen_s** se jinak chovají stejně.

Pokud některý z *pFile*, *cesta*, *režimu*, nebo *stream* jsou **NULL**, nebo pokud *cesta* je prázdný řetězec, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátit **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s –** se obvykle používá k přesměrování dříve otevřených souborů **stdin**, **stdout**, a **stderr** na soubory zadané uživatelem. Nový soubor spojený s *stream* se otevře s *režimu*, což je řetězec znaků určující typ požadovaného přístupu k souboru, následujícím způsobem:

|*Režim*|Access|
|-|-|
| **"r"** | Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, **freopen_s –** volání selže. |
| **"w"** | Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah zničen. |
| **"a"** | Otevře se pro zápis na konci souboru (přidávání) bez odstranění značky end file (EOF) před zápisem do souboru. Vytvoří soubor, pokud neexistuje. |
| **"r +"** | Otevře pro čtení i zápis. Soubor musí existovat. |
| **"w +"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah zničen. |
| **"a +"** | Otevře pro čtení a připojení. Operace zobrazení zahrnuje odstranění značky EOF před zápisem do souboru. Nedojde k obnovení značky EOF po dokončení zápisu. Vytvoří soubor, pokud neexistuje. |

Použití **"w"** a **"w +"** typy opatrně, protože mohou zničit existující soubory.

Při otevření souboru se **"a"** nebo **"a +"** získat přístup k typu, všechny operace zápisu na konci souboru. Přestože lze ukazatel na soubor přesunout pomocí [fseek](fseek-fseeki64.md) nebo [rewind](rewind.md), ukazatel na soubor vždy přesunut na konec souboru před jakékoli zápisu operace provádí. Žádná existující data proto nemohou být přepsána.

**"A"** režimu neodstraní značku EOF před připojením k souboru. Po připojení došlo k chybě, příkaz MS-DOS TYPE zobrazí pouze data až po původní značku EOF, nikoliv data připojená k souboru. **"A +"** režimu odstranění značky EOF před připojením k souboru. Po připojení zobrazí příkaz MS-DOS TYPE všechna data v souboru. **"A +"** režim je vyžadován pro připojení k souboru datového proudu, který je přerušen skrze značku EOF CTRL + Z.

Když **"r +"**, **"w +"**, nebo **"a +"** je zadán přístupový typ, je povoleno čtení i zápis (Tento soubor říká, že je otevřen pro "úpravy"). Ale při přepínání mezi čtení a zápis, musí existovat podílející [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md), nebo [rewind](rewind.md) operace. Aktuální pozici, je možné zadat pro [fsetpos](fsetpos.md) nebo [fseek](fseek-fseeki64.md) operace, v případě potřeby. Kromě výše uvedených hodnot, jeden z následujících znaků může být součástí *režimu* řetězec k určení režimu překladu nových řádků.

|*režim* modifikátor|Režim překladu|
|-|-|
| **t** | Otevřít v textovém (přeloženém) režimu. |
| **b** | Otevřít v binárním (nepřeloženém) režimu; překlady typů návrat na začátek řádku a znak odřádkování jsou potlačeny. |

V textovém (přeloženém) režimu jsou kombinace návratový znak odřádkování (CR-LF) návrat na začátek řádku přeloženy do jednoho konce řádku (LF) znaků na vstupu; LF jsou přeloženy na výstupu jako kombinace CR-LF. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo zápis a čtení s **"a +"**, knihovny run-time kontroluje CTRL + Z na konci souboru a odstraní ji, pokud je to možné. Toto je provedeno z důvodu použití [fseek](fseek-fseeki64.md) a [ftell –](ftell-ftelli64.md) pro přesun v rámci souboru mohou způsobit [fseek](fseek-fseeki64.md) nesprávné chování na konci souboru. **t** možnost je rozšířením společnosti Microsoft, který by se neměly kde je žádoucí přenositelnost ANSI.

Pokud **t** nebo **b** není uveden v *režimu*, je výchozí režim překladu definován pomocí globální proměnné [_fmode](../../c-runtime-library/fmode.md). Pokud **t** nebo **b** předponou argumentu, funkce selže a vrátí **NULL**.

Diskuzi o textovém a binárním režimu, najdete v článku [textového a binárního režimu souboru vstupně-výstupních operací](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UPW). Standardní datový proud popisovačů, které jsou spojeny s konzolou, **stdin**, **stdout**, a **stderr**, musí být přesměrován před funkcí jazyka C za běhu můžete použít v aplikacích pro UWP . Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
