---
title: errno, _doserrno, _sys_errlist, and _sys_nerr
ms.date: 11/04/2016
apiname:
- _errno
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _sys_errlist
- errno
- _sys_nerr
- _doserrno
helpviewer_keywords:
- error codes, printing
- sys_errlist global variable
- doserrno global variable
- errno global variable
- _doserrno global variable
- _sys_errlist global variable
- _sys_nerr global variable
- sys_nerr global variable
ms.assetid: adbec641-6d91-4e19-8398-9a34046bd369
ms.openlocfilehash: 57d04fe5867c6a969b6aeca40f26b18b5dcd7a61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344041"
---
# <a name="errno-doserrno-syserrlist-and-sysnerr"></a>errno, _doserrno, _sys_errlist, and _sys_nerr

Globální makra, které obsahují kódy chyb, které jsou nastavené během provádění programu a řetězec ekvivalenty kódy chyb pro zobrazení.

## <a name="syntax"></a>Syntaxe

```
#define errno   (*_errno())
#define _doserrno   (*__doserrno())
#define _sys_errlist (__sys_errlist())
#define _sys_nerr (*__sys_nerr())
```

## <a name="remarks"></a>Poznámky

Obě `errno` a `_doserrno` jsou modulem runtime při spuštění programu nastaveny na hodnotu 0. `errno` je nastaven na chybu při volání funkce úrovni systému. Protože `errno` obsahuje hodnotu pro poslední volání, které je tato hodnota může být změněna následným voláním. Knihovny runtime volá tuto sadu `errno` v případě chyby nerušte zaškrtnutí políčka `errno` v případě úspěchu. Vždy vymažte `errno` voláním `_set_errno(0)` bezprostředně před volání, které může nastavit a zkontrolovat ihned po volání.

V případě chyby `errno` není nutně nastavena na stejnou hodnotu jako chybový kód vrácený voláním systému. Vstupně-výstupních operací `_doserrno` ukládá kód chyby operačního systému: ekvivalenty `errno` kódy. Pro většinu operací bez vstupně-, hodnota `_doserrno` není nastaven.

Každý `errno` hodnota je přidružena chybovou zprávu ve `_sys_errlist` , který lze vytisknout pomocí jedné z [perror](../c-runtime-library/reference/perror-wperror.md) funkce nebo uložený v řetězci pomocí jedné z [strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) nebo [strerror_s –](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) funkce. `perror` a `strerror` funkce použijte `_sys_errlist` pole a `_sys_nerr`– počet prvků v `_sys_errlist`– ke zpracování informací o chybách. Přímý přístup k `_sys_errlist` a `_sys_nerr` z důvodů zabezpečení kódu je zastaralý. Doporučujeme používat bezpečnější funkční verze místo globální makra, jak je znázorněno zde:

|Globální – makro|Funkční ekvivalenty|
|------------------|----------------------------|
|`_doserrno`|[_get_doserrno](../c-runtime-library/reference/get-doserrno.md), [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)|
|`errno`|[_get_errno](../c-runtime-library/reference/get-errno.md), [_set_errno](../c-runtime-library/reference/set-errno.md)|
|`_sys_errlist`, `_sys_nerr`|[strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|

Knihovna matematických rutin nastavuje `errno` voláním [_matherr](../c-runtime-library/reference/matherr.md). Chcete-li matematické chyby ošetřit jinak, napište vlastní rutinu podle `_matherr` a pojmenujte ho `_matherr`.

Všechny `errno` hodnoty v následující tabulce jsou předdefinované konstanty v \<errno.h >, a jsou kompatibilní se systémem UNIX. Pouze `ERANGE`, `EILSEQ`, a `EDOM` zadávají se ve standardu ISO C99.

|Konstanta|Zpráva o systémové chybě|Value|
|--------------|--------------------------|-----------|
|`EPERM`|Operace není povolena.|1|
|`ENOENT`|Žádný odpovídající soubor nebo adresář|2|
|`ESRCH`|Žádný odpovídající proces|3|
|`EINTR`|Funkce byla přerušena.|4|
|`EIO`|Vstupně-výstupní chyba|5|
|`ENXIO`|Žádné odpovídající zařízení ani adresa|6|
|`E2BIG`|Seznam argumentů je příliš dlouhý.|7|
|`ENOEXEC`|Chyba formátu exec|8|
|`EBADF`|Chybné číslo souboru|9|
|`ECHILD`|Žádné vytvářené procesy|10|
|`EAGAIN`|Žádné další procesy nebo není dostatek paměti nebo bylo dosaženo maximální úrovně vnoření.|11|
|`ENOMEM`|Není dostatek paměti|12|
|`EACCES`|Oprávnění byla odepřena.|13|
|`EFAULT`|Chybná adresa|14|
|`EBUSY`|Zařízení nebo prostředek je zaneprázdněn.|16|
|`EEXIST`|Soubor existuje.|17|
|`EXDEV`|Odkaz mezi zařízeními|18|
|`ENODEV`|Žádné odpovídající zařízení|19|
|`ENOTDIR`|Nejedná se o adresář.|20|
|`EISDIR`|Jedná se o adresář.|21|
|`EINVAL`|Argument je neplatný.|22|
|`ENFILE`|V systému je otevřeno příliš mnoho souborů.|23|
|`EMFILE`|Bylo otevřeno příliš mnoho souborů.|24|
|`ENOTTY`|Nesprávná operace vstupně-výstupní kontroly|25|
|`EFBIG`|Soubor je příliš velký.|27|
|`ENOSPC`|V zařízení není dostatek místa.|28|
|`ESPIPE`|Neplatné hledání|29|
|`EROFS`|Systém souborů je určen jen pro čtení.|30|
|`EMLINK`|Příliš mnoho odkazů|31|
|`EPIPE`|Kanál je přerušen.|32|
|`EDOM`|Matematický argument|33|
|`ERANGE`|Výsledek je příliš velký.|34|
|`EDEADLK`|Došlo by k vzájemnému zablokování prostředků.|36|
|`EDEADLOCK`|Stejné jako funkce EDEADLK pro kompatibilitu se staršími verzemi Microsoft C|36|
|`ENAMETOOLONG`|Název souboru je příliš dlouhý.|38|
|`ENOLCK`|K dispozici nejsou žádné zámky.|39|
|`ENOSYS`|Tato funkce není podporována.|40|
|`ENOTEMPTY`|Adresář není prázdný.|41|
|`EILSEQ`|Neplatná sekvence bajtů|42|
|`STRUNCATE`|Řetězec byl zkrácen.|80|

## <a name="requirements"></a>Požadavky

|Globální – makro|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|------------------|---------------------|---------------------|
|`errno`|\<errno.h > nebo \<stdlib.h >, \<cerrno – > nebo \<cstdlib – > (C++)||
|`_doserrno`, `_sys_errlist`, `_sys_nerr`|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

`_doserrno`, `_sys_errlist`, A `_sys_nerr` makra jsou rozšíření společnosti Microsoft. Další informace o kompatibilitě naleznete v tématu [kompatibility](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Globální proměnné](../c-runtime-library/global-variables.md)<br/>
[errno – konstanty](../c-runtime-library/errno-constants.md)<br/>
[perror, _wperror](../c-runtime-library/reference/perror-wperror.md)<br/>
[strerror, _strerror, _wcserror, \__wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)<br/>
[strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)<br/>
[_get_doserrno](../c-runtime-library/reference/get-doserrno.md)<br/>
[_set_doserrno](../c-runtime-library/reference/set-doserrno.md)<br/>
[_get_errno](../c-runtime-library/reference/get-errno.md)<br/>
[_set_errno](../c-runtime-library/reference/set-errno.md)
