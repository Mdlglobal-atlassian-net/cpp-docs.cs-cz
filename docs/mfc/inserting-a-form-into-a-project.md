---
title: Vložení formuláře do projektu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e62618301e09ad4c44fb91608976ecab972a59da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344130"
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

