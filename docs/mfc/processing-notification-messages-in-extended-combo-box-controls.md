---
title: Zpracování zpráv s oznámením v rozšířené pole se seznamem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1e71502f818321dc8893f89f21993c25b032602
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346773"
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

