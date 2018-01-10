---
title: "Třída CMFCDisableMenuAnimation | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
dev_langs: C++
helpviewer_keywords: CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 458a35e708db41ee393da70aedd653aca44cf802
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation – třída
Zakáže animace místní nabídky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDisableMenuAnimation  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Vytvoří `CMFCDisableMenuAnimation` objektu.|  
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCDisableMenuAnimation::Restore](#restore)|Obnoví předchozí animace, který používá rozhraní k zobrazení místní nabídky.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|Název|Popis|  
|`CMFCDisableMenuAnimation::m_animType`|Ukládá předchozí typ animace místní nabídky.|  
  
### <a name="remarks"></a>Poznámky  
 Tato pomocná třída použijte k dočasnému zakázání animace místní nabídky (například když při zpracování příkazů myši a klávesnice).  
  
 A `CMFCDisableMenuAnimation` objekt zakáže animace místní nabídky během celé jeho životnosti. Uloží aktuální typ animace místní nabídky v konstruktoru `m_animType` pole a nastaví aktuální animace typ, který má `CMFCPopupMenu::NO_ANIMATION`. Destruktoru obnoví předchozí typ animace.  
  
 Můžete vytvořit `CMFCDisableMenuAnimation` objektu v zásobníku zakázat animace místní nabídky v rámci jedné funkce. Pokud chcete zakázat místní nabídky animace mezi funkce, vytvořte `CMFCDisableMenuAnimation` objektu v haldě a odstraňte ji. Pokud chcete obnovit animace místní nabídky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití zásobníku k dočasnému zakázání nabídky animace.  
  
 [!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpopupmenu.h  
  
##  <a name="restore"></a>CMFCDisableMenuAnimation::Restore  
 Obnoví předchozí animace, který používá rozhraní k zobrazení místní nabídky.  
  
```  
void Restore ();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `CMFCDisableMenuAnimation` destruktor obnovit předchozí animace, který používá rozhraní k zobrazení místní nabídky.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu – třída](../../mfc/reference/cmfcpopupmenu-class.md)
