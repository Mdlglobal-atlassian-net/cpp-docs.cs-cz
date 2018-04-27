---
title: _splitpath –, _wsplitpath – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29102810363e6501d622ac065b63d0bfe978911a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="splitpath-wsplitpath"></a>_splitpath, _wsplitpath

Název cesty rozdělte součásti. Bezpečnější verze tyto funkce jsou k dispozici, najdete v části [_splitpath_s –, _wsplitpath_s –](splitpath-s-wsplitpath-s.md).

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

*cesta* úplnou cestu.

*jednotka* písmenem jednotky následovaným dvojtečkou (**:**). Abyste mohli předávat **NULL** pro tento parametr, pokud není nutné písmeno jednotky.

*dir* cesta k adresáři, včetně koncové lomítko. Předávání lomítka ( **/** ), zpětná lomítka ( **\\** ), nebo mohou být použity obě. Abyste mohli předávat **NULL** pro tento parametr, pokud není nutné cesta k adresáři.

*%{fname/* základní název souboru (bez přípony). Abyste mohli předávat **NULL** pro tento parametr, pokud není nutné název souboru.

*ext* příponu názvu souboru, včetně úvodní období (**.**). Abyste mohli předávat **NULL** pro tento parametr, pokud není nutné příponu názvu souboru.

## <a name="remarks"></a>Poznámky

**_Splitpath –** funkce dělí do jeho součástí čtyři cestu. **_splitpath –** automaticky zpracovává argumenty řetězce vícebajtových znaků podle potřeby, rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky aktuálně používán. **_wsplitpath –** je verze široká charakterová **_splitpath –**; argumenty, které mají **_wsplitpath –** jsou široká charakterová řetězce. Tyto funkce chovají stejně jako jinak.

**Poznámka k zabezpečení** tyto funkce zpoplatněná potenciální hrozbu způsobené problém přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti problémy jsou často metodu systému útoku, výsledkem bude vyplacena neoprávněně zvýšení úrovně oprávnění. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795). Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_splitpath_s –, _wsplitpath_s –](splitpath-s-wsplitpath-s.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath –**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Jednotlivé komponenty úplná cesta je uložena v samostatné vyrovnávací paměti; manifestu konstanty **_max_drive –**, **_max_dir –**, **_max_fname –**, a **_max_ext –** (definovanou v STDLIB. H) zadejte maximální velikost pro každou součást souboru. Soubor součásti, které jsou větší než odpovídající manifestu konstanty způsobit poškození haldy.

Každé vyrovnávací paměti musí mít stejnou velikost jako jeho odpovídající manifestu konstanta, aby se zabránilo potenciální přetečení vyrovnávací paměti.

V následující tabulce jsou uvedeny hodnoty manifestu konstanty.

|Název|Hodnota|
|----------|-----------|
|**_MAX_DRIVE –**|3|
|**_MAX_DIR –**|256|
|**_MAX_FNAME –**|256|
|**_MAX_EXT –**|256|

Pokud úplná cesta neobsahuje součásti (například název souboru), **_splitpath –** přiřadí prázdné řetězce odpovídající vyrovnávací paměti.

Můžete předat **NULL** k **_splitpath –** pro libovolný parametr jinak než *cesta* , není nutné.

Pokud *cesta* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a funkce vrátí hodnotu **einval –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_makepath –](makepath-wmakepath.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
