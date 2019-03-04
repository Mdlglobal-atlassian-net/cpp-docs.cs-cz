---
title: Třída CSplitterWndEx
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: 8dedad4e99a37b13dc618859c8e6d8a83a65ea76
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265142"
---
# <a name="csplitterwndex-class"></a>Třída CSplitterWndEx

Představuje vlastní dělící okno.

## <a name="syntax"></a>Syntaxe

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|Výchozí konstruktor.|
|`CSplitterWndEx::~CSplitterWndEx`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Volá se rozhraním, chcete-li nakreslit okno s rozdělovačem. (Přepíše [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|

## <a name="remarks"></a>Poznámky

Přepsat `OnDrawSplitter` metodu za účelem přizpůsobení vzhledu součásti grafické okno s rozdělovačem.

`CSplitterWndEx` Třída se používá spolu s [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox), a [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) metody, které jsou Správce vzhledu implementované. Způsobí vizuálního správce, chcete-li nakreslit rozděleného okna ve vaší aplikaci nahradit deklarace `CSplitterWnd` třídy s `CSplitterWndEx` třídy. Pro rámec okna aplikace rozdělovač okna třídy deklarované v CMainFrame – třída, která se nachází v mainfrm.h. Příklad najdete v tématu `OutlookDemo` ukázku v adresáři ukázky.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd.](csplitterwnd-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxsplitterwndex.h

##  <a name="ondrawsplitter"></a>  CSplitterWndEx::OnDrawSplitter

Volá se rozhraním, chcete-li nakreslit okno s rozdělovačem.

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení. Pokud má parametr hodnotu NULL, rozhraní překreslí aktivní okno.

*nType*<br/>
[in] Jeden z `CSplitterWnd::ESplitType` hodnot výčtu, která určuje prvku rozdělovač okna pro kreslení. Platné hodnoty jsou `splitBox`, `splitBar`, `splitIntersection`, a `splitBorder`.

*Rect*<br/>
[in] Ohraničující obdélník, který určuje rozměry a umístění pro vykreslení elementu zadané rozdělovací okna.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../hierarchy-chart.md)<br/>
[Třídy](mfc-classes.md)<br/>
[CSplitterWnd – třída](csplitterwnd-class.md)<br/>
[CMFCVisualManager – třída](cmfcvisualmanager-class.md)
