---
title: _sopen_s, _wsopen_s
ms.date: 11/04/2016
api_name:
- _sopen_s
- _wsopen_s
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
- _sopen_s
- wsopen_s
- _wsopen_s
- sopen_s
helpviewer_keywords:
- sopen_s function
- _wsopen_s function
- wsopen_s function
- opening files, for sharing
- files [C++], opening
- _sopen_s function
- files [C++], sharing
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
ms.openlocfilehash: 86bfef0d8aab81ae990f1e111ec4870cd4b854b8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947900"
---
# <a name="_sopen_s-_wsopen_s"></a>_sopen_s, _wsopen_s

Otevře soubor pro sdílení. Tyto verze [_sopen a _wsopen](sopen-wsopen.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _sopen_s(
   int* pfh,
   const char *filename,
   int oflag,
   int shflag,
   int pmode
);
errno_t _wsopen_s(
   int* pfh,
   const wchar_t *filename,
   int oflag,
   int shflag,
   int pmode,
);
```

### <a name="parameters"></a>Parametry

*pfh*<br/>
Popisovač souboru nebo-1 v případě chyby.

*Bitmap*<br/>
Název souboru.

*oflag*<br/>
Druh povolených operací.

*shflag*<br/>
Typ sdílení je povolený.

*pmode*<br/>
Nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

Nenulová návratová hodnota označuje chybu. v takovém případě je **errno** nastaveno na jednu z následujících hodnot.

|hodnota errno|Podmínka|
|-|-|
| **EACCES** |  Daná cesta je adresář, nebo je soubor jen pro čtení, ale došlo k pokusu o operaci otevření pro zápis. |
| **EEXIST** |  Byly zadány příznaky **_O_CREAT** a **_O_EXCL** , ale *název souboru* již existuje. |
| **EINVAL** |  Neplatný argument *oflag*, *Shflag*nebo *pmode* , nebo *PFH* nebo *filename* byl ukazatel s hodnotou null. |
| **EMFILE** | Nejsou k dispozici žádné další popisovače souboru. |
| **ENOENT** | Soubor nebo cesta nebyla nalezena. |

Je-li funkci předán neplatný argument, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a vrátí **EINVAL** .

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

V případě chyby je hodnota-1 vrácena prostřednictvím *PFH* (Pokud *PFH* není ukazatel s hodnotou null).

## <a name="remarks"></a>Poznámky

Funkce **_sopen_s** otevře soubor určený parametrem *filename* a připraví soubor pro sdílené čtení nebo zápis, jak jsou definovány v *oflag* a *Shflag*. **_wsopen_s** je **_sopen_s**verze s velkým znakem; Argument *filename* pro **_wsopen_s** je řetězec s velkým znakem. **_wsopen_s** a **_sopen_s** se chovají stejně jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

Celočíselný výraz *oflag* je tvořen kombinací jedné nebo více konstant manifestu, které jsou definovány v \<fcntl. h >. V případě, že dvě nebo více konstant tvoří argument *oflag*, jsou kombinovány s bitovým operátorem **&#124;** or ().

|konstanta *oflag*|Chování|
|-|-|
| **_O_APPEND** | Přesune ukazatel souboru na konec souboru před každou operací zápisu. |
| **_O_BINARY** | Otevře soubor v binárním (nepřeloženém) režimu. (Popis binárního režimu najdete v tématu [fopen](fopen-wfopen.md) .) |
| **_O_CREAT** | Vytvoří soubor a otevře jej pro zápis. Nemá žádný vliv, pokud soubor určený parametrem *filename* existuje. Je-li zadán parametr **_O_CREAT** , je požadován argument *pmode* . |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | Vytvoří soubor jako dočasný a pokud je to možné, nebude se vyprázdnit na disk. Je-li zadán parametr **_O_CREAT** , je požadován argument *pmode* . |
| **_O_CREAT** &#124; **_O_TEMPORARY** | Vytvoří soubor jako dočasný; po zavření posledního deskriptoru souboru se soubor odstraní. Je-li zadán parametr **_O_CREAT** , je požadován argument *pmode* . |
| **_O_CREAT** &#124; ` _O_EXCL` | Vrací hodnotu chyby, pokud soubor určený parametrem *filename* existuje. Platí pouze při použití s **_O_CREAT**. |
| **_O_NOINHERIT** | Zabraňuje vytvoření popisovače sdíleného souboru. |
| **_O_RANDOM** | Určuje, že ukládání do mezipaměti je optimalizované pro, ale ne omezené na, náhodný přístup z disku. |
| **_O_RDONLY** | Otevře soubor jen pro čtení. Nelze zadat pomocí **_O_RDWR** nebo **_O_WRONLY**. |
| **_O_RDWR** | Otevře soubor pro čtení i zápis. Nelze zadat pomocí **_O_RDONLY** nebo **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Určuje, že ukládání do mezipaměti je optimalizované pro, ale ne omezené na, sekvenční přístup z disku. |
| **_O_TEXT** | Otevře soubor v textovém (přeloženém) režimu. (Další informace najdete v tématu [vstupně-výstupní operace se soubory v textovém a binárním režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [fopen](fopen-wfopen.md).) |
| **_O_TRUNC** | Otevře soubor a zkrátí ho na nulovou délku. soubor musí mít oprávnění k zápisu. Nelze zadat pomocí **_O_RDONLY**. **_O_TRUNC** použité s **_O_CREAT** otevře existující soubor nebo vytvoří soubor. **Poznámka:** Příznak **_O_TRUNC** zničí obsah zadaného souboru. |
| **_O_WRONLY** | Otevře soubor pouze pro zápis. Nelze zadat pomocí **_O_RDONLY** nebo **_O_RDWR**. |
| **_O_U16TEXT** | Otevře soubor v režimu Unicode UTF-16. |
| **_O_U8TEXT** | Otevře soubor v režimu Unicode UTF-8. |
| **_O_WTEXT** | Otevře soubor v režimu Unicode. |

Chcete-li určit režim přístupu k souboru, je nutné zadat buď **_O_RDONLY**, **_O_RDWR**nebo **_O_WRONLY**. Neexistuje žádná výchozí hodnota pro režim přístupu.

Když se soubor otevře v režimu Unicode pomocí **_O_WTEXT**, **_O_U8TEXT**nebo **_O_U16TEXT**, funkce Input přeloží data načtená ze souboru do dat UTF-16 uložených jako typ **wchar_t**. Funkce, které zapisují do souboru otevřeného v režimu Unicode, očekávají vyrovnávací paměti, které obsahují data UTF-16 uložená jako typ **wchar_t**. Pokud je soubor kódovaný jako UTF-8, data UTF-16 se při zápisu přeloží na UTF-8 a obsah zakódovaný v kódování UTF-8 se převede na UTF-16 při čtení. Při pokusu o čtení nebo zápis lichého počtu bajtů v režimu Unicode dojde k chybě ověření parametru. Chcete-li číst nebo zapisovat data uložená v programu jako UTF-8, místo režimu Unicode použijte textový nebo binární souborový režim. Zodpovídáte za všechny požadované překlady kódování.

Pokud je volání **_sopen_s** s **_O_WRONLY** |  **_O_APPEND** (režim připojení) a **_O_WTEXT**, **_O_U16TEXT**nebo **_O_U8TEXT**, pokusí se nejprve otevřít soubor pro čtení a zápis, přečtěte si kusovník a pak ho znovu otevřít. pouze pro zápis. Pokud soubor otevíráte pro čtení a zápis, otevře se soubor jenom pro zápis a použije se výchozí hodnota pro nastavení režimu Unicode.

Argument *Shflag* je konstantní výraz, který se skládá z jedné z následujících konstant manifestu, které jsou definovány v \<> Share. h.

|konstanta *Shflag*|Chování|
|-|-|
| **_SH_DENYRW** | Zakazuje přístup pro čtení a zápis k souboru. |
| **_SH_DENYWR** | Zakazuje přístup pro zápis do souboru. |
| **_SH_DENYRD** | Odepře přístup pro čtení k souboru. |
| **_SH_DENYNO** | Povolí přístup pro čtení a zápis. |

Argument *pmode* se vždy vyžaduje, na rozdíl od **_sopen**. Když zadáte **_O_CREAT**, v případě, že soubor neexistuje, *pmode* určuje nastavení oprávnění souboru, které se nastaví při prvním zavření nového souboru. V opačném případě se *pmode* ignoruje. *pmode* je celočíselný výraz, který obsahuje jednu nebo obě konstanty manifestu **_S_IWRITE** a **_S_IREAD**, které jsou definovány v \<sys\stat.h >. Pokud jsou zadány obě konstanty, jsou kombinovány s bitovým operátorem OR. Význam *pmode* je následující.

|*pmode*|Význam|
|-|-|
| **_S_IREAD** | Povoluje se pouze čtení. |
| **_S_IWRITE** | Zápis povolen. (V důsledku toho povoluje čtení a zápis.) |
| **_S_IREAD** &#124; **_S_IWRITE** | Čtení a zápis jsou povoleny. |

Pokud není uděleno oprávnění k zápisu, je soubor určen jen pro čtení. V operačním systému Windows jsou všechny soubory čitelné; není možné poskytovat oprávnění pouze pro zápis. Proto jsou režimy **_S_IWRITE** a **_S_IREAD** |  **_S_IWRITE** ekvivalentní.

**_sopen_s** aplikuje aktuální masku oprávnění souboru na *pmode* před nastavením oprávnění. (Viz [_umask](umask.md).)

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<io.h>|\<fcntl. h >, \<sys\types.h >, \<sys\stat.h >, \<Share. h >|
|**_wsopen_s**|\<IO. h > nebo \<WCHAR. h >|\<fcntl. h >, \<sys/Types. h > \<, sys/stat. h > \<; Share. h >|

**_sopen_s** a **_Wsopen_s** jsou rozšíření společnosti Microsoft. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_locking](locking.md).

## <a name="see-also"></a>Viz také:

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
