---
title: Vložení formuláře do projektu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 968c24a4f64b88be6de95f0f1dd98c09eb494a97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="inserting-a-form-into-a-project"></a>Vložení formuláře do projektu
Formuláře poskytují pohodlný kontejner pro ovládací prvky. Formulář na základě MFC lze snadno vložit do aplikace podporuje aplikace knihovny MFC.  
  
### <a name="to-insert-a-form-into-your-project"></a>Vložení formuláře do projektu  
  
1.  V zobrazení tříd vyberte projekt, do které chcete přidat formuláři a klikněte pravým tlačítkem myši.  
  
2.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat třídu**.  
  
     Pokud **nového formuláře** příkaz není k dispozici, projekt může být založeno na aktivní knihovny šablony (ATL). Chcete-li přidat formuláře do projektu knihovny ATL, je potřeba [zadat určitá nastavení](../atl/reference/application-settings-atl-project-wizard.md) při prvním vytvoření projektu.  
  
3.  Z **MFC** složku, klikněte na tlačítko **třídy knihovny MFC**.  
  
4.  Pomocí Průvodce třídou MFC, ujistěte se, nová třída odvozena od [CFormView](../mfc/reference/cformview-class.md).  
  
 Visual C++ přidá formuláře k vaší aplikaci, otevřete v editoru dialogových oken tak, abyste ji mohli začít přidání ovládacích prvků a práci na celkové struktury.  
  
 Můžete chtít provést následující kroky (neplatí pro aplikace založené na dialogové okno):  
  
1.  Přepsání `OnUpdate` – členská funkce.  
  
2.  Implementujte členské funkce pro přesun dat ze zobrazení do dokumentu.  
  
3.  Vytvoření `OnPrint` – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení formulářů](../mfc/form-views-mfc.md)

