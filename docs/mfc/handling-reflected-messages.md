---
title: Zpracování Reflektovaných zpráv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05b5f62169d2b65010ec75ab8c8b5c30959b77b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="handling-reflected-messages"></a>Zpracování reflektovaných zpráv
Zpráva reflexe umožňuje zpracovat zprávy pro ovládací prvek, jako například `WM_CTLCOLOR`, **wm_command –**, a **wm_notify –**, v samotném ovládacím prvku. Díky řízení více samostatné a přenosné. Tento mechanismus funguje s běžné ovládací prvky Windows, a také s ovládacími prvky ActiveX (dříve se označovaly jako ovládací prvky OLE).  
  
 Zpráva reflexe můžete znovu použít vaše `CWnd`-snadněji odvozených třídách. Zpráva reflexe funguje prostřednictvím [CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify), pomocí speciální **ON_XXX_REFLECT** zprávy položek mapování: například **ON_CTLCOLOR_REFLECT** a **On_control_reflect –**. [Technická poznámka 62](../mfc/tn062-message-reflection-for-windows-controls.md) vysvětluje reflexe zpráv podrobněji.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat  
  
-   [Další informace o reflexe zpráv](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [Implementace reflexe zprávy pro běžného ovládacího prvku](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [Implementace reflexe zprávy pro ovládací prvek ActiveX](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)  
  
## <a name="see-also"></a>Viz také  
 [Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
