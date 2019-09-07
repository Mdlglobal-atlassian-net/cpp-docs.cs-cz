---
title: COleIPFrameWnd – třída
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
ms.openlocfilehash: 8eab2ddfc778900b53d77105f1d8215a2c095e9f
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741562"
---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd – třída

Základ pro místní editační okno vaší aplikace.

## <a name="syntax"></a>Syntaxe

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|`COleIPFrameWnd` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Volá se rozhraním, když se položka aktivuje pro místní úpravy.|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Volá se rozhraním, aby se přeumístilo místní okno pro úpravy.|

## <a name="remarks"></a>Poznámky

Tato třída vytvoří ovládací prvky pro umístění v rámci okna dokumentu aplikace kontejneru. Také zpracovává oznámení vygenerovaná vloženým objektem [COleResizeBar](../../mfc/reference/coleresizebar-class.md) , když uživatel změní velikost místního okna pro úpravy.

Další informace o použití nástroje `COleIPFrameWnd`najdete v článku [Aktivace](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="coleipframewnd"></a>COleIPFrameWnd::COleIPFrameWnd

`COleIPFrameWnd` Vytvoří objekt a inicializuje své místní informace o stavu, které jsou uloženy ve struktuře typu OLEINPLACEFRAMEINFO.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [OLEINPLACEFRAMEINFO](/windows/win32/api/oleidl/ns-oleidl-oleinplaceframeinfo) v Windows SDK.

##  <a name="oncreatecontrolbars"></a>COleIPFrameWnd:: OnCreateControlBars

Rozhraní volá funkci, `OnCreateControlBars` když je položka aktivována pro místní úpravy.

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
Ukazatel na okno na úrovni dokumentu kontejneru. Může mít hodnotu NULL, pokud je kontejner aplikace SDI.

### <a name="return-value"></a>Návratová hodnota

Nenulové při úspěchu; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovádí žádnou akci. Přepište tuto funkci, aby se při vytváření řídicích panelů prováděly zvláštní požadavky na zpracování.

##  <a name="repositionframe"></a>COleIPFrameWnd::RepositionFrame

Rozhraní volá `RepositionFrame` členskou funkci pro rozložení ovládacích panelů a přemístění místního okna pro úpravy tak, aby bylo viditelné.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt obsahující souřadnice aktuálního umístění okna rámce v pixelech vzhledem k oblasti klienta.

*lpClipRect*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt obsahující aktuální souřadnice oříznutí (v pixelech), které jsou relativní vzhledem ke klientské oblasti.

### <a name="remarks"></a>Poznámky

Rozložení ovládacích panelů v okně kontejneru se liší od okna, které se provádí v okně s rámečkem bez OLE. Okno s rámečkem bez OLE vypočítá pozice ovládacích panelů a dalších objektů z dané velikosti rámečku okna, jako v volání metody [CFrameWnd:: RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). Klientská oblast je to, co zbývá po prostoru pro ovládací panely a jiné objekty se odečtou. `COleIPFrameWnd` Okno na druhé straně umisťuje panely nástrojů podle dané klientské oblasti. Jinými slovy `CFrameWnd::RecalcLayout` funguje "z vnějšího" v "," zatímco `COleIPFrameWnd::RepositionFrame` funguje "z vnitřku."

## <a name="see-also"></a>Viz také:

[HIERSVR Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)
