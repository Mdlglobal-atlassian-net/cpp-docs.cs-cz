---
title: _aligned_free
ms.date: 11/04/2016
api_name:
- _aligned_free
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- aligned_free
- _aligned_free
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
ms.openlocfilehash: 44556d3f044a567f4903ef14a4b2a9b353af02ff
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943974"
---
# <a name="_aligned_free"></a>_aligned_free

Uvolňuje blok paměti, který byl přidělen pomocí [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Syntaxe

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatel na blok paměti, který byl vrácen do `_aligned_malloc` funkce or. `_aligned_offset_malloc`

## <a name="remarks"></a>Poznámky

**_aligned_free** je označena `__declspec(noalias)`, což znamená, že funkce je zaručena, že nemění globální proměnné. Další informace najdete v tématu [jiné](../../cpp/noalias.md).

Tato funkce neověřuje svůj parametr, na rozdíl od ostatních _alignedch funkcí CRT. Pokud je *memblock* ukazatel s hodnotou null, tato funkce jednoduše neprovede žádné akce. Nemění `errno` se a nevyvolává obslužnou rutinu neplatného parametru. Pokud dojde k chybě ve funkci kvůli pomocí dříve _aligned funkce přidělení bloku paměti nebo chybné zarovnání paměti dochází kvůli některé nepředvídaných calamity, funkce vygeneruje sestavu ladění z [_RPT, _RPTF, _RPTW, _Rptfw makra](rpt-rptf-rptw-rptfw-macros.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_free**|\<. h >|

## <a name="example"></a>Příklad

Další informace najdete v tématu [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Viz také:

[Zarovnání dat](../../c-runtime-library/data-alignment.md)