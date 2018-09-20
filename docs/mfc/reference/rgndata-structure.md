---
title: Rgndata – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- RGNDATA
dev_langs:
- C++
helpviewer_keywords:
- RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d40cd86cff4c3e58e88f9d17a551dc789bd1db4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398207"
---
# <a name="rgndata-structure"></a>RGNDATA – struktura

`RGNDATA` Struktura obsahuje hlavičku a pole obdélníky, které tvoří oblast. Tyto obdélníky, seřazený shora dolů zleva doprava, nemusí být stejné.

## <a name="syntax"></a>Syntaxe

```
typedef struct _RGNDATA { /* rgnd */
    RGNDATAHEADER rdh;
    char Buffer[1];
} RGNDATA;
```

#### <a name="parameters"></a>Parametry

*rdh*<br/>
Určuje [RGNDATAHEADER](/windows/desktop/api/wingdi/ns-wingdi-_rgndataheader) struktury. (Další informace o této struktuře naleznete v tématu Windows SDK.) Členové této struktury zadat typ oblasti (ať už jde obdélníkové nebo lichoběžníkové), počet obdélníky, které tvoří oblast, velikost vyrovnávací paměti, která obsahuje struktury obdélník a tak dále.

*Vyrovnávací paměti*<br/>
Určuje libovolné velikosti vyrovnávací paměti, která obsahuje [RECT](../../mfc/reference/rect-structure1.md) struktury, které tvoří oblast.

## <a name="requirements"></a>Požadavky

**Záhlaví:** wingdi.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)<br/>
[CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

