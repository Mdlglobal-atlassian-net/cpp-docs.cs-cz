---
title: _splitpath, _wsplitpath
ms.date: 4/2/2020
api_name:
- _wsplitpath
- _splitpath
- _o__splitpath
- _o__wsplitpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
ms.openlocfilehash: 6798f93b2d1bc18a190b3b015bf8c882a3fa8a37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355615"
---
# <a name="_splitpath-_wsplitpath"></a>_splitpath, _wsplitpath

Rozdělte název cesty na součásti. K dispozici jsou bezpečnější verze těchto funkcí, viz [_splitpath_s _wsplitpath_s](splitpath-s-wsplitpath-s.md).

## <a name="syntax"></a>Syntaxe

```C
void _splitpath(
   const char *path,
   char *drive,
   char *dir,
   char *fname,
   char *ext
);
void _wsplitpath(
   const wchar_t *path,
   wchar_t *drive,
   wchar_t *dir,
   wchar_t *fname,
   wchar_t *ext
);
```

### <a name="parameters"></a>Parametry

*Cestu*<br/>
Úplná cesta.

*Jednotky*<br/>
Písmeno jednotky následované dvojtečkou (**:**). Pokud nepotřebujete písmeno jednotky, můžete pro tento parametr předat **hodnotu NULL.**

*Dir*<br/>
Cesta adresáře, včetně koncového lomítka. Lze použít **/** lomítka **\\** ( ), zpětná lomítka ( ) nebo obojí. Pokud nepotřebujete cestu k adresáři, můžete pro tento parametr předat **hodnotu NULL.**

*Fname*<br/>
Základní název souboru (bez přípony). Pokud název souboru nepotřebujete, můžete pro tento parametr předat hodnotu **NULL.**

*Ext*<br/>
Přípona názvu souboru, včetně úvodního období (**.**). Pokud příponu název souboru nepotřebujete, můžete pro tento parametr předat **hodnotu NULL.**

## <a name="remarks"></a>Poznámky

Funkce **_splitpath** rozdělí cestu na čtyři součásti. **_splitpath** podle potřeby automaticky zpracovává argumenty vícebajtových řetězců a rozpozná se sekvence vícebajtových znaků podle aktuálně používáné vícebajtové znakové stránky. **_wsplitpath** je širokoznaková verze **_splitpath**; argumenty, které **mají _wsplitpath,** jsou řetězce s širokými znaky. Tyto funkce se chovají stejně jinak.

**Poznámka k zabezpečení** Tyto funkce vznikají potenciální hrozbu způsobené problém přetečení vyrovnávací paměti. Problémy s přetečením vyrovnávací paměti jsou častou metodou systémového útoku, což vede k neoprávněnému zvýšení oprávnění. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns). K dispozici jsou bezpečnější verze těchto funkcí. viz [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Každá součást úplné cesty je uložena v samostatné vyrovnávací paměti; konstanty manifestu **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**a **_MAX_EXT** (definované v STDLIB. H) určete maximální velikost pro každou komponentu souboru. Součásti souboru, které jsou větší než odpovídající konstanty manifestu způsobit poškození haldy.

Každá vyrovnávací paměť musí být stejně velká jako odpovídající konstanta manifestu, aby se zabránilo potenciálnímu přetečení vyrovnávací paměti.

V následující tabulce jsou uvedeny hodnoty konstant manifestu.

|Name (Název)|Hodnota|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Pokud úplná cesta neobsahuje komponentu (například název souboru), **_splitpath** přiřadí odpovídající matoušky prázdných řetězců.

Hodnotu **NULL** můžete předat **_splitpath** pro libovolný parametr než *cestu,* kterou nepotřebujete.

Pokud je *cesta* **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [_makepath](makepath-wmakepath.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
