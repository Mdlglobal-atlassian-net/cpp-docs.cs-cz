---
title: "COM – vstupní body rozhraní | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4d551c3875a2c8aca235437579db2f467f680380
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="com-interface-entry-points"></a>COM – vstupní body rozhraní
Členské funkce rozhraní modelu COM, použijte [method_prologue –](com-interface-entry-points.md#method_prologue) makro zachování správné globální stav při volání metody exportovaný rozhraní.  
  
 Obvykle členské funkce rozhraní implementované `CCmdTarget`-odvozené objekty již použití tohoto makra zajistit automatické inicializace `pThis` ukazatel. Příklad:  
  
 [!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]  
  
 Další informace najdete v tématu [Technická poznámka 38](../mfc/tn038-mfc-ole-iunknown-implementation.md) na MFC/OLE **IUnknown** implementace.  
  
 `METHOD_PROLOGUE` Makro je definován jako:  
  
 `#define METHOD_PROLOGUE(theClass, localClass) \`  
  
 `theClass* pThis = \`  
  
 `((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \`  
  
 `AFX_MANAGE_STATE(pThis->m_pModuleState) \`  
  
 Část makra, která se týkají správy globální stav je:  
  
 `AFX_MANAGE_STATE( pThis->m_pModuleState )`  
  
 V tomto výrazu *m_pModuleState* se považuje za členské proměnné obsahující objektu. Je implementované `CCmdTarget` základní třídy a je inicializován na odpovídající hodnotu podle `COleObjectFactory`, při vytváření instance objektu.  
  
## <a name="see-also"></a>Viz také  
 [Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

