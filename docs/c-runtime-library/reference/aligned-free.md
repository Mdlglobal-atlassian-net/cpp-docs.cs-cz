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
ms.openlocfilehash: 0fa28be550050a7eec2a515cfb47d98fb26591d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170966"
---
# <a name="_aligned_free"></a>_aligned_free

Uvolňuje blok paměti, který byl přidělen [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Syntaxe

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatel na blok paměti, který byl vrácen do funkce `_aligned_malloc` nebo `_aligned_offset_malloc`.

## <a name="remarks"></a>Poznámky

**_aligned_free** je označena `__declspec(noalias)`, což znamená, že funkce je zaručena, že nemění globální proměnné. Další informace najdete v tématu [jiné](../../cpp/noalias.md).

Tato funkce neověřuje svůj parametr, na rozdíl od ostatních _aligned funkce CRT. Pokud je *memblock* ukazatel s hodnotou null, tato funkce jednoduše neprovede žádné akce. Nemění `errno` a nevyvolává obslužnou rutinu neplatného parametru. Pokud ve funkci dojde k chybě z důvodu nepoužití funkce _aligned dříve k přidělení bloku paměti nebo chybného zarovnání paměti z důvodu některých neočekávaných Calamity, funkce vygeneruje sestavu ladění z [_RPT, _RPTF, _RPTW _RPTFW maker](rpt-rptf-rptw-rptfw-macros.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_free**|\<. h >|

## <a name="example"></a>Příklad

Další informace najdete v tématu [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Viz také

[Zarovnání dat](../../c-runtime-library/data-alignment.md)
