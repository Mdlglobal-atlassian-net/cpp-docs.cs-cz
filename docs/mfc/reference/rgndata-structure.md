---
title: RGNDATA – struktura
ms.date: 11/04/2016
f1_keywords:
- RGNDATA
helpviewer_keywords:
- RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
ms.openlocfilehash: d6ee25b490aa5c7055b4e8ccf63939fbdd8dd4ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638136"
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

