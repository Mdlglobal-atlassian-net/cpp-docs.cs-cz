---
title: "Vytvoření nemodálního seznamu vlastností | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4686caf6c414952cd86dfe0c69fcc3be8ee09af9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-modeless-property-sheet"></a>Vytvoření nemodálního seznamu vlastností
Seznamy vlastností, které vytvoříte za normálních okolností bude modální. Pokud používáte modální vlastností, musí uživatel zavřete okno vlastností před použitím jiných součástí aplikace. Tento článek popisuje metody, které můžete použít k vytvoření nemodálního seznamu vlastností umožňující uživateli nechat otevřené okno vlastností při používání dalších částí aplikace.  
  
 Pro zobrazení vlastností jako pole dialogového okna bez režimu místo jako modální dialogové okno, volejte [CPropertySheet::Create](../mfc/reference/cpropertysheet-class.md#create) místo [DoModal](../mfc/reference/cpropertysheet-class.md#domodal). Musíte také implementovat některé další úkoly pro podporu nemodálního seznamu vlastností.  
  
 Mezi další úlohy je výměna dat mezi vlastností a externí objekt, který provádí změny v otevřeném seznamu vlastností. Obvykle se jedná o stejnou úlohu jako u standardní nemodální dialogová okna. Součástí této úlohy je implementace kanál komunikace mezi nemodálního seznamu vlastností a externí objekt, na kterou se vztahují nastavení vlastností. Tato implementace je mnohem jednodušší, pokud odvodíte třídu od [cpropertysheet –](../mfc/reference/cpropertysheet-class.md) pro vaše nemodálního seznamu vlastností. Tento článek předpokládá, že provedete.  
  
 Jeden způsob pro komunikaci mezi nemodální vlastností a externí je určit ukazatel ze seznamu vlastností externí objekt objektu (aktuální výběr v zobrazení, např.). Definice funkce (nazývá něco podobného jako `SetMyExternalObject`) v `CPropertySheet`-odvozené třídy změnit ukazatel vždy, když se změní fokus z jednoho externího objektu do jiného. `SetMyExternalObject` Funkce je potřeba obnovit nastavení pro jednotlivé vlastnosti stránky tak, aby odrážela nově vybraný externí objekt. K tomu, `SetMyExternalObject` funkce musí být schopni přistupovat [CPropertyPage](../mfc/reference/cpropertypage-class.md) objekty, které patří k `CPropertySheet` třídy.  
  
 Nejvhodnější způsob, jak poskytnout přístup k vlastnosti stránky v rámci seznamu vlastností je pro vložení `CPropertyPage` objekty v `CPropertySheet`-odvozené objektu. Vložení `CPropertyPage` objekty v `CPropertySheet`-odvozené objektu se liší od typických návrhu pro modálních dialogových oken, kde vytvoří vlastník seznamu vlastností `CPropertyPage` objekty a předává je do seznamu vlastností prostřednictvím [ CPropertySheet::AddPage](../mfc/reference/cpropertysheet-class.md#addpage).  
  
 Existuje mnoho alternativy uživatelského rozhraní pro určení, kdy bude použito nastavení nemodálního seznamu vlastností do externího objektu. Jeden alternativou je aktuální stránka vlastností nastavení vždy, když uživatel změní žádnou hodnotu. Další alternativou je poskytnout tlačítko použít, což umožňuje uživatelům hromadit změny na stránkách vlastností před potvrzením je externí objekt. Informace o způsobech zpracování na tlačítko použít, najdete v článku [ošetření tlačítka použít](../mfc/handling-the-apply-button.md).  
  
## <a name="see-also"></a>Viz také  
 [Seznam vlastností](../mfc/property-sheets-mfc.md)   
 [Výměna dat](../mfc/exchanging-data.md)   
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

