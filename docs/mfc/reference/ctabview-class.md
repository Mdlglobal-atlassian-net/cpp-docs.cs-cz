---
title: Třída CtabView
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
ms.openlocfilehash: ad30cbbf5de195708d2d357a76c38b661d095c2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365925"
---
# <a name="ctabview-class"></a>Třída CtabView

Třída `CTabView` zjednodušuje použití třídy ovládacího prvku tabulátoru ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) v aplikacích, které používají architekturu dokumentu/zobrazení knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CTabbedView : public CView
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CTabView::Přidatzobrazení](#addview)|Přidá nové zobrazení do ovládacího prvku karta.|
|[CTabView::FindTab](#findtab)|Vrátí index zadaného zobrazení v ovládacím prvku karta.|
|[CTabView::GetActiveView](#getactiveview)|Vrátí ukazatel na aktuálně aktivní zobrazení.|
|[CTabView::Ovládací prvek GetTabControl](#gettabcontrol)|Vrátí odkaz na ovládací prvek tabulátoru přidružený k zobrazení.|
|[CTabView::RemoveView](#removeview)|Odebere zobrazení z ovládacího prvku karta.|
|[CTabView::SetActiveView](#setactiveview)|Aktivuje zobrazení.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CtabView::IsScrollBar](#isscrollbar)|Volat rámci při vytváření zobrazení tabulátoru k určení, zda zobrazení tabulátoru má sdílený vodorovný posuvník.|
|[Ctabview::OnActivateView](#onactivateview)|Volat rámci při zobrazení tabulátoru je aktivní nebo neaktivní.|

## <a name="remarks"></a>Poznámky

Tato třída usnadňuje vložení zobrazení s kartami do aplikace dokumentu nebo zobrazení. `CTabView`je `CView`odvozená třída, která obsahuje `CMFCTabCtrl` vložený objekt. `CTabView`zpracovává všechny zprávy potřebné `CMFCTabCtrl` pro podporu objektu. Jednoduše odvodit třídu z `CTabView` a `CView`připojte ji do aplikace `AddView` a potom přidejte odvozené třídy pomocí metody. Ovládací prvek karta zobrazí tato zobrazení jako karty.

Můžete mít například dokument, který může být reprezentován různými způsoby: jako tabulka, graf, upravitelný formulář a tak dále. Můžete vytvořit jednotlivé pohledy kreslení dat podle `CTabView`potřeby, vložte je do -odvozený objekt a mít je záložkou bez dalšího kódování.

[TabbedView Ukázka: Aplikace zobrazení s kartami knihovny MFC](../../overview/visual-cpp-samples.md) ilustruje použití `CTabView`aplikace .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CTabView` se používá v TabbedView vzorku.

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxTabView.h

## <a name="ctabviewaddview"></a><a name="addview"></a>CTabView::Přidatzobrazení

Přidá zobrazení do ovládacího prvku karta.

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Parametry

*pViewClass*<br/>
[v] Ukazatel na třídu runtime vloženého zobrazení.

*strViewLabel*<br/>
[v] Určuje text karty.

*iIndex*<br/>
[v] Určuje pozici založenou na nule, do které má být pohled vložen. Pokud je pozice -1, nová karta je vložena na konci.

*pKontext*<br/>
[v] Ukazatel na `CCreateContext` zobrazení.

### <a name="return-value"></a>Návratová hodnota

Index zobrazení, pokud je tato metoda úspěšná. Jinak -1.

### <a name="remarks"></a>Poznámky

Voláním této funkce přidáte zobrazení do ovládacího prvku tabulátoru, který je vložen ý do rámečku.

## <a name="ctabviewfindtab"></a><a name="findtab"></a>CTabView::FindTab

Vrátí index zadaného zobrazení v ovládacím prvku karta.

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>Parametry

*hWndView*<br/>
[v] Úchyt zobrazení.

### <a name="return-value"></a>Návratová hodnota

Index zobrazení, pokud je nalezen; jinak -1.

### <a name="remarks"></a>Poznámky

Volání této funkce načíst index zobrazení, který má zadaný popisovač.

## <a name="ctabviewgetactiveview"></a><a name="getactiveview"></a>CTabView::GetActiveView

Vrátí ukazatel na aktuálně aktivní zobrazení.

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na aktivní zobrazení nebo NULL, pokud neexistuje žádné aktivní zobrazení.

### <a name="remarks"></a>Poznámky

## <a name="ctabviewgettabcontrol"></a><a name="gettabcontrol"></a>CTabView::Ovládací prvek GetTabControl

Vrátí odkaz na ovládací prvek tabulátoru přidružený k zobrazení.

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na ovládací prvek tabulátoru přidružený k zobrazení.

## <a name="ctabviewisscrollbar"></a><a name="isscrollbar"></a>CtabView::IsScrollBar

Volat rámci při vytváření zobrazení tabulátoru k určení, zda zobrazení tabulátoru má sdílený vodorovný posuvník.

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud má být zobrazení tabulátoru vytvořeno společně se sdíleným posuvníkem. V opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto metodu při vytváření objektu *CTabView.*

Přepsat *IsScrollBar* metoda v *CTabView*-odvozené třídy a vrátit TRUE, pokud chcete vytvořit zobrazení, které má sdílený vodorovný posuvník.

## <a name="ctabviewonactivateview"></a><a name="onactivateview"></a>Ctabview::OnActivateView

Volat rámci při zobrazení tabulátoru je aktivní nebo neaktivní.

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>Parametry

*Prohlédni*<br/>
[v] Ukazatel na zobrazení.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovede žádné provádění. Přepsat tuto metodu `CTabView`v odvozené třídy zpracovat toto oznámení.

## <a name="ctabviewremoveview"></a><a name="removeview"></a>CTabView::RemoveView

Odebere zobrazení z ovládacího prvku karta.

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
[v] Index zobrazení odebrat.

### <a name="return-value"></a>Návratová hodnota

Index odebráného zobrazení, pokud je tato metoda úspěšná. Jinak -1.

### <a name="remarks"></a>Poznámky

## <a name="ctabviewsetactiveview"></a><a name="setactiveview"></a>CTabView::SetActiveView

Aktivuje zobrazení.

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
[v] Index na základě nuly zobrazení tabulátoru.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo zadané zobrazení aktivní, NEPRAVDA, pokud je index zobrazení neplatný.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTabCtrl](../../mfc/reference/ctabview-class.md)<br/>
[Třída CView](../../mfc/reference/cview-class.md)
