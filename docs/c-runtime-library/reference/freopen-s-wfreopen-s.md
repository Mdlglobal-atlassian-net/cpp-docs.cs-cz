---
title: freopen_s –, _wfreopen_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04b136a46672838fd6ee554668353d92796abc7e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="freopens-wfreopens"></a>freopen_s, _wfreopen_s

Znovu přiřadí ukazatel souboru. Tyto verze nástroje [freopen –, _wfreopen –](freopen-wfreopen.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Typ přístupu povolena.

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací kód chyby. Dojde-li k chybě, je původní soubor uzavřen.

## <a name="remarks"></a>Poznámky

**Freopen_s –** funkce zavře soubor aktuálně přidružen *datového proudu* a znovu přidělí *datového proudu* do souboru určeného *cesta* . **_wfreopen_s –** je verze široká charakterová **_freopen_s**; *cesta* a *režimu* argumenty, které mají **_wfreopen_s –** jsou široká charakterová řetězce. **_wfreopen_s –** a **_freopen_s** chovat jinak shodně.

Pokud platí jedna z *pFile*, *cesta*, *režimu*, nebo *datového proudu* jsou **NULL**, nebo pokud *cesta* je prázdný řetězec, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátit **einval –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s –**|**freopen_s –**|**freopen_s –**|**_wfreopen_s**|

**freopen_s –** se obvykle používá pro přesměrování předem otevřených souborů **stdin –**, **stdout**, a **stderr** na soubory zadané uživatelem. Nový soubor přidružený k *datového proudu* je otevřen s *režimu*, což je řetězec znaků určující typ přístupu, které jsou požadované pro soubor, následujícím způsobem:

|*Režim*|Access|
|-|-|
**"r"**|Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, **freopen_s –** volání selže.
**"w"**|Otevře se prázdný soubor pro zápis. Pokud je daný soubor existuje, její obsah se způsobem zničena.
**"a"**|Otevře pro zápis na konec souboru (připojení) bez odebrání značky end souboru (EOF) před nová data jsou zapsána do souboru. Pokud neexistuje, vytvoří soubor.
**"r +"**|Otevře pro čtení i zápis. Soubor musí existovat.
**"w +"**|Otevře se prázdný soubor pro čtení i zápis. Pokud soubor existuje, její obsah se způsobem zničena.
**"+"**|Otevře pro čtení a připojením. Připojování operaci zahrnuje odebrání značky EOF před nová data jsou zapsána do souboru. Po dokončení zápisu, nedojde k obnovení EOF značky. Pokud neexistuje, vytvoří soubor.

Použití **"w"** a **"w +"** typy opatrně, protože zničí existující soubory.

Při otevření souboru s **"a"** nebo **"+"** přistupovat typu, všechny zápisu operace dojde na konci souboru. I když ukazatele souboru můžete změnit jejich umístění pomocí [fseek](fseek-fseeki64.md) nebo [rewind](rewind.md), ukazatele souboru je vždycky přesunuta zpět na konec souboru před všechny zápisu operace provádí. Žádná existující data proto nemohou být přepsána.

**"A"** režimu neodebere značky EOF před připojením k souboru. Po připojení došlo k chybě, MS-DOS typ příkazu se zobrazí pouze data až původní EOF značky a není žádná data připojen k souboru. **"+"** Režimu odebrat značky EOF před připojením k souboru. Po připojení, zobrazí příkaz MS-DOS typ všechna data v tomto souboru. **"+"** Režim je vyžadován pro připojení do datového proudu souboru, který je byla ukončena s CTRL + Z EOF značky.

Když **"r +"**, **"w +"**, nebo **"+"** byl zadán typ přístupu, jsou povoleny pro čtení i zápis (soubor říká, že je třeba otevřít pro "update"). Ale při přepínání mezi čtení a zápis, musí být uplynulého [fsetpos –](fsetpos.md), [fseek](fseek-fseeki64.md), nebo [rewind](rewind.md) operaci. Aktuální pozice lze [fsetpos –](fsetpos.md) nebo [fseek](fseek-fseeki64.md) operace, v případě potřeby. Kromě výše uvedené hodnoty, jednu z následujících znaků může být součástí *režimu* řetězec k určení režim překladu pro nové řádky.

|*režim* – modifikátor|Režim překladu|
|-|-|
**t**|Otevřete v textu (přeložit) režimu.
**b**|Otevřete v binárním režimu (nepřeložený); jsou potlačovány překlady zahrnující znaky CR a konce řádku.

V režimu textových (přeložit) jsou kombinace vrátit-nový řádek (CR-LF) znaků CR přeložit na jednu nový řádek (LF) znaků na vstup; LF znaky jsou převedeny na znaky CR LF kombinace na výstup. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřen pro čtení nebo zápis a čtení s **"+"**, běhové knihovny kontroluje CTRL + Z na konci souboru a odstraní ji, pokud je to možné. To je provést, protože používá [fseek](fseek-fseeki64.md) a [ftell –](ftell-ftelli64.md) přesunout v souboru může způsobit [fseek](fseek-fseeki64.md) chovat nesprávně blíží konec souboru. **t** možnost je rozšířením Microsoft, které by se neměla používat, kde je žádoucí přenositelnost ANSI.

Pokud **t** nebo **b** není uveden v *režimu*, je výchozí režim překladu definované globální proměnná [_fmode –](../../c-runtime-library/fmode.md). Pokud **t** nebo **b** předponou argument, funkce selže a vrátí je **NULL**.

Informace o textovém a binárním režimu, najdete v části [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**freopen_s –**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, **stdin –**, **stdout**, a **stderr**, musí být přesměrována C běhové funkce mohli používat v aplikacích pro UPW . Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
