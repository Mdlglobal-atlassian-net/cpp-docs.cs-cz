---
title: freopen_s, _wfreopen_s
ms.date: 4/2/2020
api_name:
- _wfreopen_s
- freopen_s
- _o__wfreopen_s
- _o_freopen_s
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
ms.openlocfilehash: a24e34ead905d2f704bfbf4d829064c656272e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345922"
---
# <a name="freopen_s-_wfreopen_s"></a>freopen_s, _wfreopen_s

Znovu přiřadí ukazatel souboru. Tyto verze [freopen, _wfreopen](freopen-wfreopen.md) mají vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*pSoubor*<br/>
Ukazatel na ukazatel souboru poskytnutý voláním.

*Cestu*<br/>
Cesta k novému souboru.

*Režimu*<br/>
Typ přístupu povolen.

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací kód chyby. Dojde-li k chybě, je původní soubor uzavřen.

## <a name="remarks"></a>Poznámky

Funkce **freopen_s** zavře soubor, který je aktuálně spojen s *datovým proudem,* a znovu přiřadí datový *proud* k souboru určenému *cestou*. **_wfreopen_s** je širokoznaková verze **_freopen_s**; *argumenty cesty* a *režimu,* které **mají _wfreopen_s,** jsou řetězce s širokými znaky. **_wfreopen_s** a **_freopen_s** se chovají stejně jinak.

Pokud některý z *pFile*, *cesta*, *režim*nebo *datový proud* jsou **NULL**, nebo pokud *cesta* je prázdný řetězec, tyto funkce vyvolat neplatný parametr obslužné rutiny, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce nastavit **errno** na **EINVAL** a vrátit **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s** se obvykle používá k přesměrování předem otevřených souborů **stdin**, **stdout**a **stderr** na soubory určené uživatelem. Nový soubor přidružený k *datovému proudu* je otevřen s *režimem*, což je řetězec znaků určující typ přístupu požadovaný pro soubor, a to následovně:

|*Režimu*|Access|
|-|-|
| **"r"** | Otevírá se pro čtení. Pokud soubor neexistuje nebo jej nelze najít, **volání freopen_s** se nezdaří. |
| **"w"** | Otevře prázdný soubor pro psaní. Pokud daný soubor existuje, jeho obsah je zničen. |
| **"a"** | Otevře se pro zápis na konci souboru (připojení) bez odebrání značky konce souboru (EOF) před zápisem nových dat do souboru. Vytvoří soubor, pokud neexistuje. |
| **"r+"** | Otevírá se pro čtení i psaní. Soubor musí existovat. |
| **"w+"** | Otevře prázdný soubor pro čtení i zápis. Pokud soubor existuje, jeho obsah je zničen. |
| **"a+"** | Otevírá se pro čtení a připojení. Operace připojení zahrnuje odebrání značky EOF před zápisem nových dat do souboru. Značka EOF není obnovena po dokončení zápisu. Vytvoří soubor, pokud neexistuje. |

Používejte typy **"w"** a **"w+"** opatrně, protože mohou zničit existující soubory.

Při otevření souboru s typem přístupu **"a"** nebo **"a+",** všechny operace zápisu probíhají na konci souboru. Přestože ukazatel souboru lze přemístit pomocí [fseek](fseek-fseeki64.md) nebo [převíjení zpět](rewind.md), ukazatel souboru je vždy přesunuta zpět na konec souboru před provedením jakékoli operace zápisu. Existující data tedy nelze přepsat.

Režim **"a"** neodebere značku EOF před připojením k souboru. Po připojení došlo k ms-dos typ příkazu zobrazí pouze data až do původní značky EOF a žádná data připojená k souboru. Režim **"a+"** odebere značku EOF před připojením k souboru. Po připojení se v příkazu MS-DOS TYPE zobrazí všechna data v souboru. Režim **"a+"** je vyžadován pro připojení k souboru datového proudu, který je ukončen značkou CTRL+Z EOF.

Pokud je zadán typ přístupu **"r+"**, **"w+"** nebo **"a+",** je povoleno čtení i zápis (soubor je údajně otevřený pro "aktualizovat"). Však při přepínání mezi čtením a zápisem, musí být zasahující [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md), nebo [převíjení vzad](rewind.md) operace. Aktuální pozice může být určena pro [fsetpos](fsetpos.md) nebo [fseek](fseek-fseeki64.md) operace, pokud je to žádoucí. Kromě výše uvedených hodnot může být do řetězce *režimu* zahrnut jeden z následujících znaků, který určí režim překladu pro nové řádky.

|*modifikátor režimu*|Režim překladu|
|-|-|
| **t** | Otevřít v textovém (přeloženém) režimu. |
| **B** | Otevřít v binárním (nepřeloženém) režimu; překlady zahrnující znaky carriage-return a line feed jsou potlačeny. |

V režimu textu (přeloženo) jsou kombinace zpětného kanálu přepravy (CR-LF) přeloženy do znaků posuvu jednoho řádku (LF) na vstupu; Lf znaky jsou přeloženy do cr-LF kombinace na výstupu. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo pro zápis a čtení s **"a+"** zkontroluje run-time knihovna ctrl+z na konci souboru a pokud je to možné, odstraní ji. Důvodem je, protože pomocí [fseek](fseek-fseeki64.md) a [ftell](ftell-ftelli64.md) přesunout v rámci souboru může způsobit [fseek](fseek-fseeki64.md) chovat nesprávně blízko konce souboru. T **t** Možnost je rozšíření společnosti Microsoft, které by neměly být používány tam, kde je požadována přenositelnost ANSI.

Pokud **t** nebo **b** není uveden v *režimu*, výchozí režim překladu je definován globální proměnnou [_fmode](../../c-runtime-library/fmode.md). Pokud **t** nebo **b** je předponou argument, funkce se nezdaří a vrátí **NULL**.

Diskuse o texta a binární režimy naleznete [v tématu Text a binární režim soubor V/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h> \<nebo wchar.h>|

Konzola není podporována v aplikacích univerzální platformy Windows (UPW). Standardní popisovače datového proudu, které jsou přidruženy ke **konzole, stdin**, **stdout**a **stderr**, musí být přesměrovány před c run-time funkce je možné použít v aplikacích UPW. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
