---
title: "Zpracování zpráv s oznámením v rozšířené pole se seznamem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a78e7b9fd8f9c67f14a4bb51088866785d372cca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Zpracování zpráv s oznámením v ovládacích prvcích rozšířeného pole se seznamem
Jak uživatelé pracují s pole rozšířeného pole se seznamem ovládacího prvku (`CComboBoxEx`) odešle zprávy s oznámením do nadřazeného okna, obvykle objekt zobrazení nebo dialogové okno. Tyto zprávy zpracování, pokud chcete, aby dělala něco v odpovědi. Například pokud uživatel aktivuje rozevíracím seznamu nebo kliknutí v ovládacím prvku textového pole, **CBEN_BEGINEDIT** odeslání oznámení.  
  
 Okno Vlastnosti použijte pro přidání obslužné rutiny oznamovacích do nadřazené třídy pro ty zprávy, které chcete implementovat.  
  
 Následující seznam popisuje různé oznámení zaslaná z ovládacího prvku rozšířené pole se seznamem pole.  
  
-   **CBEN_BEGINEDIT** odeslat v případě, že uživatel aktivuje rozevíracím seznamu nebo kliknutí v ovládacím prvku textového pole.  
  
-   **CBEN_DELETEITEM** odeslat v případě, že položka byla odstraněna.  
  
-   **CBEN_DRAGBEGIN** odeslány v případě, že uživatel zahájí přetahování bitové kopie položku zobrazenou v části ovládací prvek pro úpravy.  
  
-   **CBEN_ENDEDIT** odeslat v případě, že uživatel uzavřelo operace v rámci pole pro úpravy nebo má vybrané položky z ovládacího prvku rozevíracího seznamu.  
  
-   **CBEN_GETDISPINFO** posílá načtení zobrazení informací o položka zpětného volání.  
  
-   **CBEN_INSERTITEM** odeslat v případě, že byla vložena nové položky v ovládacím prvku.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

