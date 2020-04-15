---
title: Obslužné rutiny pro oblasti map zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- handlers [MFC], message-map ranges
- message maps [MFC], message handler functions
- message maps [MFC], ranges
- control-notification messages [MFC]
- command IDs [MFC], message mapping
- message-map ranges [MFC]
- handlers [MFC]
- message handling [MFC], message handler functions
- mappings [MFC], message ranges
- command handling [MFC], command update handlers
- controls [MFC], notifications
- handler functions [MFC], message-map ranges
- handler functions [MFC]
- command update handlers [MFC]
- command routing [MFC], command update handlers
- message ranges [MFC]
- handler functions [MFC], declaring
- message ranges [MFC], mapping
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
ms.openlocfilehash: fc33df6957beab6e4e8de3093dfc00cf2651780e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370510"
---
# <a name="handlers-for-message-map-ranges"></a>Obslužné rutiny pro oblasti map zpráv

Tento článek vysvětluje, jak mapovat rozsah zpráv na jednu funkci obslužné rutiny zprávy (namísto mapování jedné zprávy pouze na jednu funkci).

Jsou chvíle, kdy je třeba zpracovat více než jednu zprávu nebo ovládací prvek oznámení přesně stejným způsobem. V takových chvílích můžete chtít mapovat všechny zprávy na jednu funkci obslužné rutiny. Rozsahy map zpráv umožňují provést souvislý rozsah zpráv:

- Rozsahy ID příkazů můžete mapovat takto:

  - Funkce obslužné rutiny příkazu.

  - Funkce obslužné rutiny aktualizace příkazu.

- Zprávy s oznámením ovládacího prvku pro rozsah ID ovládacího prvku můžete mapovat na funkci obslužné rutiny zprávy.

Témata uvedená v tomto článku zahrnují:

- [Zápis položky mapy zprávy](#_core_writing_the_message.2d.map_entry)

- [Deklarování funkce obslužné rutiny](#_core_declaring_the_handler_function)

- [Příklad pro rozsah ID příkazů](#_core_example_for_a_range_of_command_ids)

- [Příklad pro rozsah ID ovládacího prvku](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>Zápis položky mapy zpráv

V . CPP, přidejte položku mapy zpráv, jak je znázorněno v následujícím příkladu:

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

Položka mapy zpráv se skládá z následujících položek:

- Makro rozsahu mapy zpráv:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Parametry makra:

  První dvě makra mají tři parametry:

  - ID příkazu, který spustí rozsah

  - ID příkazu, který ukončí rozsah

  - Název funkce obslužné rutiny zprávy

  Rozsah ID příkazů musí být souvislý.

  Třetí makro `ON_CONTROL_RANGE`, přebírá další první parametr: zprávu o oznámení ovládacího prvku, **například EN_CHANGE**.

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>Deklarování funkce obslužné rutiny

Přidejte deklaraci funkce obslužné rutiny v . H soubor. Následující kód ukazuje, jak to může vypadat, jak je znázorněno níže:

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Obslužné rutiny funkce pro jednotlivé příkazy obvykle neberou žádné parametry. S výjimkou funkcí obslužné rutiny aktualizace vyžadují funkce obslužné rutiny pro rozsahy map zpráv další parametr *nID*, typu **UINT**. Tento parametr je prvním parametrem. Parametr extra přizpůsobí další ID příkazu potřebné k určení, který příkaz uživatel skutečně zvolil.

Další informace o požadavcích na parametry pro aktualizaci funkcí obslužné rutiny naleznete [v tématu Příklad rozsahu ID příkazů](#_core_example_for_a_range_of_command_ids).

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>Příklad pro rozsah ID příkazů

Kdy můžete použít rozsahy Jeden příklad je při zpracování příkazů, jako je příkaz Lupa ve vzorku knihovny MFC [HIERSVR](../overview/visual-cpp-samples.md). Tento příkaz přiblíží zobrazení a změní jeho velikost mezi 25 % a 300 % jeho normální velikosti. Hiersvr je zobrazení třídy používá rozsah pro zpracování příkazů Lupa s položkou mapy zprávy připomínající toto:

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Při zápisu položky mapy zpráv zadáte:

- Dvě ID příkazů, začínající a končící souvislý rozsah.

   Zde jsou **ID_VIEW_ZOOM25** a **ID_VIEW_ZOOM300**.

- Název funkce obslužné rutiny pro příkazy.

   Tady je `OnZoom`to .

Deklarace funkce by se podobala takto:

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

Případ funkce obslužné rutiny aktualizace je podobný a pravděpodobně bude více široce užitečné. Je zcela běžné psát `ON_UPDATE_COMMAND_UI` obslužné rutiny pro řadu příkazů a ocitnete se psaní, nebo kopírování, stejný kód znovu a znovu. Řešením je namapovat rozsah ID příkazů na jednu `ON_UPDATE_COMMAND_UI_RANGE` funkci obslužné rutiny aktualizace pomocí makra. ID příkazů musí tvořit souvislý rozsah. Příklad naleznete obslužné rutiny `OnUpdateZoom` a jeho `ON_UPDATE_COMMAND_UI_RANGE` položky mapy zpráv v třídě zobrazení ukázky HIERSVR.

Aktualizace obslužné rutiny funkce pro jednotlivé příkazy obvykle `CCmdUI*`trvat jeden parametr, *pCmdUI*, typu . Na rozdíl od funkcí obslužné rutiny, funkce obslužné rutiny aktualizace pro rozsahy map zpráv nevyžadují další parametr *nID*, typu **UINT**. ID příkazu, který je potřeba určit, který příkaz uživatel `CCmdUI` skutečně zvolil, se nachází v objektu.

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>Příklad pro rozsah ID ovládacího prvku

Dalším zajímavým případem je mapování zpráv o znacích ovládacího prvku pro rozsah ID ovládacího prvku na jednu obslužnou rutinu. Předpokládejme, že uživatel může klepnout na libovolné z 10 tlačítek. Chcete-li mapovat všech 10 tlačítek na jednu obslužnou rutinu, bude položka mapy zpráv vypadat takto:

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Při zápisu `ON_CONTROL_RANGE` makra do mapy zpráv určíte:

- Konkrétní zpráva o oznamovací mj.

   Tady je to **BN_CLICKED**.

- Hodnoty ID ovládacího prvku přidružené k souvislému rozsahu ovládacích prvků.

   Zde jsou **IDC_BUTTON1** a **IDC_BUTTON10**.

- Název funkce obslužné rutiny zprávy.

   Tady je `OnButtonClicked`to .

Při zápisu funkce obslužné rutiny zadejte další parametr **UINT,** jak je znázorněno v následujícím textu:

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

Obslužná rutina `OnButtonClicked` pro jednu **zprávu BN_CLICKED** nemá žádné parametry. Stejná obslužná rutina pro řadu tlačítek trvá jeden **UINT**. Další parametr umožňuje identifikaci konkrétní ovládací prvek odpovědný za generování **BN_CLICKED** zprávy.

Kód uvedený v příkladu je typický: převod `int` hodnoty předané v rozsahu zpráv a tvrzení, že se jedná o tento případ. Pak můžete provést jinou akci v závislosti na tom, na které tlačítko bylo kliknuto.

## <a name="see-also"></a>Viz také

[Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
