---
title: Ctabview – třída
ms.date: 11/04/2016
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
ms.openlocfilehash: 5ac62d04c38dbddda90d2f33a9c14c9c131fcd9c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326592"
---
# <a name="ctabview-class"></a>Ctabview – třída

`CTabView` Třída zjednodušuje použití třídy ovládacího prvku karta ( [cmfctabctrl –](../../mfc/reference/ctabview-class.md)) v aplikacích, které používají architekturu document/view knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CTabbedView : public CView
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTabView::AddView](#addview)|Přidá nové zobrazení pro ovládací prvek karty.|
|[CTabView::FindTab](#findtab)|Vrátí index zadané zobrazení v ovládacím prvku karty.|
|[CTabView::GetActiveView](#getactiveview)|Vrací ukazatel k aktuálně aktivnímu zobrazení.|
|[CTabView::GetTabControl](#gettabcontrol)|Vrátí odkaz na ovládací prvek karty, které jsou přidružené k zobrazení.|
|[CTabView::RemoveView](#removeview)|Odstraní zobrazení z ovládacího prvku karta.|
|[CTabView::SetActiveView](#setactiveview)|Aktivuje zobrazení.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CTabView::IsScrollBar](#isscrollbar)|Volá se rozhraním při vytváření zobrazení karta slouží k určení, zda má kartě se zobrazením sdílené vodorovný posuvník.|
|[CTabView::OnActivateView](#onactivateview)|Volá se rozhraním, když se kartě se zobrazením je aktivní nebo neaktivní.|

## <a name="remarks"></a>Poznámky

Tato třída umožňuje snadno převést zobrazení se záložkami do dokumentů/zobrazení aplikace. `CTabView` je `CView`-odvozené třídy, která obsahuje vložený `CMFCTabCtrl` objektu. `CTabView` zpracovává všechny zprávy, které jsou potřeba pro podporu `CMFCTabCtrl` objektu. Jednoduše odvodit třídu z `CTabView` a zařadit ho do své aplikace a pak přidejte `CView`-odvozené třídy pomocí `AddView` metody. Ovládací prvek karty zobrazí jako karty těchto zobrazení.

Například může mít dokument, který může být reprezentována různými způsoby: jako tabulky, graf, Upravitelný formulář a tak dále. Můžete vytvořit jednotlivé zobrazení vykreslování data podle potřeby, vložte je do vašeho `CTabView`-odvozenému objektu a potom kliknul na záložkách bez jakékoli další kódování.

[Ukázka TabbedView: Zobrazení aplikace s kartami knihovny MFC](../../visual-cpp-samples.md) ukazuje využití `CTabView`.

## <a name="example"></a>Příklad

Následující příklad ukazuje jak `CTabView` se používá v ukázce TabbedView.

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxTabView.h

##  <a name="addview"></a>  CTabView::AddView

Přidá do ovládacího prvku Karta zobrazení.

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Parametry

*pViewClass*<br/>
[in] Ukazatel na třídu runtime vložená zobrazení.

*strViewLabel*<br/>
[in] Určuje text, na kartě.

*iIndex*<br/>
[in] Určí založený na nule pozici, na kterém se má vložit zobrazení. Pokud na pozici, je -1 je vložen novou kartu na konci.

*pContext*<br/>
[in] Ukazatel `CCreateContext` zobrazení.

### <a name="return-value"></a>Návratová hodnota

Index zobrazení, pokud tato metoda bude úspěšná. Jinak -1.

### <a name="remarks"></a>Poznámky

Voláním této funkce Přidat zobrazení do ovládacího prvku karta, který je vložený v objektu frame.

##  <a name="findtab"></a>  CTabView::FindTab

Vrátí index zadané zobrazení v ovládacím prvku karty.

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>Parametry

*hWndView*<br/>
[in] Popisovač zobrazení.

### <a name="return-value"></a>Návratová hodnota

Index zobrazení, pokud je nalezen; jinak -1.

### <a name="remarks"></a>Poznámky

Volání této funkce načtete index zobrazení, který má Zadaný popisovač.

##  <a name="getactiveview"></a>  CTabView::GetActiveView

Vrací ukazatel na aktuálně aktivní zobrazení.

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na aktivní zobrazení, nebo hodnota NULL, pokud neexistuje žádná aktivní zobrazení.

### <a name="remarks"></a>Poznámky

##  <a name="gettabcontrol"></a>  CTabView::GetTabControl

Vrátí odkaz na ovládací prvek karty, které jsou přidružené k zobrazení.

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na ovládací prvek karty, které jsou přidružené k zobrazení.

##  <a name="isscrollbar"></a>  CTabView::IsScrollBar

Volá se rozhraním při vytváření zobrazení karta slouží k určení, zda má kartě se zobrazením sdílené vodorovný posuvník.

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud kartě se zobrazením by měl být vytvořen spolu s sdílené posuvníku. V opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu při *ctabview –* objekt se vytváří.

Přepsat *IsScrollBar* metoda *ctabview –*-odvozené třídy a vrací TRUE, pokud chcete vytvořit zobrazení, který má sdílené vodorovný posuvník.

##  <a name="onactivateview"></a>  CTabView::OnActivateView

Volá se rozhraním, když se kartě se zobrazením je aktivní nebo neaktivní.

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>Parametry

*Zobrazení*<br/>
[in] Ukazatel na zobrazení.

### <a name="remarks"></a>Poznámky

Výchozí implementace nemá žádný účinek. Potlačí tuto metodu v `CTabView`-odvozené třídy pro zpracování tohoto oznámení.

##  <a name="removeview"></a>  CTabView::RemoveView

Odstraní zobrazení z ovládacího prvku karta.

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
[in] Index zobrazení odebrat.

### <a name="return-value"></a>Návratová hodnota

Index zobrazení odebrané, pokud tato metoda bude úspěšná. V opačném případě hodnota-1.

### <a name="remarks"></a>Poznámky

##  <a name="setactiveview"></a>  CTabView::SetActiveView

Aktivuje zobrazení.

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
[in] Index založený na nule kartě se zobrazením.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud zadané zobrazení se provádí aktivní, FALSE v případě zobrazení indexu je neplatný.

### <a name="remarks"></a>Poznámky

Další informace najdete v části [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTabCtrl](../../mfc/reference/ctabview-class.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)
