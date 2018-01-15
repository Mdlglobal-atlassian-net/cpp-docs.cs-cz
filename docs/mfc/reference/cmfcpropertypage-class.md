---
title: "Třída CMFCPropertyPage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
dev_langs: C++
helpviewer_keywords: CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d11f9e4849a0c632e6a63d794dc294fa504d196a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage – třída
`CMFCPropertyPage` Třída podporuje zobrazení místní nabídky na stránku vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Vytvoří `CMFCPropertyPage` objektu.|  
|`CMFCPropertyPage::~CMFCPropertyPage`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCPropertyPage::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|`CMFCPropertyPage::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|`CMFCPropertyPage::OnSetActive`|Tento člen funkce je volána rámcem, když na stránce je volená uživatelem a stránkou bude aktivní. (Přepisuje [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|  
|`CMFCPropertyPage::PreTranslateMessage`|Přeloží zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. Další informace a syntaxe využívající metody najdete v tématu [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Přepisuje `CPropertyPage::PreTranslateMessage`.)|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCPropertyPage` Třída reprezentuje jednotlivých stránek vlastností známé jako dialogové okno karty.  
  
 Použití `CMFCPropertyPage` třídy společně s [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) třídy. Na stránce vlastností používat nabídky, nahraďte všechny výskyty `CPropertyPage` třídy s `CMFCPropertyPage` třídy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpropertypage.h  
  
##  <a name="cmfcpropertypage"></a>CMFCPropertyPage::CMFCPropertyPage  
 Vytvoří `CMFCPropertyPage` objektu.  
  
```  
CMFCPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption=0);

 
CMFCPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption=0);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDTemplate`  
 ID prostředku šablony pro tuto stránku.  
  
 `nIDCaption`  
 ID prostředku popisku se umístí na kartě pro tuto stránku. Pokud je 0, název se získávají z pole šablony dialogového okna pro tuto stránku. Výchozí hodnota je 0.  
  
 `lpszTemplateName`  
 Bodů na název šablony pro tuto stránku. Nemůže být `NULL`.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Další informace o parametrech konstruktor najdete v tématu [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertySheet – třída](../../mfc/reference/cmfcpropertysheet-class.md)
