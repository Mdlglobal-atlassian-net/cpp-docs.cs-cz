---
title: "Seznamy vlastností jako průvodci | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 65aedc5dbeb8a740d5713983f66eefe693864937
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="property-sheets-as-wizards"></a>Seznamy vlastností jako průvodci
Klíčové vlastnosti vlastností Průvodce je, že navigace je k dispozici další nebo dokončit zpět a zrušit tlačítka místo karty. Je třeba volat [CPropertySheet::SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode) před voláním [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) na objektu List vlastnosti využít této funkce.  
  
 Uživatel obdrží stejné [CPropertyPage::OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) a [CPropertyPage::OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) oznámení při přesouvání z jedné stránky na jinou stránku. Tlačítka Dokončit a další se vzájemně vylučují ovládací prvky; To znamená pouze jedna z nich se zobrazí v čase. Na první stránce by měly být povoleny na tlačítko Další. Pokud je uživatel na poslední stránce, by měly být povoleny na tlačítko Dokončit. Není to automaticky pomocí rozhraní. Budete muset volat [CPropertySheet::SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) na poslední stránce dosáhnout.  
  
 Pro zobrazení všech výchozích tlačítek, je třeba zobrazit na tlačítko Dokončit a přesunout na tlačítko Další. Pak přesuňte na tlačítko zpět tak, aby se udržuje jeho relativní pozici, na tlačítko Další.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Seznam vlastností](../mfc/property-sheets-mfc.md)

