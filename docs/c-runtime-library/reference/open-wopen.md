---
title: _Otevřít _wopen – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _open
- _wopen
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
- _wopen
- _topen
- _open
dev_langs:
- C++
helpviewer_keywords:
- opening files, for file I/O
- topen function
- _open function
- _topen function
- _wopen function
- files [C++], opening
- wopen function
- open function
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf1d5cca5f729e0b3e2ee55cd6d8778450bdead1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405338"
---
# <a name="open-wopen"></a>_open, _wopen

Otevře soubor. Tyto funkce jsou zastaralé, protože bezpečnější verze jsou k dispozici. v tématu [_sopen_s –, _wsopen_s –](sopen-s-wsopen-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _open(
   const char *filename,
   int oflag [,
   int pmode]
);
int _wopen(
   const wchar_t *filename,
   int oflag [,
   int pmode]
);
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Název souboru.

*oflag*<br/>
Druh operace povoleny.

*pmode*<br/>
Režim oprávnění.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí, vrátí se popisovač souboru pro otevřený soubor. Vrácená hodnota -1 označuje chybu; v takovém případě **errno** nastaven na jednu z následujících hodnot.

|errno – hodnota|Podmínka|
|-|-|
**EACCES –**|Se pokusil otevřít jen pro čtení souboru pro zápis souboru režimu sdílení neumožňuje zadané operace, nebo zadaná cesta je adresář.
**EEXIST –**|**_O_creat –** a **_o_excl –** příznaků zadaných, ale *filename* již existuje.
**EINVAL –**|Neplatný *oflag* nebo *pmode* argument.
**EMFILE –**|Žádné další popisovače souborů, které jsou k dispozici (je otevřeno příliš mnoho souborů).
**ENOENT –**|Soubor nebo cesta nebyla nalezena.

Další informace o těchto a dalších návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Otevřít** funkce otevře soubor určený touto *filename* a připraví ho pro čtení nebo zápisu podle specifikace *oflag*. **_wopen –** je verze široká charakterová **_Otevřít**; *filename* argument **_wopen –** je široká charakterová řetězec. **_wopen –** a **_Otevřít** chovat jinak shodně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen –**|**_Otevřít**|**_Otevřít**|**_wopen**|

*oflag* je vytvořen výraz celého čísla z jedné nebo více následujících manifestu konstanty nebo konstantní kombinace, které jsou definovány v \<fcntl.h >.

|*oflag* konstant|Chování|
|-|-|
**_O_APPEND –**|Přesune ukazatele souboru na konec souboru před každou operaci zápisu.
**_O_BINARY –**|Soubor se otevře v binárním režimu (nepřeložený). (Viz [fopen –](fopen-wfopen.md) popis binárního režimu.)
**_O_CREAT –**|Soubor se vytvoří a otevře ji pro zápis. Nemá vliv, pokud soubor určeného *filename* existuje. *Pmode* argument je požadován při **_o_creat –** je zadán.
**_O_CREAT –** &AMP;#124; **_O_SHORT_LIVED**|Vytvoří soubor jako dočasné a pokud je to možné není vyprázdnit na disk. *Pmode* argument je požadován při **_o_creat –** je zadán.
**_O_CREAT –** &AMP;#124; **_O_TEMPORARY**|Vytvoří soubor jako dočasné; soubor je odstraněn při zavření posledního popisovače souborů. *Pmode* argument je požadován při **_o_creat –** je zadán.
**_O_CREAT –**&AMP;#124; ` _O_EXCL`|Vrací hodnotu chyby, pokud soubor určený touto *filename* existuje. Platí pouze při použití s **_o_creat –**.
**_O_NOINHERIT**|Brání vytváření sdílený soubor popisovače.
**_O_RANDOM**|Určuje, že ukládání do mezipaměti je optimalizovaná pro, ale není omezena na náhodný přístup z disku.
**_O_RDONLY –**|Otevře se soubor jen pro čtení. Nelze zadat u **_o_rdwr –** nebo **_o_wronly –**.
**_O_RDWR –**|Otevře soubor pro čtení i zápis. Nelze zadat u **_o_rdonly –** nebo **_o_wronly –**.
**_O_SEQUENTIAL**|Určuje, že ukládání do mezipaměti je optimalizovaná pro, ale není omezen na, sekvenční přístup z disku.
**_O_TEXT –**|Otevře soubor v režimu textových (přeložit). (Další informace najdete v tématu [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [fopen –](fopen-wfopen.md).)
**_O_TRUNC –**|Otevře soubor a zkrátí ho nule length; soubor musí mít oprávnění k zápisu. Nelze zadat u **_o_rdonly –**. **_O_trunc –** použít s **_o_creat –** otevře existující soubor nebo soubor se vytvoří. **Poznámka:** **_o_trunc –** příznak zničí obsah zadaného souboru.
**_O_WRONLY –**|Otevře soubor pro zápis pouze. Nelze zadat u **_o_rdonly –** nebo **_o_rdwr –**.
**_O_U16TEXT**|Otevře soubor v režimu Unicode UTF-16.
**_O_U8TEXT**|Otevře soubor v režimu Unicode UTF-8.
**_O_WTEXT**|Otevře soubor v režimu Unicode.

Pokud chcete nastavit režim souboru přístup, je nutné zadat buď **_o_rdonly –**, **_o_rdwr –**, nebo **_o_wronly –**. Neexistuje žádná výchozí hodnota pro režim přístupu.

Pokud **_O_WTEXT** slouží k otevření souboru pro čtení, **_Otevřít** čte na začátek souboru a kontroluje značka pořadí bajtů (BOM). Pokud je Kusovník, soubor je považována za UTF-8 nebo UTF-16LE, v závislosti na Kusovníku. Pokud je k dispozici žádné BOM, soubor je považována za ANSI. Při otevření souboru pro zápis pomocí **_O_WTEXT**, použije se ve formátu UTF-16. Bez ohledu na to žádné předchozí nastavení nebo bajt pořadí značky, pokud **_O_U8TEXT** se používá, vždy otevření souboru ve formátu UTF-8; Pokud **_O_U16TEXT** se používá, soubor se vždy otevře jako UTF-16.

Při otevření souboru v režimu Unicode pomocí **_O_WTEXT**, **_O_U8TEXT**, nebo **_O_U16TEXT**, vstupní funkce převede data, která je pro čtení ze souboru do data ve formátu UTF-16 Uložit jako typ **wchar_t**. Funkce, které zapisovat do souboru otevřeného v režimu Unicode očekávat vyrovnávací paměti, které obsahují data ve formátu UTF-16 uložené jako typ **wchar_t**. Pokud soubor zakódován pomocí kódování UTF-8, je při je zapsán a kódování UTF-8 obsah souboru je přeložit na UTF-16, když je pro čtení dat ve formátu UTF-16 přeložit na UTF-8. Pokus o čtení nebo zápisu lichý počet bajtů v režimu Unicode způsobí, že chyba ověření parametru. Číst nebo zapisovat data, která je uložená v programu jako UTF-8, použijte místo režim Unicode režim textových nebo binárních souborů. Jste zodpovědní za jakékoli požadované kódování překlad.

Pokud **_Otevřít** je volán s **_o_wronly –** | **_o_append –** (režim připojení) a **_O_WTEXT**, **_O_ U16TEXT**, nebo **_O_U8TEXT**, nejprve se pokusí otevřít soubor pro čtení a zápis, přečtěte si Kusovníku a pak ho znovu otevřít pro zápis pouze. Pokud otevírání souboru pro čtení a zápis selže, otevře soubor pro zápis pouze a používá výchozí hodnota pro nastavení režimu kódování Unicode.

Při použití dvou nebo více manifestu konstanty do formuláře *oflag* argument, konstanty spolu se operátoru bitové operace OR ( **&#124;** ). Informace z binárního souboru a text režimů, naleznete v [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

*Pmode* se vyžaduje jenom v případě **_o_creat –** je zadán. Pokud soubor již existuje, *pmode* je ignorována. V opačném *pmode* určuje nastavení oprávnění souborů, které lze nastavit při zavření první nový soubor. **_Otevřít** použije aktuální maska souboru oprávnění k *pmode* předtím, než jsou oprávnění nastavena. (Další informace najdete v tématu [_umask –](umask.md).) *pmode* je použit celočíselný výraz, který obsahuje jedno nebo obě následující manifestu konstanty, které jsou definovány v \<sys\stat.h >.

|*pmode*|Význam|
|-|-|
**_S_IREAD –**|Pouze čtení povolené.
**_S_IWRITE –**|Zápis povolen. (Ve skutečnosti povoluje čtení a zápis.)
**_S_IREAD –** &AMP;#124; **_S_IWRITE –**|Čtení a zápis povolen.

Pokud jsou zadány oba konstanty, jsou spojeny pomocí operátoru bitové operace OR ( **&#124;** ). V systému Windows jsou všechny soubory čitelný; oprávnění jen pro zápis není k dispozici. Proto režimů **_s_iwrite –** a **_s_iread –** | **_s_iwrite –** odpovídají.

Pokud hodnota než některých kombinací **_s_iread –** a **_s_iwrite –** je zadán pro *pmode*– i v případě, že by zadejte platný *pmode*v jiném operačním systému, nebo pokud je některá hodnota jiné než povolené maximum *oflag* zadané hodnoty, funkce generuje kontrolní výrazy v režimu ladění a vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, funkce vrátí hodnotu -1 a nastaví je povoleno spuštění **errno** k **einval –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_Otevřít**|\<IO.h >|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|
|**_wopen**|\<IO.h > nebo \<wchar.h >|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|

**_Otevřít** a **_wopen –** jsou rozšíření Microsoft. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_open.c
// compile with: /W3
/* This program uses _open to open a file
* named CRT_OPEN.C for input and a file named CRT_OPEN.OUT
* for output. The files are then closed.
*/
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int fh1, fh2;

   fh1 = _open( "CRT_OPEN.C", _O_RDONLY ); // C4996
   // Note: _open is deprecated; consider using _sopen_s instead
   if( fh1 == -1 )
      perror( "Open failed on input file" );
   else
   {
      printf( "Open succeeded on input file\n" );
      _close( fh1 );
   }

   fh2 = _open( "CRT_OPEN.OUT", _O_WRONLY | _O_CREAT, _S_IREAD |
                            _S_IWRITE ); // C4996
   if( fh2 == -1 )
      perror( "Open failed on output file" );
   else
   {
      printf( "Open succeeded on output file\n" );
      _close( fh2 );
   }
}
```

### <a name="output"></a>Výstup

```Output
Open succeeded on input file
Open succeeded on output file
```

## <a name="see-also"></a>Viz také

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
