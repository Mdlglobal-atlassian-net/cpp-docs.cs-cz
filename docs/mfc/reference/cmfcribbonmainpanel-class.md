---
title: "Třída CMFCRibbonMainPanel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8b5508abdc90c4c566d078f2f75c30822c7a18e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel – třída
Implementuje panely pásu karet, která se zobrazí po kliknutí na tlačítko [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonMainPanel : public CMFCRibbonPanel  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Výchozí konstruktor.|  
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonMainPanel::Add](#add)|Přidá element pásu karet do levého podokna tlačítko panelu aplikace. (Přepisuje [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).)|  
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Přidá do nabídky seznam posledních souborů v textovém řetězci.|  
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Přidá element pásu karet na dolním podokně panelu aplikace pásu karet.|  
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Přidá element pásu karet do pravého podokna tlačítko panelu aplikace.|  
|`CMFCRibbonMainPanel::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Vrátí obdélníku, který představuje oblasti na hlavním panelu pásu karet.|  
|`CMFCRibbonMainPanel::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní zobrazuje `CMFCRibbonMainPanel` při otevření panelu aplikací. Obsahuje tři podokna:  
  
-   V levém podokně obsahuje příkazy související se soubory, jako například **otevřete**, **Uložit**, **tiskových**, a **Zavřít**. Chcete-li přidat příkaz do v tomto podokně, volejte [CMFCRibbonMainPanel::Add](#add).  
  
-   V pravém podokně obsahuje možnosti, které mění příkaz, který klikněte v levém podokně. Například pokud kliknete na tlačítko **uložit jako** v levém podokně, v pravém podokně můžete zobrazit dostupné typy souborů. Chcete-li přidat položku do tohoto podokna, volejte [CMFCRibbonMainPanel::AddToRight](#addtoright).  
  
-   Dolní podokno obsahuje tlačítka, která umožňují ke změně nastavení aplikace a ukončení programu. Chcete-li přidat položku do tohoto podokna, volejte [CMFCRibbonMainPanel::AddToBottom](#addtobottom).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
 [CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonMainPanel.h  
  
##  <a name="add"></a>CMFCRibbonMainPanel::Add  
 Přidá element pásu karet do levého podokna tlačítko panelu aplikace.  
  
```  
virtual void Add(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out]`pElem`  
 Ukazatel na pásu karet elementu, který chcete přidat do hlavní panel.  
  
### <a name="remarks"></a>Poznámky  
 Přidá element pásu karet na panel. Elementy přidané pomocí této metody bude nacházet v levém sloupci na hlavním panelu.  
  
##  <a name="addrecentfileslist"></a>CMFCRibbonMainPanel::AddRecentFilesList  
 Přidá do nabídky seznam posledních souborů v textovém řetězci.  
  
```  
void AddRecentFilesList(
    LPCTSTR lpszLabel,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszLabel`  
 Určuje řetězec, přidejte do seznamu posledních souborů.  
  
 `nWidth`  
 Určuje šířku v pixelech panelu seznam posledních souborů.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addtobottom"></a>CMFCRibbonMainPanel::AddToBottom  
 Přidá element pásu karet na dolním podokně panelu aplikace pásu karet.  
  
```  
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out]`pElem`  
 Ukazatel na pásu karet elementu, který chcete přidat do dolní části na hlavním panelu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addtoright"></a>CMFCRibbonMainPanel::AddToRight  
 Přidá element pásu karet do pravého podokna tlačítko panelu aplikace.  
  
```  
void AddToRight(
    CMFCRibbonBaseElement* pElem,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>Parametry  
 `pElem`  
 Ukazatel na pásu karet element mají být přidány do pravé straně hlavního panelu.  
  
 `nWidth`  
 Určuje šířku v pixelech pravém panelu.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete přidat element pásu karet na pravém panelu. Na pravém panelu obvykle zobrazí seznam naposledy použitých souborů, ale můžete přidat jakýkoli další pásu karet prvek sem.  
  
##  <a name="getcommandsframe"></a>CMFCRibbonMainPanel::GetCommandsFrame  
 Vrátí obdélníku, který představuje oblasti na hlavním panelu pásu karet.  
  
```  
CRect GetCommandsFrame() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Obdélníku, která představuje oblasti na hlavním panelu pásu karet.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel – třída](../../mfc/reference/cmfcribbonpanel-class.md)
