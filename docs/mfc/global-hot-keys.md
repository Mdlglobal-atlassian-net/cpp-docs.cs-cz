---
title: "Globální klávesové zkratky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 48f3e2a1e0c1461180291342a8cd18682173e8bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="global-hot-keys"></a>Globální klávesové zkratky
Globální klávesové zkratky je přidružen konkrétní nonchild období. Umožňuje uživatelům aktivovat v okně libovolná součást systému. Aplikace nastaví globální klávesové zkratky pro konkrétní okno odesláním [WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) zpráva, která má toto okno. Například pokud `m_HotKeyCtrl` je [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) objektu a `pMainWnd` ukazatel do okna aktivovaná, při stisknutí klávesové zkratky, můžete použít následující kód k přidružení aktivní klíč zadaný v ovládacím prvku s okno na kterou odkazuje `pMainWnd`.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]  
  
 Vždy, když uživatel stiskne Globální klávesové zkratky, obdrží určeno okno [WM_SYSCOMMAND](http://msdn.microsoft.com/library/windows/desktop/ms646360) zprávu, která určuje **SC_HOTKEY** jako typ příkazu. Tato zpráva taky aktivuje okně, které ji přijme. Protože zpráva neobsahuje žádné informace o přesný klávesy, která byla stisknuta, pomocí této metody není povoleno rozlišování mezi různé klávesové zkratky, které může být připojené k okně. Klávesové zkratky zůstává platná do aplikace, která odeslala **WM_SETHOTKEY** ukončí.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

