---
title: freopen –, _wfreopen – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- freopen
- _wfreopen
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
- _wfreopen
- _tfreopen
- freopen
dev_langs:
- C++
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e371076ce095116930908174d4fa29e9cfd876e5
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="freopen-wfreopen"></a>freopen, _wfreopen

Znovu přiřadí ukazatel souboru. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [freopen_s –, _wfreopen_s –](freopen-s-wfreopen-s.md).

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

*Cesta*<br/>
Cesta k novému souboru.

*Režim*<br/>
Typ přístupu povolena.

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na nově otevřený soubor. Pokud dojde k chybě, původní soubor se zavře a funkce vrátí hodnotu **NULL** hodnota ukazatele s hodnotou. Pokud *cesta*, *režimu*, nebo *datového proudu* je ukazatel s hodnotou null, nebo pokud *filename* je prázdný řetězec, tyto funkce vyvolání neplatný parametr obslužné rutiny, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátit **NULL**.

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.

## <a name="remarks"></a>Poznámky

Bezpečnější verzích tyto funkce neexistuje, najdete v části [freopen_s –, _wfreopen_s –](freopen-s-wfreopen-s.md).

**Freopen –** funkce zavře soubor aktuálně přidružen *datového proudu* a znovu přidělí *datového proudu* do souboru určeného *cestu*. **_wfreopen –** je verze široká charakterová **_freopen**; *cesta* a *režimu* argumenty, které mají **_wfreopen –** jsou široká charakterová řetězce. **_wfreopen –** a **_freopen** chovat jinak shodně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen –**|**freopen –**|**freopen –**|**_wfreopen**|

**freopen –** se obvykle používá pro přesměrování předem otevřených souborů **stdin –**, **stdout**, a **stderr** na soubory zadané uživatelem. Nový soubor přidružený k *datového proudu* je otevřen s *režimu*, což je řetězec znaků určující typ přístupu, které jsou požadované pro soubor, následujícím způsobem:

|*Režim*|Access|
|-|-|
**"r"**|Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, **freopen –** volání selže.
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
|**freopen –**|\<stdio.h>|
|**_wfreopen**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, **stdin –**, **stdout**, a **stderr**, musí být přesměrována C běhové funkce mohli používat v aplikacích pro UPW . Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
