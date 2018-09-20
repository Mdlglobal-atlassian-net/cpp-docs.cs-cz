---
title: Implementace pracovních oblastí v ovládacích prvcích seznam | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc245ef87343d9f33277e41c5c191ea713e21da0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383412"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementace pracovních oblastí v ovládacích prvcích seznam

Ve výchozím nastavení uspořádá ovládací prvek seznamu všechny položky v podobě standardní mřížky. Ale je podporované jinou metodou, pracovních oblastí, které uspořádá položky seznamu do obdélníkové skupin. Pro obrázek ovládacího prvku seznam, který implementuje pracovních prostorech naleznete v tématu pomocí zobrazení seznamu ovládacích prvků v sadě Windows SDK.

> [!NOTE]
>  Pracovní prostory jsou viditelné pouze v případě, že ovládací prvek seznamu je v režimu ikonu nebo ikonu. Všechny aktuální pracovní oblasti se ale zachovají, pokud zobrazení je přepnout do režimu sestavy nebo seznamu.

Pracovní prostory slouží k zobrazení prázdný ohraničení (na levé straně, nahoru a napravo od položky), nebo způsobit vodorovný posuvník, který se má zobrazit při obvykle by existovat jeden. Další běžné použití je vytvoření několika pracovních prostorech, ke kterým položky přesunut nebo vyřadit. Pomocí této metody můžete vytvořit oblasti v rámci jednoho zobrazení, které mají různý význam. Uživatel pak může kategorizaci položky tak, že je v jiné oblasti. Příklad tohoto by zobrazení systému souborů, který má oblasti pro čtení a zápis souborů a jiné oblasti pro soubory jen pro čtení. Pokud soubor položky byly přesunuty do oblasti jen pro čtení, by automaticky budou jen pro čtení. Přesun souboru z oblasti jen pro čtení v oblasti čtení a zápisu s žádným soubor pro čtení a zápisu.

`CListCtrl` poskytuje několik členské funkce pro vytváření a správu pracovních prostorech v ovládacím prvku seznamu. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) a [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) načíst a nastavit pole `CRect` objekty (nebo `RECT` struktury), který uložit aktuální implementace pracovní oblasti pro ovládací prvek seznamu. Kromě toho [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) načte aktuální počet pracovních prostorech ovládacího prvku seznam (ve výchozím nastavení, nula).

## <a name="items-and-working-areas"></a>Položky a pracovních oblastí

Po vytvoření pracovní oblasti položky, které se nacházejí v pracovní oblasti stanou členy jeho. Podobně pokud položka se přesune do pracovní oblasti, stane se členem pracovní oblast, do které byl přesunut. Pokud položka neleží v všechny pracovní plochy, automaticky stane členem první pracovní oblasti (index 0). Pokud chcete vytvořit položku a jeho umístěné v konkrétní pracovní oblasti, budete muset vytvořit položku a poté ho přesuňte do požadované pracovní oblast pomocí volání [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). Druhý příklad ukazuje tento postup.

Následující příklad implementuje čtyři pracovní oblasti (`rcWorkAreas`), stejnou velikost s 10 pixel celého ohraničení kolem každé pracovní oblasti v ovládacím prvku seznam (`m_WorkAreaListCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

Volání [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) byl proveden k výpočtu odhadu oblasti celková vyžaduje k zobrazení všech položek v jedné oblasti. Tento odhad je poté rozdělen do čtyř oblastí a vyplní 5 pixelů celého ohraničení.

Následující příklad přiřadí existující položky seznamu pro každou skupinu (`rcWorkAreas`) a aktualizuje zobrazení ovládacího prvku (`m_WorkAreaListCtrl`) k dokončení efekt.

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Viz také

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

