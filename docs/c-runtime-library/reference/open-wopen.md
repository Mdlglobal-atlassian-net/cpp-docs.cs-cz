---
title: _open, _wopen
ms.date: 11/04/2016
api_name:
- _open
- _wopen
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
- _wopen
- _topen
- _open
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
ms.openlocfilehash: 4ce6e9aebe5d058143ad737f9c9db5bb68b30b1f
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150720"
---
# <a name="_open-_wopen"></a>_open, _wopen

Otevře soubor. Tyto funkce jsou zastaralé, protože jsou k dispozici bezpečnější verze. viz [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md).

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

*Bitmap*<br/>
Název souboru.

*oflag*<br/>
Druh povolených operací.

*pmode*<br/>
Režim oprávnění.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí popisovač souboru pro otevřený soubor. Návratová hodnota-1 označuje chybu. v takovém případě je **errno** nastaveno na jednu z následujících hodnot.

|hodnota errno|Podmínka|
|-|-|
| **EACCES** | Byl proveden pokus o otevření souboru určeného jen pro čtení pro zápis, režim sdílení souborů nepovoluje zadané operace, nebo je daná cesta adresářem. |
| **EEXIST** | Byly zadány příznaky **_O_CREAT** a **_O_EXCL** , ale *název souboru* již existuje. |
| **EINVAL** | Neplatný argument *oflag* nebo *pmode* |
| **EMFILE** | Nejsou k dispozici žádné další popisovače souboru (je otevřeno příliš mnoho souborů). |
| **ENOENT** | Soubor nebo cesta nebyla nalezena. |

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_open** otevře soubor určený parametrem *filename* a připraví ho pro čtení nebo zápis, jak je uvedeno v *oflag*. **_wopen** je verze **_open**s velkým znakem; Argument *filename* pro **_wopen** je řetězec s velkým znakem. **_wopen** a **_open** se chovají identicky jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen**|**_open**|**_open**|**_wopen**|

*oflag* je celočíselný výraz tvořený jednou nebo více následujícími konstantami manifestu nebo konstantními kombinacemi, které jsou definovány v \<fcntl. h >.

|konstanta *oflag*|Chování|
|-|-|
| **_O_APPEND** | Přesune ukazatel souboru na konec souboru před každou operací zápisu. |
| **_O_BINARY** | Otevře soubor v binárním (nepřeloženém) režimu. (Popis binárního režimu najdete v tématu [fopen](fopen-wfopen.md) .) |
| **_O_CREAT** | Vytvoří soubor a otevře jej pro zápis. Nemá žádný vliv, pokud soubor určený parametrem *filename* existuje. Je-li zadán **_O_CREAT** , je vyžadován argument *pmode* . |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | Vytvoří soubor jako dočasný a pokud je to možné, nebude se vyprázdnit na disk. Je-li zadán **_O_CREAT** , je vyžadován argument *pmode* . |
| **_O_CREAT** &#124; **_O_TEMPORARY** | Vytvoří soubor jako dočasný; po zavření posledního deskriptoru souboru se soubor odstraní. Je-li zadán **_O_CREAT** , je vyžadován argument *pmode* . |
| **_O_CREAT** &#124; `_O_EXCL` | Vrací hodnotu chyby, pokud soubor určený parametrem *filename* existuje. Platí pouze při použití s **_O_CREAT**. |
| **_O_NOINHERIT** | Zabraňuje vytvoření popisovače sdíleného souboru. |
| **_O_RANDOM** | Určuje, že ukládání do mezipaměti je optimalizované pro, ale ne omezené na, náhodný přístup z disku. |
| **_O_RDONLY** | Otevře soubor jen pro čtení. Nelze zadat pomocí **_O_RDWR** nebo **_O_WRONLY**. |
| **_O_RDWR** | Otevře soubor pro čtení i zápis. Nelze zadat pomocí **_O_RDONLY** nebo **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Určuje, že ukládání do mezipaměti je optimalizované pro, ale ne omezené na, sekvenční přístup z disku. |
| **_O_TEXT** | Otevře soubor v textovém (přeloženém) režimu. (Další informace najdete v tématu [vstupně-výstupní operace se soubory v textovém a binárním režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [fopen](fopen-wfopen.md).) |
| **_O_TRUNC** | Otevře soubor a zkrátí ho na nulovou délku. soubor musí mít oprávnění k zápisu. Nelze zadat pomocí **_O_RDONLY**. **_O_TRUNC** použito s **_O_CREAT** otevře existující soubor nebo vytvoří soubor. **Poznámka:** Příznak **_O_TRUNC** zničí obsah zadaného souboru. |
| **_O_WRONLY** | Otevře soubor pouze pro zápis. Nelze zadat pomocí **_O_RDONLY** nebo **_O_RDWR**. |
| **_O_U16TEXT** | Otevře soubor v režimu Unicode UTF-16. |
| **_O_U8TEXT** | Otevře soubor v režimu Unicode UTF-8. |
| **_O_WTEXT** | Otevře soubor v režimu Unicode. |

Chcete-li určit režim přístupu k souboru, je nutné zadat buď **_O_RDONLY**, **_O_RDWR**nebo **_O_WRONLY**. Neexistuje žádná výchozí hodnota pro režim přístupu.

Pokud se k otevření souboru pro čtení používá **_O_WTEXT** , **_open** přečte začátek souboru a vyhledá znak pořadí bajtů (BOM). Pokud je k dispozici BOM, je soubor považován za UTF-8 nebo UTF-16LE v závislosti na kusovníku. Pokud není k dispozici žádný kusovník, bude soubor považován za ANSI. Když je soubor otevřen pro zápis pomocí **_O_WTEXT**, použije se UTF-16. Bez ohledu na předchozí nastavení nebo označení pořadí bajtů, pokud se používá **_O_U8TEXT** , soubor se vždycky otevře jako UTF-8; Pokud se používá **_O_U16TEXT** , soubor se vždycky otevře jako UTF-16.

Když se soubor otevře v režimu Unicode pomocí **_O_WTEXT**, **_O_U8TEXT**nebo **_O_U16TEXT**, funkce Input přeloží data načtená ze souboru do dat UTF-16 uložených jako typ **wchar_t**. Funkce, které zapisují do souboru otevřeného v režimu Unicode, očekávají vyrovnávací paměti, které obsahují data UTF-16 uložená jako typ **wchar_t**. Pokud je soubor kódovaný jako UTF-8, data UTF-16 se při zápisu přeloží na UTF-8 a obsah zakódovaný v kódování UTF-8 se převede na UTF-16 při čtení. Při pokusu o čtení nebo zápis lichého počtu bajtů v režimu Unicode dojde k chybě ověření parametru. Chcete-li číst nebo zapisovat data uložená v programu jako UTF-8, místo režimu Unicode použijte textový nebo binární souborový režim. Zodpovídáte za všechny požadované překlady kódování.

Pokud **_open** je zavolána _open **_O_WRONLY** |  **_O_APPEND** (režim připojení) a **_O_WTEXT**, **_O_U16TEXT**nebo **_O_U8TEXT**, nejprve se pokusí otevřít soubor pro čtení a zápis, přečtěte si kusovník a pak ho znovu otevřít pro zápis. Pokud soubor otevíráte pro čtení a zápis, otevře se soubor jenom pro zápis a použije se výchozí hodnota pro nastavení režimu Unicode.

V případě použití dvou nebo více konstant manifestu k vytvoření argumentu *oflag* jsou konstanty kombinovány s bitovým operátorem OR ( **&#124;** ). Diskuzi o binárních a textových režimech najdete v tématu [vstupně-výstupní operace se soubory textového a binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Argument *pmode* je vyžadován pouze v případě, že je zadána **_O_CREAT** . Pokud soubor již existuje, *pmode* se ignoruje. V opačném případě *pmode* určuje nastavení oprávnění souboru, která jsou nastavena při prvním zavření nového souboru. **_open** aplikuje aktuální masku oprávnění souboru na *pmode* před nastavením oprávnění. (Další informace najdete v tématu [_umask](umask.md).) *pmode* je celočíselný výraz, který obsahuje jednu nebo obě následující konstanty manifestu, které jsou definovány v \<sys\stat.h >.

|*pmode*|Význam|
|-|-|
| **_S_IREAD** | Povoluje se pouze čtení. |
| **_S_IWRITE** | Zápis povolen. (V důsledku toho povoluje čtení a zápis.) |
| **_S_IREAD** &#124; **_S_IWRITE** | Čtení a zápis jsou povoleny. |

Jsou-li obě konstanty zadány, jsou spojeny s bitovým operátorem OR ( **&#124;** ). V systému Windows jsou všechny soubory čitelné; oprávnění pouze pro zápis nejsou k dispozici. Proto jsou režimy **_S_IWRITE** a **_S_IREAD** |  **_S_IWRITE** ekvivalentní.

Pokud je pro *pmode*zadána jiná hodnota než některá kombinace **_S_IREAD** a **_S_IWRITE** , a to i v případě, že by zadal platný *pmode* v jiném operačním systému, nebo pokud je zadána jiná jiná hodnota než povolené hodnoty *oflag* , funkce vygeneruje kontrolní výraz v režimu ladění a vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_open**|\<IO. h >|\<fcntl. h >, \<sys\types.h >, \<sys\stat.h >|
|**_wopen**|\<IO. h > nebo \<WCHAR. h >|\<fcntl. h >, \<sys\types.h >, \<sys\stat.h >|

**_open** a **_Wopen** jsou rozšíření společnosti Microsoft. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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
