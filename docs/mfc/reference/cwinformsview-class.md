---
title: CWinFormsView – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4d90f2a7f964d264966d5254d051ebddaf2baa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448139"
---
# <a name="cwinformsview-class"></a>CWinFormsView – třída

Poskytuje obecné funkce pro hostování ovládacího prvku Windows Forms jako zobrazení MFC.

## <a name="syntax"></a>Syntaxe

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWinFormsView::CWinFormsView](#cwinformsview)|Vytvoří `CWinFormsView` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWinFormsView::GetControl](#getcontrol)|Načte ukazatel na ovládacím prvku Windows Forms.|

### <a name="public-operators"></a>Veřejné operátory

|Název||
|----------|-|
|[Ovládací prvek CWinFormsView::operator ^](#operator_control)|Přetypování typu jako ukazatel na ovládacím prvku Windows Forms.|

## <a name="remarks"></a>Poznámky

Knihovna MFC používá `CWinFormsView` třídy pro hostování ovládacího prvku formulářů Windows rozhraní .NET Framework v rámci zobrazení MFC. Ovládací prvek je podřízený nativní zobrazení a zabírá celé klientské oblasti zobrazení MFC. Výsledek je podobný `CFormView` zobrazení, díky tomu můžete využít výhod Návrhář formulářů Windows a běhu k vytvoření zobrazení založené na formulářích.

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
>  Integrace formulářů Windows MFC funguje jenom v projektech, které dynamicky propojit s knihovnou MFC (projekty, ve kterých je definována AFXDLL).

> [!NOTE]
>  CWinFormsView nepodporuje okna s rozdělovačem knihovny MFC ( [CSplitterWnd – třída](../../mfc/reference/csplitterwnd-class.md)). Aktuálně pouze Windows Forms příčky ovládací prvek je podporován.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h

##  <a name="cwinformsview"></a>  CWinFormsView::CWinFormsView

Vytvoří `CWinFormsView` objektu.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Parametry

*pManagedViewType*<br/>
Ukazatel na datový typ uživatelského ovládacího prvku Windows Forms.

### <a name="example"></a>Příklad

V následujícím příkladu `CUserView` třída dědí z `CWinFormsView` a předává typ `UserControl1` k `CWinFormsView` konstruktoru. `UserControl1` je vlastními silami sestavených ovládacího prvku v ControlLibrary1.dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>  CWinFormsView::GetControl

Načte ukazatel na ovládacím prvku Windows Forms.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `System.Windows.Forms.Control` objektu.

### <a name="remarks"></a>Poznámky

Příklad toho, jak pomocí Windows Forms, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_control"></a>  Ovládací prvek CWinFormsView::operator ^

Přetypování typu jako ukazatel na ovládacím prvku Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Poznámky

Tento operátor umožňuje předat `CWinFormsView` zobrazení a funkce, které přijímají ukazatel na ovládací prvek Windows Forms typu <xref:System.Windows.Forms.Control>.

### <a name="example"></a>Příklad

  Zobrazit [CWinFormsView::GetControl](#getcontrol).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl – třída](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog – třída](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)
