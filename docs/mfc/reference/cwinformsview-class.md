---
title: CWinFormsView – třída
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
ms.openlocfilehash: f4a5e6b88527dad8606092ccebd4899bba5181f6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420860"
---
# <a name="cwinformsview-class"></a>CWinFormsView – třída

Poskytuje obecné funkce pro hostování ovládacího prvku model Windows Forms jako zobrazení MFC.

## <a name="syntax"></a>Syntaxe

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWinFormsView:: CWinFormsView](#cwinformsview)|Vytvoří objekt `CWinFormsView`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWinFormsView:: GetControl](#getcontrol)|Načte ukazatel na ovládací prvek model Windows Forms.|

### <a name="public-operators"></a>Veřejné operátory

|Název||
|----------|-|
|[CWinFormsView:: operator – ovládací prvek ^](#operator_control)|Přetypování typu jako ukazatele na ovládací prvek model Windows Forms.|

## <a name="remarks"></a>Poznámky

Knihovna MFC používá třídu `CWinFormsView` k hostování .NET Framework ovládacího prvku model Windows Forms v zobrazení knihovny MFC. Ovládací prvek je podřízeným prvkem nativního zobrazení a zabírá celou klientskou oblast zobrazení knihovny MFC. Výsledek je podobný zobrazení `CFormView`, což vám umožní využít výhod model Windows Formsho návrháře a doby spuštění k vytvoření formulářů s bohatou možností zobrazení.

Další informace o použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
>  Knihovna MFC model Windows Forms Integration funguje pouze v projektech, které jsou propojeny dynamicky s knihovnou MFC (projekty, ve kterých je definována AFXDLL –).

> [!NOTE]
>  CWinFormsView nepodporuje okno rozdělení knihovny MFC ( [Třída CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)). V současné době je podporován pouze ovládací prvek rozdělovače model Windows Forms.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms. h

##  <a name="cwinformsview"></a>CWinFormsView:: CWinFormsView

Vytvoří objekt `CWinFormsView`.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Parametry

*pManagedViewType*<br/>
Ukazatel na datový typ uživatelského ovládacího prvku model Windows Forms.

### <a name="example"></a>Příklad

V následujícím příkladu třída `CUserView` dědí z `CWinFormsView` a předá typ `UserControl1` konstruktoru `CWinFormsView`. `UserControl1` je uživatelsky sestavený ovládací prvek v knihovně ControlLibrary1. dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>CWinFormsView:: GetControl

Načte ukazatel na ovládací prvek model Windows Forms.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `System.Windows.Forms.Control`.

### <a name="remarks"></a>Poznámky

Příklad použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_control"></a>CWinFormsView:: operator – ovládací prvek ^

Přetypování typu jako ukazatele na ovládací prvek model Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Poznámky

Tento operátor umožňuje předat `CWinFormsView` zobrazení funkcí, které přijímají ukazatel na ovládací prvek model Windows Forms typu <xref:System.Windows.Forms.Control>.

### <a name="example"></a>Příklad

  Viz [CWinFormsView:: GetControl](#getcontrol).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl – třída](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog – třída](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)
