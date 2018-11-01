---
title: Coleipframewnd – třída
ms.date: 11/04/2016
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
ms.openlocfilehash: 78b846a6b17fb18f533139e9ac6444babd4baac5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498827"
---
# <a name="coleipframewnd-class"></a>Coleipframewnd – třída

Základ pro úpravy okna aplikace na místě.

## <a name="syntax"></a>Syntaxe

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Vytvoří `COleIPFrameWnd` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Volá se rozhraním, když se položka aktivuje pro místní úpravy.|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Volá se rozhraním, aby přemístění okna pro úpravy na místě.|

## <a name="remarks"></a>Poznámky

Tato třída se vytvoří a pozice řídit pruhy v rámci okna dokumentu aplikace typu kontejner. Také obstará oznámení vygenerovaná vložený [coleresizebar –](../../mfc/reference/coleresizebar-class.md) objektu, když uživatel změní velikost okna pro úpravy na místě.

Další informace o používání `COleIPFrameWnd`, najdete v článku [aktivace](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd

Vytvoří `COleIPFrameWnd` objektu a inicializuje informací o stavu v místě, která je uložena v strukturu typu OLEINPLACEFRAMEINFO.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [OLEINPLACEFRAMEINFO](/windows/desktop/api/oleidl/ns-oleidl-tagoifi) v sadě Windows SDK.

##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars

Rámec volá `OnCreateControlBars` fungovat v případě, že položka aktivuje pro místní úpravy.

```
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,
    CWnd* pWndDoc);

virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,
    CFrameWnd* pWndDoc);
```

### <a name="parameters"></a>Parametry

*pWndFrame*<br/>
Ukazatel na okno rámce aplikace kontejneru.

*pWndDoc*<br/>
Ukazatel na úrovni dokumentu okno kontejneru. Může mít hodnotu NULL, pokud je aplikace SDI kontejner.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu; nenulovou hodnotu. jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace nemá žádný účinek. Potlačí tuto funkci provést žádné speciální zpracování požadováno, když se vytvoří ovládací panely.

##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame

Rámec volá `RepositionFrame` členskou funkci Rozvrhněte ovládací pruhy a přemístění okna pro úpravy na místě, takže všechno je viditelný.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel `RECT` struktury nebo `CRect` objekt, který obsahuje místního rámec okna aktuální souřadnice polohy, v pixelech vzhledem ke klientské oblasti.

*lpClipRect*<br/>
Ukazatel `RECT` struktury nebo `CRect` objekt, který obsahuje místního rámec okna aktuální obdélník oříznutí souřadnice, v pixelech vzhledem ke klientské oblasti.

### <a name="remarks"></a>Poznámky

Ovládací pruhy v okně kontejneru rozložení se liší od, které provádí pomocí okna rámce jiných než OLE. Okno rámce jiných než OLE vypočítá pozice ovládacích pruhů a dalších objektů z daného oken s rámečkem velikost, jako volání [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). Klientské oblasti je, co je ještě po odečtena místo ovládacích pruhů a dalších objektů. A `COleIPFrameWnd` okně na druhé straně umístí panelů nástrojů v souladu s danou klientské oblasti. Jinými slovy `CFrameWnd::RecalcLayout` funguje "z vnějšku in", zatímco `COleIPFrameWnd::RepositionFrame` funguje "než vnitřní mimo."

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)
