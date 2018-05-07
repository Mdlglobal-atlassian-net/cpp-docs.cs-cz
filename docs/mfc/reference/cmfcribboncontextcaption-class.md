---
title: Třída CMFCRibbonContextCaption | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2fa63de2a633b2c8a9fff975de6eaaae7cbb470c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribboncontextcaption-class"></a>CMFCRibbonContextCaption – třída
Implementuje barevnou popisek, který se zobrazí v horní části pásu karet nebo kategorie kontextu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonContextCaption : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCRibbonContextCaption::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CMFCRibbonContextCaption::GetColor](#getcolor)|Vrátí barva titulek.|  
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||  
|`CMFCRibbonContextCaption::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída nemůže být přímo vytvořeny instance. [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md) Tato třída třída interně používá k přidání barev do kategorií pásu karet.  
  
 Chcete-li nastavit barvu pro pás karet kategorie, volejte [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor). Chcete-li nastavit barvu pro kontext kategorie, volejte [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonBar.h  
  
##  <a name="getcolor"></a>  CMFCRibbonContextCaption::GetColor  
 Vrátí barvu pozadí popisku.  
  
```  
AFX_RibbonCategoryColor GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota může být jedna z následujících výčtové hodnoty:  
  
- `AFX_CategoryColor_None`  
  
- `AFX_CategoryColor_Red`  
  
- `AFX_CategoryColor_Orange`  
  
- `AFX_CategoryColor_Yellow`  
  
- `AFX_CategoryColor_Green`  
  
- `AFX_CategoryColor_Blue`  
  
- `AFX_CategoryColor_Indigo`  
  
- `AFX_CategoryColor_Violet`  
  
### <a name="remarks"></a>Poznámky  
 Barva titulek můžete nastavit voláním [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) nebo [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).  
  
##  <a name="getrighttabx"></a>  CMFCRibbonContextCaption::GetRightTabX  
 Načte pozici pravé hrany karta kategorie.  
  
```  
int GetRightTabX() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací pravé X-hodnotu ohraničující obdélník `CMFCRibbonCategory` karta objektu, nebo hodnota -1, pokud se zkrátí na kartě.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonCategory – třída](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
