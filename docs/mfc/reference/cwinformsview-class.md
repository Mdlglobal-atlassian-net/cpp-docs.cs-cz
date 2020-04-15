---
title: Třída CWinFormsView
ms.date: 11/04/2016
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
ms.openlocfilehash: 6eb6b9e385e9dbc96eb3b62ffb80909e54569e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369595"
---
# <a name="cwinformsview-class"></a>Třída CWinFormsView

Poskytuje obecné funkce pro hostování ovládacího prvku Windows Forms jako zobrazení knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CWinFormsView::CWinFormsView](#cwinformsview)|Vytvoří `CWinFormsView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CWinFormsView::Ovládací prvek GetControl](#getcontrol)|Načte ukazatel na ovládací prvek Windows Forms.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)||
|----------|-|
|[CWinFormsView::Ovládací prvek operátoru^](#operator_control)|Přetypování typu jako ukazatel ovládacího prvku Windows Forms.|

## <a name="remarks"></a>Poznámky

Knihovna MFC používá třídu `CWinFormsView` k hostování ovládacího prvku .NET Framework Windows Forms v rámci zobrazení knihovny MFC. Ovládací prvek je podřízený nativní zobrazení a zabírá celou oblast klienta zobrazení knihovny MFC. Výsledek je podobný `CFormView` zobrazení, což umožňuje využít výhod návrháře formulářů systému Windows a čas spuštění k vytvoření zobrazení založených na bohatém formuláři.

Další informace o používání formulářů Systému Windows naleznete [v tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
> Integrace mfc Windows Forms funguje pouze v projektech, které dynamicky propojují s knihovnou MFC (projekty, ve kterých je definována knihovna AFXDLL).

> [!NOTE]
> CWinFormsView nepodporuje okno rozdělovače knihovny MFC ( [Třída CSplitterWnd).](../../mfc/reference/csplitterwnd-class.md) V současné době je podporován pouze ovládací prvek Windows Forms Splitter.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h

## <a name="cwinformsviewcwinformsview"></a><a name="cwinformsview"></a>CWinFormsView::CWinFormsView

Vytvoří `CWinFormsView` objekt.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Parametry

*pManagedViewType*<br/>
Ukazatel na datový typ uživatelského ovládacího prvku Windows Forms.

### <a name="example"></a>Příklad

V následujícím příkladu `CUserView` třída dědí z `CWinFormsView` a `UserControl1` předá typ konstruktoru. `CWinFormsView` `UserControl1`je vlastní ovládací prvek v ControlLibrary1.dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

## <a name="cwinformsviewgetcontrol"></a><a name="getcontrol"></a>CWinFormsView::Ovládací prvek GetControl

Načte ukazatel na ovládací prvek Windows Forms.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `System.Windows.Forms.Control` objekt.

### <a name="remarks"></a>Poznámky

Příklad použití formulářů systému Windows naleznete v [tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsviewoperator-control"></a><a name="operator_control"></a>CWinFormsView::Ovládací prvek operátoru^

Přetypování typu jako ukazatel ovládacího prvku Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Poznámky

Tento operátor umožňuje předat `CWinFormsView` zobrazení funkcím, které přijímají ukazatel na <xref:System.Windows.Forms.Control>ovládací prvek Windows Forms typu .

### <a name="example"></a>Příklad

  Viz [CWinFormsView::GetControl](#getcontrol).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)<br/>
[Třída CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)
