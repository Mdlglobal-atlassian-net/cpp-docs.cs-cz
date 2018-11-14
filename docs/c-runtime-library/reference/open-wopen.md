---
title: _open, _wopen
ms.date: 11/04/2016
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
ms.openlocfilehash: 7ef28d6cafa0b74b50ee2c50ec380b8bd3aed79f
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327288"
---
# <a name="open-wopen"></a>_open, _wopen

Otevře se soubor. Tyto funkce jsou zastaralé, protože bezpečnější verze jsou k dispozici. Zobrazit [_sopen_s – _wsopen_s –](sopen-s-wsopen-s.md).

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
Druh operace povolena.

*pmode*<br/>
Režim oprávnění.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací popisovač souboru otevřený soubor. Návratová hodnota-1 označuje chybu; v takovém případě **errno** nastavena na jednu z následujících hodnot.

|Hodnota errno|Podmínka|
|-|-|
| **EACCES** | Se pokusil otevřít soubor jen pro čtení pro zápis souboru sdílení režimu neumožňuje zadanou operací nebo zadaná cesta je adresář. |
| **EEXIST** | **_O_CREAT** a **_O_EXCL** příznaků zadaných, ale *filename* již existuje. |
| **EINVAL** | Neplatný *oflag* nebo *pmode* argument. |
| **EMFILE** | Nejsou k dispozici žádné další popisovače souboru (je otevřeno příliš mnoho souborů). |
| **ENOENT** | Soubor nebo cesta nebyla nalezena. |

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Otevřít** otevře soubor určený parametrem funkce *filename* a připraví ho pro čtení nebo zápisu, jak jsou určené *oflag*. **_wopen –** je verze širokého znaku **_Otevřít**; *filename* argument **_wopen –** je širokoznaký řetězec. **_wopen –** a **_Otevřít** se jinak chovají stejně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen –**|**_Otevřít**|**_Otevřít**|**_wopen**|

*oflag* výraz celého čísla je vytvořen z jednoho nebo více z následujících konstant manifestu nebo konstantní kombinacích, které jsou definovány v \<fcntl.h >.

|*oflag* konstanty|Chování|
|-|-|
| **_O_APPEND** | Přesune ukazatel na soubor na konec souboru před každou operaci zápisu. |
| **_O_BINARY** | Otevře soubor v binárním (nepřeloženém) režimu. (Viz [fopen](fopen-wfopen.md) popis binárním režimu.) |
| **_O_CREAT** | Vytvoří soubor a otevře jej pro zápis. Nemá žádný vliv, pokud souboru určeném *filename* existuje. *Pmode* argument je požadován při **_O_CREAT** určena. |
| **_O_CREAT** &AMP;#124; **_O_SHORT_LIVED** | Vytvoří soubor jako dočasný a pokud je to možné není vyprázdnit na disk. *Pmode* argument je požadován při **_O_CREAT** určena. |
| **_O_CREAT** &AMP;#124; **_O_TEMPORARY** | Vytvoří soubor jako dočasný; Při zavření posledního popisovač souboru, odstraní se tento soubor. *Pmode* argument je požadován při **_O_CREAT** určena. |
| **_O_CREAT**&AMP;#124; ` _O_EXCL` | Vrací chybovou hodnotu, pokud soubor určený parametrem *filename* existuje. Platí pouze při použití s **_O_CREAT**. |
| **_O_NOINHERIT** | Zabraňuje vytváření popisovače sdílený soubor. |
| **_O_RANDOM** | Určuje, že je mezipaměť optimalizovaná pro, ale nikoliv omezená, náhodný přístup z disku. |
| **_O_RDONLY** | Otevře se soubor jen pro čtení. Nelze zadat s **_O_RDWR** nebo **_O_WRONLY**. |
| **_O_RDWR** | Otevře soubor pro čtení i zápis. Nelze zadat s **_O_RDONLY** nebo **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Určuje, že je mezipaměť optimalizovaná pro, ale nikoliv omezená, sekvenčním přístupem z disku. |
| **_O_TEXT** | Otevře soubor v textovém (přeloženém) režimu. (Další informace najdete v tématu [textového a binárního režimu souboru vstupně-výstupních operací](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [fopen](fopen-wfopen.md).) |
| **_O_TRUNC** | Otevře soubor a zkrátí ho na hodnotu nula length; soubor musí mít oprávnění k zápisu. Nelze zadat s **_O_RDONLY**. **_O_TRUNC** použít s **_O_CREAT** otevře existující soubor nebo vytvoří soubor. **Poznámka:** **_O_TRUNC** příznak odstraní obsah zadaného souboru. |
| **_O_WRONLY** | Otevře soubor pro zápis. Nelze zadat s **_O_RDONLY** nebo **_O_RDWR**. |
| **_O_U16TEXT** | Otevře soubor v režimu Unicode UTF-16. |
| **_O_U8TEXT** | Otevře soubor v režimu Unicode UTF-8. |
| **_O_WTEXT** | Otevře soubor v režimu Unicode. |

Pokud chcete zadat režim přístupu k souboru, je nutné zadat buď **_O_RDONLY**, **_O_RDWR**, nebo **_O_WRONLY**. Není žádná výchozí hodnota pro režim přístupu.

Pokud **_O_WTEXT** slouží k otevření souboru pro čtení, **_Otevřít** přečte na začátek souboru a vyhledá pořadí bajtů (BOM). Pokud BOM, soubor je považován za kódování UTF-8 nebo UTF-16LE, v závislosti na BOM. Pokud není přítomno BOM, soubor se považuje ANSI. Při otevření souboru pro zápis s použitím **_O_WTEXT**, použije se UTF-16. Bez ohledu na to žádné předchozí nastavení nebo bajt značka pro pořadí, pokud **_O_U8TEXT** je používají, vždy otevření souboru jako UTF-8; Pokud **_O_U16TEXT** se používá, soubor se vždy otevře jako UTF-16.

Když je soubor otevřen v režimu Unicode s použitím **_O_WTEXT**, **_O_U8TEXT**, nebo **_O_U16TEXT**, zadejte funkce převede data, která je pro čtení ze souboru o datech UTF-16 Uložit jako typ **wchar_t**. Funkce, které se zápis do souboru otevřeném v režimu Unicode očekávat vyrovnávacích pamětí, které obsahují data UTF-16 uložené jako typ **wchar_t**. Pokud soubor zakódován pomocí kódování UTF-8, je při zápisem a kódování UTF-8 obsah souboru je přeložit na UTF-16, když je pro čtení dat UTF-16 přeložit na UTF-8. Pokus o čtení nebo zápisu lichý počet bajtů v režimu Unicode způsobí chybu ověření parametru. Pro čtení nebo zápis dat, která je uložena ve svém programu jako UTF-8, použijte namísto režimu Unicode textová nebo binární režim souboru. Zodpovídáte za všechny požadované kódování překladu.

Pokud **_Otevřít** volána s **_O_WRONLY** | **_O_APPEND** (režimu připojení) a **_O_WTEXT**, **_O_ U16TEXT**, nebo **_O_U8TEXT**, nejprve se pokusí otevřít soubor pro čtení a zápis, přečtěte si BOM a pak ho znovu otevřít pro zápis. Pokud otevřete soubor pro čtení a zápis selže, otevře soubor pro zápis a používá výchozí hodnota pro nastavení režimu Unicode.

Při použití dvou nebo více konstant manifestu do formuláře *oflag* argument konstanty jsou kombinované pomocí bitového operátoru OR – operátor ( **&#124;** ). Informace o režimech binární a textová, naleznete v tématu [textového a binárního režimu souboru vstupně-výstupních operací](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

*Pmode* se vyžaduje jenom v případě **_O_CREAT** určena. Pokud soubor již existuje, *pmode* se ignoruje. V opačném případě *pmode* určuje nastavení oprávnění souboru, které jsou nastaveny při zavření poprvé nový soubor. **_Otevřít** použije aktuální masku souboru oprávnění k *pmode* předtím, než jsou oprávnění. (Další informace najdete v tématu [_umask –](umask.md).) *pmode* je výraz celého čísla, která obsahuje jednu nebo obě z následujících konstant manifestu, které jsou definovány v \<sys\stat.h >.

|*pmode*|Význam|
|-|-|
| **_S_IREAD** | Povoleno jen čtení. |
| **_S_IWRITE** | Zápis povolen. (V podstatě povoluje čtení a zápis.) |
| **_S_IREAD** &AMP;#124; **_S_IWRITE** | Čtení a zápis povolen. |

Když jsou uvedeny oba konstanty, jsou spojeny pomocí bitového operátoru OR – operátor ( **&#124;** ). Ve Windows jsou čitelné; všechny soubory oprávnění jen pro zápis není k dispozici. Proto režimy **_S_IWRITE** a **_S_IREAD** | **_S_IWRITE** jsou ekvivalentní.

Pokud jiná hodnota než kombinace **_S_IREAD** a **_S_IWRITE** je určená pro *pmode*– i v případě, že by zadejte platný *pmode*v jiném operačním systému, nebo pokud je některá hodnota jiné než povolené maximum *oflag* zadané hodnoty, funkce generuje kontrolní výraz v režimu ladění a vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_Otevřít**|\<IO.h >|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|
|**_wopen**|\<IO.h > nebo \<wchar.h >|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|

**_Otevřít** a **_wopen –** jsou rozšíření společnosti Microsoft. Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také:

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
