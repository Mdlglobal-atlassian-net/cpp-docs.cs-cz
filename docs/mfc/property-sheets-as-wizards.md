---
title: Seznamy vlastností jako průvodci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73b6b0462012fc54b3bd6f2cb22422f5b1431288
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374207"
---
# <a name="property-sheets-as-wizards"></a>Seznamy vlastností jako průvodci

Klíčovou charakteristikou Průvodce vlastností je, že je součástí navigační tlačítka Další nebo dokončit zpět a zrušení namísto tabulátorů. Je třeba volat [CPropertySheet::SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode) před voláním [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) na objekt seznamu vlastností, abyste mohli využít tuto funkci.

Uživatel obdrží stejné [CPropertyPage::OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) a [CPropertyPage::OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) oznámení při přesunu z jedné stránky na jiné stránce. Dokončení tlačítka a další jsou vzájemně se vylučující ovládací prvky; To znamená pouze jeden z nich se zobrazí v čase. Na stránce první musí být povolené na tlačítko Další. Pokud je uživatel na poslední stránce, musí být povolené na tlačítko Dokončit. Tato podmínka není splněna automaticky v rámci rozhraní. Je nutné volat [CPropertySheet::SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) na poslední stránkou k dosažení tohoto cíle.

Zobrazit všechny výchozí tlačítek, je třeba zobrazit tlačítko pro dokončení a přesunout na tlačítko Další. Přesuňte tlačítko zpět tak, aby se udržuje jeho relativní pozice na tlačítko Další.

## <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]

## <a name="see-also"></a>Viz také

[Seznamy vlastností](../mfc/property-sheets-mfc.md)

