---
title: _sopen, _wsopen
ms.date: 4/2/2020
api_name:
- _sopen
- _wsopen
- _o__sopen
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
- _wsopen
- wsopen
- _sopen
- _tsopen
helpviewer_keywords:
- sopen function
- sharing files
- opening files, for sharing
- _sopen function
- wsopen function
- files [C++], opening
- files [C++], sharing
- _wsopen function
ms.assetid: a9d4cccf-06e9-414d-96fa-453fca88cc1f
ms.openlocfilehash: 0ee788823b62d97cdc81e901a812ba25f40359e9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356405"
---
# <a name="_sopen-_wsopen"></a>_sopen, _wsopen

Otevře soubor pro sdílení. K dispozici jsou bezpečnější verze těchto funkcí: viz [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _sopen(
   const char *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
int _wsopen(
   const wchar_t *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
```

### <a name="parameters"></a>Parametry

*Název_souboru*<br/>
Název souboru.

*ovlajková vlajka*<br/>
Druh operací povolených.

*švaho*<br/>
Druh sdílení povoleno.

*pmode*<br/>
Nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí popisovač souboru pro otevřený soubor.

Pokud *název_souboru* nebo *oflag* je **ukazatel NULL,** nebo pokud *oflag* nebo *sflag* není v platném rozsahu hodnot, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí -1 a nastavit **errno** na jednu z následujících hodnot.

|hodnota errno|Podmínka|
|-|-|
| **ACCACCES** | Daná cesta je adresář nebo je soubor jen pro čtení, ale došlo k pokusu o operaci otevřeného zápisu. |
| **EEXIST** | **byly** zadány příznaky _O_CREAT a **_O_EXCL,** ale *název souboru* již existuje. |
| **EINVAL** | Neplatný *argument oflag* nebo *shflag.* |
| **SOUBOR EM** | Nejsou k dispozici žádné další popisovače souborů. |
| **ENOENT** | Soubor nebo cesta nebyla nalezena. |

Další informace o těchto a dalších návratových kódech naleznete [v tématech _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_sopen** otevře soubor určený *názvem souboru* a připraví soubor pro sdílené čtení nebo zápis, jak je definováno *oflag* a *shflag*. **_wsopen** je širokoznaková verze **_sopen**; argument *název souboru,* který **má _wsopen,** je řetězec s širokým znakem. **_wsopen** a **_sopen** se chovají stejně jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

Výraz celé číslo *oflag* je tvořen kombinací jedné nebo více následujících konstant \<manifestu, které jsou definovány v souboru fcntl.h>. Pokud argument *oflag*tvoří dvě nebo více konstant , jsou kombinovány s bitovým operátorem OR ( **&#124;** ).

|*opříznaková* konstanta|Chování|
|-|-|
| **_O_APPEND** | Přesune ukazatel souboru na konec souboru před každou operací zápisu. |
| **_O_BINARY** | Otevře soubor v binárním (nepřeloženém) režimu. (Popis binárního režimu naleznete v [části fopen.)](fopen-wfopen.md) |
| **_O_CREAT** | Vytvoří soubor a otevře jej pro psaní. Nemá žádný vliv, pokud existuje soubor určený *názvem souboru.* Argument *pmode* je vyžadován, pokud je zadán **_O_CREAT.** |
| **_O_CREAT** **&#124; _O_SHORT_LIVED** | Vytvoří soubor jako dočasný a pokud možno není vyprázdněna na disk. Argument *pmode* je vyžadován, pokud je zadán **_O_CREAT.** |
| **_O_CREAT** **&#124; _O_TEMPORARY** | Vytvoří soubor jako dočasný; soubor je odstraněn při zavření posledního popisovače souboru. Argument *pmode* je vyžadován, pokud je zadán **_O_CREAT.** |
| **_O_CREAT** &#124;`_O_EXCL` | Vrátí chybovou hodnotu, pokud existuje soubor určený *názvem souboru.* Platí pouze při použití s **_O_CREAT**. |
| **_O_NOINHERIT** | Zabrání vytvoření sdíleného popisovače souboru. |
| **_O_RANDOM** | Určuje, že ukládání do mezipaměti je optimalizováno pro náhodný přístup z disku, ale není omezeno na něj. |
| **_O_RDONLY** | Otevře soubor pouze pro čtení. Nelze zadat pomocí **_O_RDWR** nebo **_O_WRONLY**. |
| **_O_RDWR** | Otevře soubor pro čtení i zápis. Nelze zadat pomocí **_O_RDONLY** nebo **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Určuje, že ukládání do mezipaměti je optimalizováno pro sekvenční přístup z disku, ale není omezen na něj. |
| **_O_TEXT** | Otevře soubor v textovém (přeloženém) režimu. (Další informace naleznete v [tématu Text a binární režim V/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) souboru a [fopen](fopen-wfopen.md).) |
| **_O_TRUNC** | Otevře soubor a zkrátí ho na nulovou délku; soubor musí mít oprávnění k zápisu. Nelze zadat pomocí **_O_RDONLY**. **_O_TRUNC** použit s **_O_CREAT** otevře existující soubor nebo vytvoří soubor. **Poznámka:** Příznak **_O_TRUNC** zničí obsah zadaného souboru. |
| **_O_WRONLY** | Otevře soubor pouze pro psaní. Nelze zadat pomocí **_O_RDONLY** nebo **_O_RDWR**. |
| **_O_U16TEXT** | Otevře soubor v režimu Unicode UTF-16. |
| **_O_U8TEXT** | Otevře soubor v režimu Unicode UTF-8. |
| **_O_WTEXT** | Otevře soubor v režimu Unicode. |

Chcete-li určit režim přístupu k souborům, je nutné zadat **buď _O_RDONLY**, **_O_RDWR**nebo **_O_WRONLY**. Pro režim přístupu neexistuje žádná výchozí hodnota.

Při otevření souboru v režimu Unicode pomocí **_O_WTEXT**, **_O_U8TEXT**nebo **_O_U16TEXT**překládají vstupní funkce data, která jsou ze souboru přečtena, do dat UTF-16 uložených jako typ **wchar_t**. Funkce, které zapisují do souboru otevřeného v režimu Unicode, očekávají vyrovnávací paměti, které obsahují data UTF-16 uložená jako typ **wchar_t**. Pokud je soubor kódován jako UTF-8, pak UTF-16 data je přeložen do UTF-8, když je zapsán, a soubor uTF-8 kódovaný obsah je přeložen do UTF-16 při čtení. Pokus o čtení nebo zápis lichého počtu bajtů v režimu Unicode způsobí chybu ověření parametru. Chcete-li číst nebo zapisovat data uložená v programu jako UTF-8, použijte místo režimu Unicode textový nebo binární režim souborů. Nesete odpovědnost za veškerý požadovaný překlad kódování.

Pokud **je _sopen** volána s **_O_WRONLY** | **_O_APPEND** (režim připojení) a **_O_WTEXT**, **_O_U16TEXT**nebo **_O_U8TEXT**, nejprve se pokusí otevřít soubor pro čtení a zápis, přečíst si kusovník a znovu jej znovu otevřít pouze pro zápis. Pokud otevření souboru pro čtení a zápis selže, otevře soubor pouze pro zápis a použije výchozí hodnotu pro nastavení režimu Unicode.

Argument *shflag* je konstantní výraz skládající se z jedné z následujících \<konstant manifestu, které jsou definovány v share.h>.

|*konstanta shflag*|Chování|
|-|-|
| **_SH_DENYRW** | Odepře přístup k souboru pro čtení a zápis. |
| **_SH_DENYWR** | Odepře přístup k souboru pro zápis. |
| **_SH_DENYRD** | Odepře přístup pro čtení k souboru. |
| **_SH_DENYNO** | Umožňuje přístup ke čtení a zápisu. |

Argument *pmode* je vyžadován pouze v **případě, že** je zadán _O_CREAT. Pokud soubor neexistuje, *pmode* určuje nastavení oprávnění souboru, které jsou nastaveny při prvním zavření nového souboru. V opačném případě je *režim pmode* ignorován. *pmode* je celé číslo výraz, který obsahuje jednu nebo obě konstanty \<manifestu **_S_IWRITE** a **_S_IREAD**, které jsou definovány v sys\stat.h>. Pokud jsou uvedeny obě konstanty, jsou kombinovány s bitové operátor OR. Význam *pmode* je následující.

|*pmode*|Význam|
|-|-|
| **_S_IREAD** | Čtení je povoleno pouze. |
| **_S_IWRITE** | Psaní povoleno. (Ve skutečnosti umožňuje čtení a zápis.) |
| **_S_IREAD** **&#124; _S_IWRITE** | Čtení a psaní povoleno. |

Pokud není uděleno oprávnění k zápisu, soubor je jen pro čtení. V operačním systému Windows jsou všechny soubory čitelné; není možné udělit oprávnění pouze pro zápis. Proto jsou ekvivalentní režimy **_S_IWRITE** a **_S_IREAD** | **_S_IWRITE.**

**_sopen** použije aktuální masku oprávnění k souboru *pmode* před nastavením oprávnění. (Viz [_umask](umask.md).)

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_sopen**|\<io.h>|\<fcntl.h>, \<sys\types.h \<>, sys\stat.h>, \<share.h>|
|**_wsopen**|\<io.h> \<nebo wchar.h>|\<fcntl.h>, \<sys\types.h \<>, sys\stat.h>, \<share.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [_locking](locking.md).

## <a name="see-also"></a>Viz také

[Vstupně-nosné(v" nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
