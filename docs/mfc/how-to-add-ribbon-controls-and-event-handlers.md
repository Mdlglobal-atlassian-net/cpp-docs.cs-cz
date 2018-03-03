---
title: "Postupy: Přidání ovládacích prvků pásu karet a obslužných rutin událostí | Microsoft Docs"
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
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f5d5015fdf5fd2a97b6b8a9b9ee9cf5ccc755ce5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Postupy: Přidání ovládacích prvků pásu karet a obslužných rutin událostí
Prvky, jako jsou tlačítka a pole se seznamem, které přidáte do panelů jsou ovládacích prvků pásu karet. Panely jsou oblasti panelu pásu karet, které zobrazují skupinu související ovládací prvky.  
  
 V tomto tématu otevřete návrháře pásu karet, tlačítko Přidat a pak propojit událost, která zobrazuje "Hello World".  
  
### <a name="to-open-the-ribbon-designer"></a>Chcete-li otevřít Návrhář pásu karet  
  
1.  V sadě Visual Studio na **zobrazení** nabídky, klikněte na tlačítko **zobrazení prostředků**.  
  
2.  V **zobrazení prostředků**, dvakrát klikněte na prostředek pásu karet, která se zobrazí na návrhovou plochu.  
  
### <a name="to-add-a-button-and-an-event-handler"></a>Přidání tlačítka a obslužné rutiny událostí  
  
1.  Z **nástrojů**, klikněte na tlačítko **tlačítko** a přetáhněte ji na panelu v návrhovou plochu.  
  
2.  Klikněte pravým tlačítkem na tlačítko a klikněte na tlačítko **přidejte obslužné rutiny události**.  
  
3.  V **Průvodce obslužnou rutinou události**, potvrďte výchozí nastavení a klikněte na **přidávat a upravovat**. Další informace najdete v tématu [Průvodce obslužnou rutinou události](../ide/event-handler-wizard.md).  
  
4.  V editoru kódu přidejte následující kód do obslužné rutiny:  
  
 ```  
    MessageBox((LPCTSTR)L"Hello World");

 ```  
  
## <a name="see-also"></a>Viz také  
 [RibbonGadgets ukázka: Jednoduché aplikace pásu karet miniaplikacemi](../visual-cpp-samples.md)   
 [Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)

