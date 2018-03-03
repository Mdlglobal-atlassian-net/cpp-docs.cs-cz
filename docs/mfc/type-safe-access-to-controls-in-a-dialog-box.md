---
title: "Typově bezpečný přístup k ovládacím prvkům v dialogovém okně | Microsoft Docs"
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
- common controls [MFC], in dialog boxes
- Windows common controls [MFC], in dialog boxes
- safe access to dialog box controls
- dialog boxes [MFC], type-safe access to controls
- controls [MFC], accessing in dialog boxes
- type-safe access to dialog box controls
- MFC dialog boxes [MFC], type-safe access to controls
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b6005f34b28a634b36aad93186a34a8806b8033d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>Typově bezpečný přístup k ovládacím prvkům v dialogovém okně
Ovládací prvky v dialogovém okně můžete použít rozhraní MFC – třídy ovládacích prvků jako `CListBox` a `CEdit`. Můžete vytvořit objekt ovládacího prvku a připojit ho k ovládacímu prvku dialogového okna. K tomuto ovládacímu prvku pak získáte přístup prostřednictvím rozhraní jeho třídy voláním členských funkcí ovládajících tento ovládací prvek. Zde popsané metody poskytují přístup k ovládacímu prvku se zajištěním bezpečnosti typů. To je zvláště užitečné pro ovládací prvky, jako jsou textová pole a pole se seznamem.  
  
 Existují dva přístupy k navazování připojení mezi ovládacího prvku v dialogovém okně a členské proměnné ovládacích C++ v `CDialog`-odvozené třídy:  
  
-   [Bez průvodců kódem](../mfc/type-safe-access-to-controls-without-code-wizards.md)  
  
-   [S použitím průvodců kódem](../mfc/type-safe-access-to-controls-with-code-wizards.md)  
  
## <a name="see-also"></a>Viz také  
 [Dialogová okna](../mfc/dialog-boxes.md)

