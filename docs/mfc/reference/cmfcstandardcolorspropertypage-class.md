---
title: "Třída CMFCStandardColorsPropertyPage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60deb16628802e61ac411d576558a8659a638410
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcstandardcolorspropertypage-class"></a>CMFCStandardColorsPropertyPage – třída
Představuje stránku vlastností, která uživatelé použít k výběru standardní barvy v dialogovém okně barvy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCStandardColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|Výchozí konstruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|`CMFCStandardColorsPropertyPage::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|`CMFCStandardColorsPropertyPage::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
  
### <a name="remarks"></a>Poznámky  
 `CMFCColorDialog` Třída používá tato třída zobrazíte její stránku vlastností standardní barev. Další informace o `CMFCColorDialog`, najdete v části [CMFCColorDialog třída](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxstandardcolorspropertypage.h  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog – třída](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCCustomColorsPropertyPage – třída](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
