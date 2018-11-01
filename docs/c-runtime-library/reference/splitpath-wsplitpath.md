---
title: _splitpath, _wsplitpath
ms.date: 11/04/2016
apiname:
- _wsplitpath
- _splitpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: d079bd17912c0711a4e1fbadadf12430520f2c96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465179"
---
# <a name="splitpath-wsplitpath"></a>_splitpath, _wsplitpath

Název cesty rozdělte do komponenty. Bezpečnější verze těchto funkcí jsou k dispozici, najdete v článku [_splitpath_s – _wsplitpath_s –](splitpath-s-wsplitpath-s.md).

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

*Cesta*<br/>
Úplná cesta.

*Jednotky*<br/>
Písmeno, za nímž následuje dvojtečka (**:**). Můžete předat **NULL** pro tento parametr, pokud není nutné písmeno jednotky.

*adresář*<br/>
Cesta k adresáři, včetně koncového lomítka. Lomítka ( **/** ), zpětná lomítka ( **\\** ), nebo obě mohou být použity. Můžete předat **NULL** pro tento parametr, pokud není nutné cesta k adresáři.

*%{fname/*<br/>
Základní název souboru (bez přípony). Můžete předat **NULL** pro tento parametr, pokud není nutné název souboru.

*ext, přípona*<br/>
Příponu názvu souboru, včetně počáteční období (**.**). Můžete předat **NULL** pro tento parametr, pokud není nutné příponu názvu souboru.

## <a name="remarks"></a>Poznámky

**_Splitpath –** funkce rozdělí cestu do jeho čtyři součásti. **_splitpath –** automaticky zpracovává argumenty vícebajtových řetězců znaků podle potřeby, rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která aktuálně používán. **_wsplitpath –** je verze širokého znaku **_splitpath –**; argumenty, které mají **_wsplitpath –** jsou širokoznaké řetězce. Tyto funkce chovají identicky jinak.

**Poznámka k zabezpečení** tyto funkce se vám účtovat potenciální ohrožení způsobené problémem přetečení vyrovnávací paměti. Problémů přetečení vyrovnávací paměti jsou častou metodou útoku na systém. Výsledkem je negarantované zvýšení úrovně oprávnění. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns). Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [_splitpath_s – _wsplitpath_s –](splitpath-s-wsplitpath-s.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath –**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Jednotlivé komponenty úplná cesta je uložena v samostatných vyrovnávací paměti; konstanty manifestu **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**, a **_MAX_EXT** (definované v STDLIB. H) zadejte maximální velikost pro každou komponentu souboru. Soubor součásti, které jsou větší než odpovídající konstant manifestu dojít k poškození haldy.

Každé vyrovnávací paměti musí být větší než jeho odpovídající manifestu konstanta, aby se zabránilo potenciální přetečení vyrovnávací paměti.

V následující tabulce jsou uvedeny hodnoty konstant manifestu.

|Název|Hodnota|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Pokud je úplná cesta neobsahuje součásti (například název_souboru), **_splitpath –** přiřadí prázdné řetězce na odpovídající vyrovnávací paměti.

Můžete předat **NULL** k **_splitpath –** pro libovolný parametr jiných než *cesta* , která není nutné.

Pokud *cesta* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_makepath –](makepath-wmakepath.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
