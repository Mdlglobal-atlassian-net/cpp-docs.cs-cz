---
title: "Přidání dialogové okno knihovny ATL | Microsoft Docs"
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
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d8c9969f4747c6c3fa2a39b7b0452f6ac54c9d58
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-atl-dialog-box"></a>Přidání dialogové okno knihovny ATL
Pokud chcete přidat dialogového okna knihovny ATL do projektu, musí být projektu projektu knihovny ATL nebo projektu knihovny MFC, která zahrnuje podporu ATL. Můžete použít [ATL – Průvodce projektem](../../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt knihovny ATL do aplikace knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) implementovat ATL – podpora pro aplikace MFC.  
  
 Ve výchozím nastavení, dialogové okno průvodce ATL implementuje dialogové okno odvozené z [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Tato třída zahrnuje podporu pro hostování ovládacích prvků ActiveX a systému Windows. Pokud nechcete, aby nároky na podporu ovládací prvek ActiveX, jakmile v Průvodci vygenerovala kódu, nahraďte všechny výskyty `CAxDialogImpl` s buď [CSimpleDialog](../../atl/reference/csimpledialog-class.md) nebo [CDialogImpl](../../atl/reference/cdialogimpl-class.md) jako základní třída .  
  
> [!NOTE]
>  `CSimpleDialog`vytvoří pouze modální dialogová okna, které podporují pouze běžné ovládací prvky Windows. `CDialogImpl`Vytvoří modální a nemodální dialogová okna.  
  
### <a name="to-add-an-atl-dialog-resource-to-your-project"></a>Chcete-li přidat dialogu knihovny ATL do projektu  
  
1.  Vytvoření projektu knihovny ATL pomocí [ATL – Průvodce projektem](../../atl/reference/atl-project-wizard.md).  
  
2.  Z [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), klikněte pravým tlačítkem na název projektu a klikněte na **přidat** z místní nabídky. Klikněte na tlačítko **přidejte třídu**.  
  
3.  V podokně šablon [přidat třídu](../../ide/add-class-dialog-box.md) dialogové okno, klikněte na tlačítko **ATL Dialog**. Klikněte na tlačítko **otevřete** zobrazíte [ATL dialogové okno průvodce](../../atl/reference/atl-dialog-wizard.md).  
  
 Další informace najdete v tématu [implementace dialogové okno](../../atl/implementing-a-dialog-box.md).  
  
## <a name="see-also"></a>Viz také  
 [Přidání třídy](../../ide/adding-a-class-visual-cpp.md)   
 [Třídy oken](../../atl/atl-window-classes.md)   
 [Mapy zpráv](../../atl/message-maps-atl.md)

