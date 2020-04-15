---
title: CSplitterWndEx – třída
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: d7952e3082bf68cff7ad9ba218073081ee522320
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363926"
---
# <a name="csplitterwndex-class"></a>CSplitterWndEx – třída

Představuje vlastní okno rozdělovače.

## <a name="syntax"></a>Syntaxe

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|Výchozí konstruktor.|
|`CSplitterWndEx::~CSplitterWndEx`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Volat rámci nakreslit okno rozdělovače. (Přepíše [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|

## <a name="remarks"></a>Poznámky

Přepište `OnDrawSplitter` metodu přizpůsobit vzhled grafických součástí okna rozdělovače.

Třída `CSplitterWndEx` se používá společně s [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)a [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) metody, které jsou implementovány vizuální manažer. Chcete-li způsobit vizuální správce nakreslit okno rozdělovače ve `CSplitterWnd` vaší `CSplitterWndEx` aplikaci, nahradit deklarace třídy s třídou. Pro aplikace okna rámce je třída okna rozdělovače deklarována ve třídě CMainFrame, která je umístěna v mainfrm.h. Příklad naleznete v `OutlookDemo` ukázce v adresáři Ukázky.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](cobject-class.md)

[CCmdCíl](ccmdtarget-class.md)

[Cwnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxsplitterwndex.h

## <a name="csplitterwndexondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter

Volat rámci nakreslit okno rozdělovače.

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení. Pokud je tento parametr NULL, rozhraní překreslí aktivní okno.

*nTyp*<br/>
[v] Jedna z `CSplitterWnd::ESplitType` hodnot výčtu, která určuje prvek okna rozdělovače k nakreslení. Platné hodnoty `splitBox` `splitBar`jsou `splitIntersection`, `splitBorder`, a .

*Rect*<br/>
[v] Ohraničující obdélník, který určuje rozměry a umístění pro nakreslení zadaného prvku okna rozdělovače.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../hierarchy-chart.md)<br/>
[Třídy](mfc-classes.md)<br/>
[CSplitterWnd – třída](csplitterwnd-class.md)<br/>
[CMFCVisualManager – třída](cmfcvisualmanager-class.md)
