---
title: "Načítání dat z objektu dialogového okna | Microsoft Docs"
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
- dialog boxes [MFC], retrieving user data
- dialog box data [MFC]
- data [MFC], retrieving
- GetDlgItemText method [MFC]
- SetDlgItemText method [MFC]
- SetWindowText method [MFC]
- dialog box data [MFC], retrieving
- retrieving data [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- dialog box controls [MFC], initializing values
- DDX (dialog data exchange) [MFC]
- MFC dialog boxes [MFC], retrieving user input
- data retrieval [MFC], dialog boxes
- data [MFC], dialog boxes
- DDX (dialog data exchange) [MFC], about DDX
- DDX (dialog data exchange) [MFC], retrieving data from Dialog object
- GetWindowText method [MFC]
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4b50ae3036a6f262312c7a05c2de093a977a588
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="retrieving-data-from-the-dialog-object"></a>Načítání dat z objektu dialogového okna
Rozhraní framework poskytuje snadný způsob k chybě při inicializaci hodnoty ovládacích prvků v dialogovém okně a k načtení hodnoty z ovládacích prvků. Více pracné ruční přístup je pro volání funkce, jako `SetDlgItemText` a `GetDlgItemText` členské funkce třídy `CWnd`, která se vztahují na ovládací prvek windows. S tyto funkce, můžete každý řízení přístupu jednotlivě, abyste nastavit nebo získat svou hodnotu, jako například volání funkcí `SetWindowText` a `GetWindowText`. Rozhraní framework přístup automatizuje inicializace a načítání.  
  
 Výměna dat dialogových oken (DDX) umožňuje snadno výměnu dat mezi ovládacími prvky v dialogovém okně proměnné pole a člena v objektu dialogového okna. Toto exchange funguje obou směrech. K chybě při inicializaci ovládacích prvků v dialogovém okně, můžete nastavit hodnoty datových členů v objektu dialogového okna a rozhraní bude hodnoty přenosu ovládacích prvků, než se zobrazí dialogové okno. Potom můžete kdykoli aktualizovat datové členy dialogové okno s data zadaná uživatelem. V tomto okamžiku můžete data tím, že odkazuje na členské proměnné data.  
  
 Můžete také uspořádat pro hodnoty ovládací prvky dialogového okna má být automaticky ověřen pomocí ověřování dat dialogového okna (DDV).  
  
 DDX a DDV jsou vysvětleny v další části [výměna dialogových dat a ověření](../mfc/dialog-data-exchange-and-validation.md).  
  
 Pro modální dialogové okno, můžete načíst žádná data uživatele zadané při `DoModal` vrátí **IDOK** , ale před dialogu objekt zničena. Pro nemodální dialogové okno, můžete data načíst z objektu dialogového okna kdykoli voláním `UpdateData` s argumentem **TRUE** a poté přístup k dialogu třídy členské proměnné. Toto téma je podrobněji popsána v [výměna dialogových dat a ověření](../mfc/dialog-data-exchange-and-validation.md).  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

