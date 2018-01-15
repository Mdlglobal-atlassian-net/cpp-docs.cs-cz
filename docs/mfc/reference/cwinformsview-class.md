---
title: "Třída CWinFormsView | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs: C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb68e906a06d18b41d97851d8d91717ac3dd78b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
|[CWinFormsView::GetControl](#getcontrol)|Načte ukazatel ovládacího prvku Windows Forms.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název||  
|----------|-|  
|[Ovládací prvek CWinFormsView::operator ^](#operator_control)|Vrhá typu jako ukazatel do ovládacího prvku Windows Forms.|  
  
## <a name="remarks"></a>Poznámky  
 MFC používá `CWinFormsView` třídy pro hostování ovládacího prvku Windows Forms rozhraní .NET Framework v rámci zobrazení knihovny MFC. Ovládací prvek je podřízená nativní zobrazení a zabírá celého klienta MFC zobrazení. Výsledkem je podobná `CFormView` zobrazení, což umožňuje využít výhod Návrhář formulářů Windows a spuštění vytvářet bohaté zobrazení založené na formulářích.  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
> [!NOTE]
>  MFC Windows Forms integrace funguje jenom v projektech, které dynamicky propojit s knihovnou MFC (projekty, ve kterých je definován AFXDLL).  
  
> [!NOTE]
>  CWinFormsView nepodporuje rozděleném okně knihovny MFC ( [CSplitterWnd třída](../../mfc/reference/csplitterwnd-class.md)). Aktuálně pouze systému Windows Forms rozdělovače ovládací prvek je podporován.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h  
  
##  <a name="cwinformsview"></a>CWinFormsView::CWinFormsView  
 Vytvoří `CWinFormsView` objektu.  
  
```  
CWinFormsView(System::Type^ pManagedViewType);  
```  
  
### <a name="parameters"></a>Parametry  
 `pManagedViewType`  
 Ukazatel na datový typ uživatelského ovládacího prvku Windows Forms.   
  
### <a name="example"></a>Příklad  
 V následujícím příkladu `CUserView` třída dědí z `CWinFormsView` a předá typ `UserControl1` k `CWinFormsView` konstruktor. `UserControl1`je uživatelské ovládací prvek v ControlLibrary1.dll.  
  
 [!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]  
  
 [!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]  
  
##  <a name="getcontrol"></a>CWinFormsView::GetControl  
 Načte ukazatel ovládacího prvku Windows Forms.  
  
```  
System::Windows::Forms::Control^ GetControl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `System.Windows.Forms.Control` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Příklad použití Windows Forms, naleznete v části [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="operator_control"></a>Ovládací prvek CWinFormsView::operator ^  
 Vrhá typu jako ukazatel do ovládacího prvku Windows Forms.  
  
```  
operator System::Windows::Forms::Control^() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor umožňuje předat `CWinFormsView` zobrazení na funkce, které přijímají ukazatel do ovládacího prvku Windows Forms typu <xref:System.Windows.Forms.Control>.  
  
### <a name="example"></a>Příklad  
  V tématu [CWinFormsView::GetControl](#getcontrol).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CWinFormsControl – třída](../../mfc/reference/cwinformscontrol-class.md)   
 [CWinFormsDialog – třída](../../mfc/reference/cwinformsdialog-class.md)   
 [CFormView – třída](../../mfc/reference/cformview-class.md)
