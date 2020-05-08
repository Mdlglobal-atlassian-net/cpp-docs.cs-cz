---
title: _aligned_free
ms.date: 4/2/2020
api_name:
- _aligned_free
- _o__aligned_free
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d296600da4db2b97479de95cfc1f8c41d0e50708
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915955"
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
Ukazatel na blok paměti, který byl vrácen do funkce `_aligned_malloc` or. `_aligned_offset_malloc`

## <a name="remarks"></a>Poznámky

**_aligned_free** je označena `__declspec(noalias)`, což znamená, že funkce je zaručena, že nemění globální proměnné. Další informace najdete v tématu [jiné](../../cpp/noalias.md).

Tato funkce neověřuje svůj parametr, na rozdíl od ostatních _aligned funkce CRT. Pokud je *memblock* ukazatel s hodnotou null, tato funkce jednoduše neprovede žádné akce. Nemění `errno` se a nevyvolává obslužnou rutinu neplatného parametru. Pokud ve funkci dojde k chybě z důvodu nepoužití funkce _aligned dříve k přidělení bloku paměti nebo chybného zarovnání paměti z důvodu některých neočekávaných Calamity, funkce vygeneruje sestavu ladění z [_RPT, _RPTF, _RPTW _RPTFW maker](rpt-rptf-rptw-rptfw-macros.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_free**|\<. h>|

## <a name="example"></a>Příklad

Další informace najdete v tématu [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Viz také

[Zarovnání dat](../../c-runtime-library/data-alignment.md)
