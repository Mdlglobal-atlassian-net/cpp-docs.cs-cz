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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 1d24565a912d74060e60024dcfd90b8018cae32d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920284"
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

*dílčí*<br/>
Úplná cesta

*disky*<br/>
Písmeno jednotky následovaný dvojtečkou (**:**). Pokud nepotřebujete písmeno jednotky, můžete pro tento parametr předat **hodnotu null** .

*Dir*<br/>
Cesta k adresáři, včetně koncového lomítka. Lze použít lomítka **/** (), zpětná lomítka ( **\\** ) nebo obojí. Pokud nepotřebujete cestu k adresáři, můžete pro tento parametr předat **hodnotu null** .

*fname*<br/>
Základní název souboru (bez přípony) Pokud název souboru nepotřebujete, můžete pro tento parametr předat **hodnotu null** .

*rozšířeného*<br/>
Přípona názvu souboru včetně úvodní tečky (**.**) Pokud nepotřebujete příponu filename, můžete pro tento parametr předat **hodnotu null** .

## <a name="remarks"></a>Poznámky

Funkce **_splitpath** přerušuje cestu do čtyř součástí. **_splitpath** automaticky zpracovává argumenty vícebajtového řetězce znaků podle potřeby a rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která se právě používá. **_wsplitpath** je verze **_splitpath**s velkým znakem; argumenty **_wsplitpath** jsou řetězce s libovolným znakem. Tyto funkce se chovají identicky jinak.

**Poznámka k zabezpečení** Tyto funkce se dotýkají potenciální hrozby týkající se problému s přetečením vyrovnávací paměti. Problémy s přetečením vyrovnávací paměti představují častější způsob útoku na systém, což vede k neoprávněnému zvýšení oprávnění. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns). K dispozici jsou bezpečnější verze těchto funkcí; viz [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Každá součást úplné cesty je uložena v samostatné vyrovnávací paměti; konstanty manifestu **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**a **_MAX_EXT** (definované v Stdlib. H) zadejte maximální velikost pro každou součást souboru. Součásti souboru, které jsou větší než odpovídající konstanty manifestu, způsobují poškození haldy.

Každá vyrovnávací paměť musí být stejně velká jako odpovídající konstanta manifestu, aby se předešlo možnému přetečení vyrovnávací paměti.

V následující tabulce jsou uvedeny hodnoty konstant manifestu.

|Name|Hodnota|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Pokud úplná cesta neobsahuje komponentu (například filename), **_splitpath** přiřadí prázdné řetězce do odpovídajících vyrovnávacích pamětí.

**Hodnotu null** můžete předat **_splitpath** pro libovolný parametr kromě *cesty* , kterou nepotřebujete.

Pokud *path* má cesta **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_splitpath**|\<Stdlib. h>|
|**_wsplitpath**|\<Stdlib. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad [_makepath](makepath-wmakepath.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
