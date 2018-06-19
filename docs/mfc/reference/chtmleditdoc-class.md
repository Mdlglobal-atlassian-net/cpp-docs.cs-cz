---
title: Třída CHtmlEditDoc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de452365a02b69798c62e2eecfd8051afcf08bb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366968"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc – třída
S [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), poskytuje funkci platformou WebBrowser úpravy v kontextu architektury MFC zobrazení dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AFX_NOVTABLE CHtmlEditDoc : public CDocument  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|Vytvoří `CHtmlEditDoc` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CHtmlEditDoc::GetView](#getview)|Načte `CHtmlEditView` objekt připojený k tomuto dokumentu.|  
|[CHtmlEditDoc::IsModified](#ismodified)|Vrátí, zda přidružené zobrazení WebBrowser – ovládací prvek obsahuje dokumentu, která byla změněna uživatelem.|  
|[CHtmlEditDoc::OpenURL](#openurl)|Otevře adresu URL.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `CHtmlEditDoc`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxhtml.h  
  
##  <a name="chtmleditdoc"></a>  CHtmlEditDoc::CHtmlEditDoc  
 Vytvoří **CHtmlEditDoc** objektu.  
  
```  
CHtmlEditDoc();
```  
  
##  <a name="getview"></a>  CHtmlEditDoc::GetView  
 Načte [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) objekt připojený k tomuto dokumentu.  
  
```  
virtual CHtmlEditView* GetView() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel v dokumentu **CHtmlEditView** objektu.  
  
##  <a name="ismodified"></a>  CHtmlEditDoc::IsModified  
 Vrátí, zda přidružené zobrazení WebBrowser – ovládací prvek obsahuje dokumentu, která byla změněna uživatelem.  
  
```  
virtual BOOL IsModified();
```  
  
##  <a name="openurl"></a>  CHtmlEditDoc::OpenURL  
 Otevře adresu URL.  
  
```  
virtual BOOL OpenURL(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszURL`  
 Chcete-li otevřít adresu URL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka HTMLEdit](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)

