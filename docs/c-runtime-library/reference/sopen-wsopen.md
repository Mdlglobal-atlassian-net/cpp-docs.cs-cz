---
title: _sopen, _wsopen
ms.date: 11/04/2016
apiname:
- _sopen
- _wsopen
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
ms.openlocfilehash: b3773550fd32df75f0a3819767de1171daebaf0f
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330122"
---
# <a name="sopen-wsopen"></a>_sopen, _wsopen

Otevře soubor pro sdílení. Bezpečnější verze těchto funkcí jsou k dispozici: viz [_sopen_s – _wsopen_s –](sopen-s-wsopen-s.md).

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

*Název souboru*<br/>
Název souboru.

*oflag*<br/>
Druh operace povolena.

*shflag*<br/>
Druh sdílení povolené.

*pmode*<br/>
Nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací popisovač souboru otevřený soubor.

Pokud *filename* nebo *oflag* je **NULL** ukazatele, nebo pokud *oflag* nebo *shflag* není v platné rozsah hodnot, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** na jednu z následujících hodnot.

|Hodnota errno|Podmínka|
|-|-|
| **EACCES** | Zadaná cesta je adresář, nebo tento soubor je jen pro čtení, ale došlo k pokusu o operaci otevřít pro zápis. |
| **EEXIST** | **_O_CREAT** a **_O_EXCL** příznaky byly zadány, ale *filename* již existuje. |
| **EINVAL** | Neplatný *oflag* nebo *shflag* argument. |
| **EMFILE** | Nejsou k dispozici žádné další popisovače souboru. |
| **ENOENT** | Soubor nebo cesta nebyla nalezena. |

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Sopen** otevře soubor určený parametrem funkce *filename* a připraví ho na sdílené čtení nebo zápisu, podle definice *oflag* a *shflag* . **_wsopen –** je verze širokého znaku **_sopen**; *filename* argument **_wsopen –** je širokoznaký řetězec. **_wsopen –** a **_sopen** se jinak chovají stejně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

Celočíselný výraz *oflag* je tvořen přidáním kombinování nejméně jeden z následujících konstant manifestu, které jsou definovány v \<fcntl.h >. Když dva nebo více konstant tvoří argument *oflag*, jsou kombinované pomocí bitového operátoru OR – operátor ( **&#124;** ).

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

Když je soubor otevřen v režimu Unicode s použitím **_O_WTEXT**, **_O_U8TEXT**, nebo **_O_U16TEXT**, zadejte funkce převede data, která je pro čtení ze souboru o datech UTF-16 Uložit jako typ **wchar_t**. Funkce, které se zápis do souboru otevřeném v režimu Unicode očekávat vyrovnávacích pamětí, které obsahují data UTF-16 uložené jako typ **wchar_t**. Pokud soubor zakódován pomocí kódování UTF-8, je při zápisem a kódování UTF-8 obsah souboru je přeložit na UTF-16, když je pro čtení dat UTF-16 přeložit na UTF-8. Pokus o čtení nebo zápisu lichý počet bajtů v režimu Unicode způsobí chybu ověření parametru. Pro čtení nebo zápis dat, která je uložena ve svém programu jako UTF-8, použijte namísto režimu Unicode textová nebo binární režim souboru. Zodpovídáte za všechny požadované kódování překladu.

Pokud **_sopen** volána s **_O_WRONLY** | **_O_APPEND** (režimu připojení) a **_O_WTEXT**, **_O_ U16TEXT**, nebo **_O_U8TEXT**, nejprve se pokusí otevřít soubor pro čtení a zápis, přečtěte si BOM a pak ho znovu otevřít pro zápis. Pokud otevřete soubor pro čtení a zápis selže, otevře soubor pro zápis a používá výchozí hodnota pro nastavení režimu Unicode.

Argument *shflag* je konstantní výraz, který se skládá z jednoho z následujících konstant manifestu, které jsou definovány v \<share.h >.

|*shflag* konstanty|Chování|
|-|-|
| **_SH_DENYRW** | Zakazuje čtení a zápis do souboru. |
| **_SH_DENYWR** | Odepřít přístup pro zápis do souboru. |
| **_SH_DENYRD** | Odepřít přístup pro čtení do souboru. |
| **_SH_DENYNO** | Povolí čtení a zápis. |

*Pmode* se vyžaduje jenom v případě **_O_CREAT** určena. Pokud soubor neexistuje, *pmode* určuje nastavení oprávnění k souboru, které se nastavují při zavření poprvé nový soubor. V opačném případě *pmode* se ignoruje. *pmode* se celočíselný výraz, který obsahuje jeden nebo oba z konstant manifestu **_S_IWRITE** a **_S_IREAD**, které jsou definovány v \<sys\stat.h >. Když jsou uvedeny oba konstanty, jsou kombinované pomocí operátoru bitového operátoru OR. Význam *pmode* vypadá takto.

|*pmode*|Význam|
|-|-|
| **_S_IREAD** | Povoleno jen čtení. |
| **_S_IWRITE** | Zápis povolen. (V podstatě povoluje čtení a zápis.) |
| **_S_IREAD** &AMP;#124; **_S_IWRITE** | Čtení a zápis povolen. |

Pokud tento parametr není zadaný oprávnění k zápisu, soubor je jen pro čtení. V operačním systému Windows jsou čitelné; všechny soubory není možné poskytnout oprávnění jen pro zápis. Proto režimy **_S_IWRITE** a **_S_IREAD** | **_S_IWRITE** jsou ekvivalentní.

**_sopen** použije aktuální masku souboru oprávnění k *pmode* předtím, než jsou oprávnění. (Viz [_umask –](umask.md).)

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_sopen**|\<IO.h >|\<fcntl.h >, \<vložit hlavičky sys\types.h >, \<sys\stat.h >, \<share.h >|
|**_wsopen**|\<IO.h > nebo \<wchar.h >|\<fcntl.h >, \<vložit hlavičky sys\types.h >, \<sys\stat.h >, \<share.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_locking –](locking.md).

## <a name="see-also"></a>Viz také:

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
