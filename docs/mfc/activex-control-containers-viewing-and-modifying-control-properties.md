---
title: "Kontejnery ovládacích prvků ActiveX: Zobrazení a úprava vlastností ovládacího prvku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5e3a12f9d591cb94c8c16e7b9f22a4db0872e78f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>ActiveX – kontejnery ovládacích prvků: Zobrazení a úpravy vlastností ovládacích prvků
Při vložení ovládacího prvku ActiveX do projektu, je užitečné k zobrazení a změna vlastností nepodporuje ovládací prvek ActiveX. Tento článek popisuje, jak to udělat pomocí editoru prostředků Visual C++.  
  
 Pokud vaše aplikace kontejneru ovládacího prvku ActiveX používá vložený ovládací prvky, můžete zobrazit a upravit vlastnosti ovládacího prvku v editoru prostředků. Editor prostředků můžete taky nastavit hodnoty vlastností v době návrhu. Editor prostředků pak automaticky uloží tyto hodnoty do souboru prostředků projektu. Jakékoli instanci ovládacího prvku pak bude mít jeho vlastnosti inicializována tak, aby tyto hodnoty.  
  
 Tento postup předpokládá, že jste vložili ovládacího prvku do projektu. Informace najdete v tématu [ActiveX – kontejnery ovládacích prvků: vložení ovládacího prvku do aplikace ovládacího prvku kontejner](../mfc/inserting-a-control-into-a-control-container-application.md).  
  
 Prvním krokem při prohlížení vlastností ovládacího prvku je přidání instance ovládacího prvku do projektu šablony dialogového okna.  
  
### <a name="to-view-the-properties-of-a-control"></a>Zobrazení vlastností ovládacího prvku  
  
1.  V zobrazení prostředků, otevřete **dialogové okno** složky.  
  
2.  Otevřete šablonu pole hlavním dialogu.  
  
3.  Vložit ovládací prvek ActiveX pomocí **vložit ovládací prvek ActiveX** dialogové okno. Další informace najdete v tématu [zobrazení a přidání ovládacích prvků ActiveX do dialogového okna](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
4.  V dialogovém okně vyberte ovládací prvek ActiveX.  
  
5.  V okně vlastností klikněte na **vlastnosti** tlačítko.  
  
 Použití **vlastnosti** dialogovém okně Upravit a testování nových vlastností okamžitě.  
  
## <a name="see-also"></a>Viz také  
 [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

