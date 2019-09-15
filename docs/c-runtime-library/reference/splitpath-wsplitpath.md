---
title: _splitpath, _wsplitpath
ms.date: 11/04/2016
api_name:
- _wsplitpath
- _splitpath
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
ms.openlocfilehash: a502977faf91d744868c4aef79b3a40ca240a90f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958043"
---
# <a name="_splitpath-_wsplitpath"></a>_splitpath, _wsplitpath

Rozdělte název cesty k součástem. Bezpečnější verze těchto funkcí jsou k dispozici, viz [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

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
Úplná cesta

*drive*<br/>
Písmeno jednotky následovaný dvojtečkou ( **:** ). Pokud nepotřebujete písmeno jednotky, můžete pro tento parametr předat **hodnotu null** .

*dir*<br/>
Cesta k adresáři, včetně koncového lomítka. Lze použít lomítka **/** (), zpětná lomítka ( **\\** ) nebo obojí. Pokud nepotřebujete cestu k adresáři, můžete pro tento parametr předat **hodnotu null** .

*fname*<br/>
Základní název souboru (bez přípony) Pokud název souboru nepotřebujete, můžete pro tento parametr předat **hodnotu null** .

*ext*<br/>
Přípona názvu souboru včetně úvodní tečky ( **.** ) Pokud nepotřebujete příponu filename, můžete pro tento parametr předat **hodnotu null** .

## <a name="remarks"></a>Poznámky

Funkce **_splitpath** přerušuje cestu na čtyři součásti. **_splitpath** automaticky zpracovává argumenty vícebajtového řetězce znaků podle potřeby a rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která se právě používá. **_wsplitpath** je **_splitpath**verze s velkým znakem; argumenty **_wsplitpath** jsou řetězce s libovolným znakem. Tyto funkce se chovají identicky jinak.

**Poznámka k zabezpečení** Tyto funkce se dotýkají potenciální hrozby týkající se problému s přetečením vyrovnávací paměti. Problémy s přetečením vyrovnávací paměti představují častější způsob útoku na systém, což vede k neoprávněnému zvýšení oprávnění. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns). K dispozici jsou bezpečnější verze těchto funkcí; viz [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Každá součást úplné cesty je uložena v samostatné vyrovnávací paměti; v manifestu jsou konstanty **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**a **_MAX_EXT** (definované v Stdlib. H) zadejte maximální velikost pro každou součást souboru. Součásti souboru, které jsou větší než odpovídající konstanty manifestu, způsobují poškození haldy.

Každá vyrovnávací paměť musí být stejně velká jako odpovídající konstanta manifestu, aby se předešlo možnému přetečení vyrovnávací paměti.

V následující tabulce jsou uvedeny hodnoty konstant manifestu.

|Name|Value|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Pokud úplná cesta neobsahuje komponentu (například filename), **_splitpath** přiřadí prázdné řetězce do odpovídajících vyrovnávacích pamětí.

Pro libovolný parametr kromě *cesty* , kterou nepotřebujete, můžete předat **hodnotu null** pro **_splitpath** .

Pokud má cesta **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<Stdlib. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_makepath](makepath-wmakepath.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
