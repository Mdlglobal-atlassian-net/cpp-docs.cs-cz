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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a6e5f0dcd0bbea436ecdad7abb1fd6fc948f80dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350720"
---
# <a name="_aligned_free"></a>_aligned_free

Uvolní blok paměti, který byl přidělen s [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Syntaxe

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblok*<br/>
Ukazatel na blok paměti, který `_aligned_malloc` byl `_aligned_offset_malloc` vrácen do funkce nebo.

## <a name="remarks"></a>Poznámky

**_aligned_free** je `__declspec(noalias)`označen , což znamená, že je zaručeno, že funkce nebude měnit globální proměnné. Další informace naleznete v tématu [noalias](../../cpp/noalias.md).

Tato funkce neověřuje jeho parametr, na rozdíl od jiných _aligned funkce CRT. Pokud *memblock* je ukazatel NULL, tato funkce jednoduše neprovede žádné akce. Nezmění se `errno` a nevyvolá neplatnou obslužnou rutinu parametru. Pokud dojde k chybě ve funkci z důvodu nepoužití _aligned funkce dříve přidělit blok paměti nebo nesouosost paměti dochází z důvodu některé nepředvídané kalamity, funkce generuje ladicí sestavu z [_RPT, _RPTF, _RPTW, _RPTFW makra](rpt-rptf-rptw-rptfw-macros.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h>|

## <a name="example"></a>Příklad

Další informace naleznete [v tématu _aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Viz také

[Zarovnání dat](../../c-runtime-library/data-alignment.md)
