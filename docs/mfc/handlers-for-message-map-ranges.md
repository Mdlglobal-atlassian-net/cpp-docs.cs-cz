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
ms.openlocfilehash: d94f0391c1aebc95b51a1bc94bea28168c445086
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519383"
---
# <a name="handlers-for-message-map-ranges"></a>Obslužné rutiny pro oblasti map zpráv

Tento článek vysvětluje, jak mapovat celou řadu zpráv jedna zpráva funkci obslužné rutiny (namísto mapování zpráv na jenom jednu funkci).

Existují situace, kdy je potřeba zpracovávat více zpráv nebo ovládací prvek oznámení stejným způsobem. Za těchto okolností možná budete chtít mapovat všechny zprávy jedna obslužná rutina funkce. Oblasti map zpráv bylo možné provést pro souvislý rozsah zprávy:

- Můžete mapovat rozsahy ID příkazů do:

  - Funkce obslužné rutiny příkazu.

  - Funkce obslužné rutiny příkazu update.

- Zprávy s oznámením ovládacího prvku pro rozsah ID ovládacích prvků můžete namapovat na funkce obslužné rutiny zprávy.

V tomto článku probíraná témata zahrnují:

- [Zápis položky mapování zpráv](#_core_writing_the_message.2d.map_entry)

- [Deklarace funkce obslužné rutiny](#_core_declaring_the_handler_function)

- [Příklad pro rozsah ID příkazů](#_core_example_for_a_range_of_command_ids)

- [Příklad pro rozsah ID ovládacího prvku](#_core_example_for_a_range_of_control_ids)

##  <a name="_core_writing_the_message.2d.map_entry"></a> Zápis položky mapování zpráv

V. CPP přidejte položky mapování zpráv, jak je znázorněno v následujícím příkladu:

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

Položka mapování zpráv se skládá z následujících položek:

- Makra map zpráv rozsahu:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Parametry do makra:

  První dvě makra mít tři parametry:

  - ID příkazu, který se spustí rozsahu

  - ID příkazu, který končí rozsahu

  - Název obslužné rutiny zpráv

  Rozsah ID příkazů musí být spojití.

  Třetí makro `ON_CONTROL_RANGE`, přijímá další první parametr: zpráva oznámení ovládacího prvku, jako například **EN_CHANGE**.

##  <a name="_core_declaring_the_handler_function"></a> Deklarace funkce obslužné rutiny

Přidat vaše obslužná rutina deklarace funkce v. Soubor H. Následující kód ukazuje, jak to může vypadat, jak je znázorněno níže:

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Funkce obslužné rutiny pro příkazy jeden obvykle nemít žádné parametry. S výjimkou funkce obslužné rutiny aktualizace, vyžadují funkce obslužné rutiny pro oblasti map zpráv speciálním parametrem *nID*, typu **UINT**. Tento parametr je první parametr. Speciálním parametrem obsáhne zvláštní příkaz spouštět ID k určení příkazu, na který uživatel vybral skutečně potřeba.

Další informace o požadavcích na parametr funkce obslužné rutiny aktualizace najdete v tématu [příklad pro určitý rozsah příkaz ID](#_core_example_for_a_range_of_command_ids).

##  <a name="_core_example_for_a_range_of_command_ids"></a> Příklad pro příkaz rozsah ID

Při může být použití rozsahů, jedním z příkladů je při zpracování příkazů, jako jsou příkazu zvětšení v ukázce MFC [HIERSVR](../visual-cpp-samples.md). Tento příkaz zvětší nebo zmenší zobrazení měřítka až 300 % normální velikosti 25 %. Třída zobrazení HIERSVR společnosti používá rozsah zpracovává příkazy přiblížení s položkou mapování zpráv podobné to:

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Při zápisu položky mapování zpráv, zadejte:

- Dva identifikátory, počáteční a koncové souvislý rozsah příkazů.

   Tady jsou **ID_VIEW_ZOOM25** a **ID_VIEW_ZOOM300**.

- Název obslužné rutiny pro příkazy.

   Tady je `OnZoom`.

Deklarace funkce by vypadat přibližně takto:

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

Případ funkce obslužné rutiny aktualizace je podobná a mohly být více velmi užitečné. Je celkem běžné pro zápis `ON_UPDATE_COMMAND_UI` obslužné rutiny pro řadu příkazů a se hodit zápisu nebo ke kopírování, stejný kód pořád dokola. Řešení je mapovat celou řadu příkaz ID do jednoho aktualizovat pomocí funkce obslužné rutiny `ON_UPDATE_COMMAND_UI_RANGE` – makro. Identifikátory příkazů musí tvořit souvislý rozsah. Příklad najdete v tématu `OnUpdateZoom` obslužné rutiny a jeho `ON_UPDATE_COMMAND_UI_RANGE` položku mapování zpráv ve třídě zobrazení HIERSVR vzorku.

Aktualizace funkcí obslužných rutin pro jeden příkazy vám normálně trvalo jediný parametr, *pCmdUI*, typu `CCmdUI*`. Na rozdíl od funkce obslužné rutiny aktualizace funkce obslužné rutiny pro oblasti map zpráv nevyžadují speciálním parametrem *nID*, typu **UINT**. ID příkazu, který je nutný k určení, které příkaz uživatele ve skutečnosti jste zvolili, je součástí `CCmdUI` objektu.

##  <a name="_core_example_for_a_range_of_control_ids"></a> Příklad pro ID ovládacího prvku rozsahu

Další možnost je zajímavé mapuje na jedna obslužná rutina zpráv s oznámením ovládacího prvku pro rozsah ID ovládacího prvku. Předpokládejme, že uživatel může získáte po kliknutí na 10 tlačítka. Pokud chcete namapovat všechny 10 tlačítka jednu obslužnou rutinu, vaší položky mapování zpráv bude vypadat takto:

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Při psaní `ON_CONTROL_RANGE` – makro v mapě zpráv, zadejte:

- Konkrétní oznámení ovládacího prvku zprávy.

   Tady je **BN_CLICKED**.

- ID ovládacího prvku hodnot spojené s souvislý rozsah ovládací prvky.

   Tady jsou **IDC_BUTTON1** a **IDC_BUTTON10**.

- Název obslužné rutiny zprávy.

   Tady je `OnButtonClicked`.

Při zápisu funkce obslužné rutiny, zadejte nadbytečné **UINT** parametru, jak je znázorněno v následujících tématech:

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

`OnButtonClicked` Obslužné rutiny pro jeden **BN_CLICKED** zpráva nemá žádné parametry. Stejnou obslužnou rutinu pro celou řadu tlačítek má jednu **UINT**. Parametr navíc umožňuje identifikaci konkrétní ovládací prvek zodpovědný za generování **BN_CLICKED** zprávy.

Kód ukazuje příklad je typické: převod hodnoty předané do `int` v rámci oblasti zpráv a potvrzující, že se jedná o tento případ. Potom může trvat nějakou jinou akci v závislosti na tom, které došlo ke kliknutí na tlačítko.

## <a name="see-also"></a>Viz také

[Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
