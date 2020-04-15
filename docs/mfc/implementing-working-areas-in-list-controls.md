---
title: Implementace pracovních oblastí v ovládacích prvcích seznam
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: 91577203163247bd230fecb083cf1c50e2875b98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377215"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementace pracovních oblastí v ovládacích prvcích seznam

Ve výchozím nastavení ovládací prvek seznamu uspořádá všechny položky standardním způsobem mřížky. Je však podporována jiná metoda, pracovní oblasti, která uspořádá položky seznamu do obdélníkových skupin. Obrázek ovládacího prvku seznamu, který implementuje pracovní oblasti, naleznete v tématu Použití ovládacích prvků zobrazení seznamu v sadě Windows SDK.

> [!NOTE]
> Pracovní oblasti jsou viditelné pouze v případě, že je ovládací prvek seznamu v režimu ikony nebo malého režimu ikon. Všechny aktuální pracovní oblasti jsou však zachovány, pokud je zobrazení přepnuto do režimu sestavy nebo seznamu.

Pracovní prostory lze použít k zobrazení prázdného ohraničení (vlevo, nahoře a/nebo vpravo od položek) nebo k zobrazení vodorovného posuvníku, když by normálně žádný nebyl. Dalším běžným použitím je vytvoření více pracovních oblastí, do kterých lze položky přesunout nebo vynechat. Pomocí této metody můžete vytvořit oblasti v jednom zobrazení, které mají různé významy. Uživatel pak může položky kategorizovat tak, že je umístí do jiné oblasti. Příkladem může být zobrazení systému souborů, který má oblast pro čtení a zápis souborů a další oblast pro soubory jen pro čtení. Pokud byla položka souboru přesunuta do oblasti jen pro čtení, automaticky by se stala jen pro čtení. Přesunutím souboru z oblasti jen pro čtení do oblasti pro čtení a zápis by soubor čtení a zápisu.

`CListCtrl`poskytuje několik členských funkcí pro vytváření a správu pracovních oblastí v ovládacím prvku seznamu. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) a [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) načítají `CRect` a nastavují pole objektů (nebo `RECT` struktur), které ukládají aktuálně implementované pracovní oblasti pro ovládací prvek seznamu. Kromě toho [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) načte aktuální počet pracovních oblastí pro ovládací prvek seznamu (ve výchozím nastavení nula).

## <a name="items-and-working-areas"></a>Položky a pracovní oblasti

Při vytvoření pracovní oblasti se její milivné stanou položky, které leží v pracovní oblasti. Podobně, pokud je položka přesunuta do pracovní oblasti, stane se členem pracovní oblasti, do které byla přesunuta. Pokud položka neleží v žádné pracovní oblasti, automaticky se stane členem první pracovní oblasti (index 0). Pokud chcete vytvořit položku a nechat ji umístit do určité pracovní oblasti, budete muset vytvořit položku a potom ji přesunout do požadované pracovní oblasti s voláním [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). Druhý příklad níže ukazuje tuto techniku.

Následující příklad implementuje čtyři`rcWorkAreas`pracovní oblasti ( ), stejné velikosti s ohraničením o šířce 10 pixelů kolem každé pracovní oblasti v ovládacím prvku seznamu (`m_WorkAreaListCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

Volání [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) byla provedena získat odhad celkové oblasti potřebné k zobrazení všech položek v jedné oblasti. Tento odhad je pak rozdělen do čtyř oblastí a doplněn o ohraničení o šířce 5 pixelů.

Další příklad přiřadí existující položky seznamu`rcWorkAreas`každé skupině ( )`m_WorkAreaListCtrl`a aktualizuje zobrazení ovládacího prvku ( ) k dokončení efektu.

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Viz také

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
