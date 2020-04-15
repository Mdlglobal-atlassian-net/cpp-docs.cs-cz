---
title: Třída COleIPFrameWnd
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
ms.openlocfilehash: 01e259cf01c42add26088b0cbd2f6dab311eb9b1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374961"
---
# <a name="coleipframewnd-class"></a>Třída COleIPFrameWnd

Základ pro okno pro úpravy aplikace na místě.

## <a name="syntax"></a>Syntaxe

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Vytvoří `COleIPFrameWnd` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Volat rámci při aktivaci položky pro úpravy na místě.|
|[COleIPFrameWnd::Přemístitrámeček](#repositionframe)|Volat rámci pro přemístění v místě editační okno.|

## <a name="remarks"></a>Poznámky

Tato třída vytvoří a umístí ovládací panely v okně dokumentu aplikace kontejneru. Také zpracovává oznámení generované vložené [COleResizeBar](../../mfc/reference/coleresizebar-class.md) objektu při změně velikosti okna pro úpravy na místě.

Další informace o `COleIPFrameWnd`použití naleznete v článku [Aktivace](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="coleipframewndcoleipframewnd"></a><a name="coleipframewnd"></a>COleIPFrameWnd::COleIPFrameWnd

Vytvoří `COleIPFrameWnd` objekt a inicializuje jeho informace o stavu na místě, které jsou uloženy ve struktuře typu OLEINPLACEFRAMEINFO.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [OLEINPLACEFRAMEINFO](/windows/win32/api/oleidl/ns-oleidl-oleinplaceframeinfo) v sadě Windows SDK.

## <a name="coleipframewndoncreatecontrolbars"></a><a name="oncreatecontrolbars"></a>COleIPFrameWnd::OnCreateControlBars

Framework volá `OnCreateControlBars` funkci při aktivaci položky pro úpravy na místě.

```
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,
    CWnd* pWndDoc);

virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,
    CFrameWnd* pWndDoc);
```

### <a name="parameters"></a>Parametry

*pWndRám*<br/>
Ukazatel na okno rámce aplikace kontejneru.

*pWndDoc*<br/>
Ukazatel na okno na úrovni dokumentu kontejneru. Může být null, pokud je kontejner aplikace SDI.

### <a name="return-value"></a>Návratová hodnota

Nenulová na úspěch; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovede žádné provádění. Přepište tuto funkci a proveďte jakékoli speciální zpracování požadované při vytváření ovládacích panelů.

## <a name="coleipframewndrepositionframe"></a><a name="repositionframe"></a>COleIPFrameWnd::Přemístitrámeček

Rámec volá `RepositionFrame` členské funkce rozložení ovládacích panelů a přemístit okno pro úpravy na místě tak, aby všechny je viditelné.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt obsahující aktuální souřadnice aktuální polohy okna na místě v obrazových bodech vzhledem k oblasti klienta.

*lpClipRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt obsahující aktuální souřadnice rámečku na místě, v obrazových bodech vzhledem k oblasti klienta.

### <a name="remarks"></a>Poznámky

Rozložení ovládacích panelů v okně kontejneru se liší od rozložení prováděného okno rámce ole. Okno rámce bez OLE vypočítá pozice ovládacích panelů a jiných objektů z dané velikosti okna rámce, jako při volání [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). Klientská oblast je to, co zůstává po odečtení prostoru pro ovládací panely a jiné objekty. Okno, `COleIPFrameWnd` na druhé straně, polohy panely nástrojů v souladu s danou klientskou oblastí. Jinými slovy, pracuje "zvenčí dovnitř", `CFrameWnd::RecalcLayout` zatímco pracuje `COleIPFrameWnd::RepositionFrame` "zevnitř ven".

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Třída CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CFrameWnd](../../mfc/reference/cframewnd-class.md)
