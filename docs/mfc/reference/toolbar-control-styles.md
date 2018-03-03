---
title: "Styly ovládacího prvku panel nástrojů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d81be893ce84da24b3a30518219ee1f6fd10057
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="toolbar-control-styles"></a>ToolBar – styly ovládacích prvků
[Třída CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) má sadu styl příznaky, které určují vzhled a chování tlačítka. Můžete nastavit kombinaci tyto příznaky voláním [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). Toto téma obsahuje seznam hodnot příznaku styl a jejich významů.  
  
## <a name="property-values"></a>Hodnoty vlastností  
 Typ tlačítka, která představuje ovládací prvek určete následující hodnoty:  
  
 TBBS_BUTTON  
 Standardní pushbutton (výchozí).  
  
 TBBS_CHECKBOX  
 zaškrtávací políčko.  
  
 TBBS_CHECKGROUP  
 Spuštění skupiny zaškrtávací políčka.  
  
 TBBS_GROUP  
 Začátek skupina tlačítek.  
  
 TBBS_SEPARATOR  
 Oddělovač.  
  
 Následující hodnoty představují aktuální stav ovládacího prvku:  
  
 TBBS_CHECKED  
 Zaškrtávací políčko je zaškrtnuto.  
  
 TBBS_DISABLED  
 Ovládací prvek je zakázaný.  
  
 TBBS_INDETERMINATE  
 Zaškrtávací políčko je v neurčitém stavu.  
  
 TBBS_PRESSED  
 Stisknutí tlačítka.  
  
 Následující hodnotu změní rozložení tlačítka na panelu nástrojů:  
  
 TBBS_BREAK  
 Umístí položka bez oddělení sloupců na nový řádek nebo v novém sloupci.  
  
## <a name="remarks"></a>Poznámky  
 Aktuální styl je uložen v [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). Nenastavujte novou hodnotu `m_nStyle` přímo, protože některé odvozené třídy provést další zpracování při volání `SetStyles`.  
  
 Visual manager určuje vzhled tlačítek v každém stavu. V tématu [správce vizualizace](../../mfc/visualization-manager.md) Další informace.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbarbutton.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)   
 [CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Správce vizualizace](../../mfc/visualization-manager.md)


