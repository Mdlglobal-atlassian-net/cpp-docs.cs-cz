---
title: Třída CMFCRibbonCustomizePropertyPage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 542c34fc02eca1f090072f49b9688d3edd4d78e6
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040672"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage – třída
Implementuje vlastní stránky pro **přizpůsobit** dialogové okno v aplikacích založených na pásu karet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|Vytvoří `CMFCRibbonCustomizePropertyPage` objektu.|  
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Přidá vlastní kategorii, která **příkazy** – pole se seznamem.|  
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Volá se v systému, když uživatel klikne **OK** na **přizpůsobit** dialogové okno.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete přidat vlastní příkazy **přizpůsobit** dialogové okno, je nutné zpracovat zprávu AFX_WM_ON_RIBBON_CUSTOMIZE. V popisovač zpráv, vytváření instancí `CMFCRibbonCustomizePropertyPage` objektu v zásobníku. Vytvořte seznam, který vlastní příkazy a pak zavolají `AddCustomCategory` přidat nové stránky **přizpůsobit** dialogové okno.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCRibbonCustomizePropertyPage` objektu a přidat vlastní kategorii.  
  
 [!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
 [CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribboncustomizedialog.h  
  
##  <a name="addcustomcategory"></a>  CMFCRibbonCustomizePropertyPage::AddCustomCategory  
 Přidá vlastní kategorii, která **příkazy** – pole se seznamem.  
  
```  
void AddCustomCategory(
    LPCTSTR lpszName,  
    const CList<UINT, UINT>& lstIDS);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] *lpszName*|Určuje název vlastní kategorie.|  
|[v] *lstIDS*|Obsahuje příkaz pásu karet ID zobrazený v vlastní kategorie.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá kategorie s názvem *lpszName* k **příkazy** – pole se seznamem. Pokud uživatel vybere kategorii, příkazy zadaná v *lstIDS* se zobrazí v seznamu příkazů.  
  
##  <a name="cmfcribboncustomizepropertypage"></a>  CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage  
 Vytvoří `CMFCRibbonCustomizePropertyPage` objektu.  
  
```  
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pRibbonBar*  
 Ukazatel na ovládacího prvku pásu karet, pro které možnosti chcete přizpůsobit.  
  
##  <a name="onok"></a>  CMFCRibbonCustomizePropertyPage::OnOK  
 Calleld v systému, když uživatel klikne **OK** na **přizpůsobit** dialogové okno.  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace použije vybrané v možnosti **přizpůsobit** dialogové okno pro panel nástrojů Rychlý přístup.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
