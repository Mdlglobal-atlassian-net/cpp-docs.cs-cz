---
title: _sopen –, _wsopen – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e8d7f7624dc8c521186aa697ad8825c77e0108f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418094"
---
# <a name="sopen-wsopen"></a>_sopen, _wsopen

Otevře soubor pro sdílení. Bezpečnější verze tyto funkce jsou k dispozici: najdete v části [_sopen_s –, _wsopen_s –](sopen-s-wsopen-s.md).

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
Druh operace povoleny.

*shflag*<br/>
Druh sdílení povoleno.

*pmode*<br/>
Nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí, vrátí se popisovač souboru pro otevřený soubor.

Pokud *filename* nebo *oflag* je **NULL** ukazatele, nebo pokud *oflag* nebo *shflag* není v rámci platná rozsah hodnot je volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte **errno** na jednu z následujících hodnot.

|errno – hodnota|Podmínka|
|-|-|
**EACCES –**|Zadaná cesta je adresář, nebo soubor je jen pro čtení, ale došlo k pokusu o operaci otevřít pro zápis.
**EEXIST –**|**_O_creat –** a **_o_excl –** příznaky byly zadány, ale *filename* již existuje.
**EINVAL –**|Neplatný *oflag* nebo *shflag* argument.
**EMFILE –**|Nejsou k dispozici žádné další popisovače souborů.
**ENOENT –**|Soubor nebo cesta nebyla nalezena.

Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Sopen –** funkce otevře soubor určený touto *filename* a připraví soubor sdílený čtení nebo zápisu, podle definice *oflag* a *shflag* . **_wsopen –** je verze široká charakterová **_sopen –**; *filename* argument **_wsopen –** je široká charakterová řetězec. **_wsopen –** a **_sopen –** chovat jinak shodně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

Celočíselný výraz *oflag* se vytvoří kombinací nejméně jeden z následujících manifestu konstanty, které jsou definovány v \<fcntl.h >. Pokud dva nebo více konstant formuláři argument *oflag*, jsou kombinované pomocí operátoru bitové operace OR ( **&#124;** ).

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

Při otevření souboru v režimu Unicode pomocí **_O_WTEXT**, **_O_U8TEXT**, nebo **_O_U16TEXT**, vstupní funkce převede data, která je pro čtení ze souboru do data ve formátu UTF-16 Uložit jako typ **wchar_t**. Funkce, které zapisovat do souboru otevřeného v režimu Unicode očekávat vyrovnávací paměti, které obsahují data ve formátu UTF-16 uložené jako typ **wchar_t**. Pokud soubor zakódován pomocí kódování UTF-8, je při je zapsán a kódování UTF-8 obsah souboru je přeložit na UTF-16, když je pro čtení dat ve formátu UTF-16 přeložit na UTF-8. Pokus o čtení nebo zápisu lichý počet bajtů v režimu Unicode způsobí, že chyba ověření parametru. Číst nebo zapisovat data, která je uložená v programu jako UTF-8, použijte místo režim Unicode režim textových nebo binárních souborů. Jste zodpovědní za jakékoli požadované kódování překlad.

Pokud **_sopen –** je volán s **_o_wronly –** | **_o_append –** (režim připojení) a **_O_WTEXT**, **_O_ U16TEXT**, nebo **_O_U8TEXT**, nejprve se pokusí otevřít soubor pro čtení a zápis, přečtěte si Kusovníku a pak ho znovu otevřít pro zápis pouze. Pokud otevírání souboru pro čtení a zápis selže, otevře soubor pro zápis pouze a používá výchozí hodnota pro nastavení režimu kódování Unicode.

Argument *shflag* je konstantní výraz, který se skládá z jednoho z následujících manifestu konstant, které jsou definovány v \<share.h >.

|*shflag* konstant|Chování|
|-|-|
**_SH_DENYRW –**|Odmítne oprávnění ke čtení a zápisu do souboru.
**_SH_DENYWR –**|Odepře přístup pro zápis do souboru.
**_SH_DENYRD –**|Odepře přístup pro čtení do souboru.
**_SH_DENYNO –**|Povolí přístup čtení a zápisu.

*Pmode* se vyžaduje jenom v případě **_o_creat –** je zadán. Pokud soubor neexistuje, *pmode* určuje nastavení v souboru oprávnění, která jsou nastavena při prvním zavření nový soubor. V opačném *pmode* je ignorována. *pmode* je použit celočíselný výraz, který obsahuje jedno nebo obě manifestu konstanty **_s_iwrite –** a **_s_iread –**, která jsou definována v \<sys\stat.h >. Pokud jsou zadány oba konstanty, jsou kombinovat s operátoru bitové operace OR. Význam *pmode* je následující.

|*pmode*|Význam|
|-|-|
**_S_IREAD –**|Pouze čtení povolené.
**_S_IWRITE –**|Zápis povolen. (Ve skutečnosti povoluje čtení a zápis.)
**_S_IREAD –** &AMP;#124; **_S_IWRITE –**|Čtení a zápis povolen.

Není-li oprávnění k zápisu, soubor je jen pro čtení. V operačním systému Windows jsou všechny soubory čitelný; není možné udělit oprávnění jen pro zápis. Proto režimů **_s_iwrite –** a **_s_iread –** | **_s_iwrite –** odpovídají.

**_sopen –** použije aktuální maska souboru oprávnění k *pmode* předtím, než jsou oprávnění nastavena. (Viz [_umask –](umask.md).)

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_sopen**|\<IO.h >|\<fcntl.h >, \<sys\types.h >, \<sys\stat.h >, \<share.h >|
|**_wsopen**|\<IO.h > nebo \<wchar.h >|\<fcntl.h >, \<sys\types.h >, \<sys\stat.h >, \<share.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_locking –](locking.md).

## <a name="see-also"></a>Viz také

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
