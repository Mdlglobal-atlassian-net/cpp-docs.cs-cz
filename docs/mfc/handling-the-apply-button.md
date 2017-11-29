---
title: "Ošetření tlačítka použít | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 67520106ed505e04c6b12967c2f45509de700a06
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="handling-the-apply-button"></a>Ošetření tlačítka Použít
Seznam vlastností mají funkci, která standardní dialogová okna nepodporují: umožňují uživatelům použít změny byly provedeny před jeho zavřením seznamu vlastností. To se provádí pomocí tlačítka použít. Tento článek popisuje metody, které můžete použít tuto funkci implementovat správně.  
  
 Modální dialogová okna obvykle použít nastavení u externího objektu, když uživatel klikne na tlačítko OK zavřete dialogové okno. Totéž platí pro seznam vlastností: když uživatel klikne na tlačítko OK, nové nastavení v seznamu vlastností projeví.  
  
 Můžete však uživateli umožňují uložit nastavení bez nutnosti zavřete dialogové okno List vlastností. Toto je funkce na tlačítko použít. Tlačítko použít aktuální nastavení ve všech stránek vlastností platí pro externí objekt, na rozdíl od použití pouze aktuální nastavení stránce momentálně aktivní.  
  
 Ve výchozím nastavení je vždy zakázáno na tlačítko použít. Musíte napsat kód, aby na tlačítko použít v příslušnou dobu a musíte napsat kód pro implementaci účinku použít, jak je popsáno níže.  
  
 Pokud nechcete, aby uživatel nabízet funkci použít, není nutné použít tlačítko Odebrat. Můžete nechat zakázané, protože bude běžné mezi aplikacemi, které používají standardní vlastnost list podpory k dispozici v budoucích verzích systému Windows.  
  
 Pokud chcete ohlásit jako upravené stránky a povolit na tlačítko použít, volání **CPropertyPage::SetModified (TRUE)**. Pokud existuje stránky sestavy upravována, zůstane zapnutá, bez ohledu na to, jestli aktuálně aktivní stránka byla změněna na tlačítko použít.  
  
 By měly volat [CPropertyPage::SetModified](../mfc/reference/cpropertypage-class.md#setmodified) vždy, když uživatel změní nastavení na stránce. K implementaci obslužné rutiny oznamovacích změn pro každý ovládací prvky na stránce vlastností, jako je možné rozpoznat, kdy se uživatel změní nastavení na stránce **EN_CHANGE** nebo **BN_CLICKED**.  
  
 Pokud chcete implementovat účinku na tlačítko použít, seznamu vlastností řekněte jeho vlastníka nebo jiné externí objekt v aplikaci, aby mohl použít aktuální nastavení na stránkách vlastností. Seznam vlastností ve stejnou dobu, měli zakázat tlačítka použít voláním **CPropertyPage::SetModified (FALSE)** pro všechny stránky, které použije jejich změny externího objektu.  
  
 Příklad tohoto procesu naleznete v části Obecné MFC ukázka [PROPDLG](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Seznam vlastností](../mfc/property-sheets-mfc.md)
