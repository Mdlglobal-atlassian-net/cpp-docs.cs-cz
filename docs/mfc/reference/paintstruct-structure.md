---
title: PAINTSTRUCT – struktura
ms.date: 11/04/2016
f1_keywords:
- PAINTSTRUCT
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
ms.openlocfilehash: f1b901ef26c61adbedb3bbe56808cd94bdfad30d
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694644"
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT – struktura

`PAINTSTRUCT` Struktura obsahuje informace, které slouží k vykreslení klientské oblasti okna.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagPAINTSTRUCT {
    HDC hdc;
    BOOL fErase;
    RECT rcPaint;
    BOOL fRestore;
    BOOL fIncUpdate;
    BYTE rgbReserved[16];
} PAINTSTRUCT;
```

#### <a name="parameters"></a>Parametry

*hDC*<br/>
Určuje kontext zobrazení má být použit pro kreslení.

*fErase*<br/>
Určuje, jestli potřebuje překreslit na pozadí. Není 0, pokud aplikace byste ho překreslit na pozadí. Aplikace je zodpovědné za vykreslování na pozadí, pokud se vytvoří okno Windows-třídy bez štětec pozadí (viz popis `hbrBackground` člen [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) struktura v sadě Windows SDK).

*rcPaint*<br/>
Určuje horní vlevo a pravém dolním rohu obdélníku, ve které je požadováno pro malování.

*fRestore*<br/>
Vyhrazeným členem. Používá se interně ve Windows.

*fIncUpdate*<br/>
Vyhrazeným členem. Používá se interně ve Windows.

*rgbReserved [16]*<br/>
Vyhrazeným členem. Vyhrazeným blokem paměť používaná interně ve Windows.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winuser

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

