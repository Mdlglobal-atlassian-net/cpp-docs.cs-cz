---
title: Obslužné rutiny pro oblasti Map zpráv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 896977da8ca57cc17a9fa3b7864e1744ee07f35d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930820"
---
# <a name="handlers-for-message-map-ranges"></a>Obslužné rutiny pro oblasti map zpráv
Tento článek vysvětluje způsob namapování řadu zprávy do jedné zprávy funkci obslužné rutiny (namísto mapování jednu zprávu na jenom jednu funkci).  
  
 Existují situace, kdy je potřeba zpracovat více než jeden upozornění na zprávy nebo ovládací prvek stejným způsobem. V takových situacích můžete chtít mapovat všechny zprávy k jedné obslužné rutiny funkce. Oblasti map zpráv umožňují to udělat pro souvislý rozsah zprávy:  
  
-   Můžete namapovat rozsahy ID příkazu pro:  
  
    -   Funkce obslužná rutina příkazu.  
  
    -   Funkce obslužné rutiny aktualizace příkaz.  
  
-   Funkce obslužné rutiny zpráv můžete namapovat zprávy oznámení ovládacího prvku pro rozsah ID ovládacích prvků.  
  
 Témata popsaná v tomto článku:  
  
-   [Zápis položky map zpráv](#_core_writing_the_message.2d.map_entry)  
  
-   [Deklarování obslužné rutiny](#_core_declaring_the_handler_function)  
  
-   [Příklad pro rozsah identifikátory příkazů](#_core_example_for_a_range_of_command_ids)  
  
-   [Příklad pro rozsah ID ovládacích prvků](#_core_example_for_a_range_of_control_ids)  
  
##  <a name="_core_writing_the_message.2d.map_entry"></a> Zápis položky Map zpráv  
 V. CPP soubor, přidejte mapování zpráv zadání, jak je znázorněno v následujícím příkladu:  
  
 [!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]  
  
 Položka mapování zpráv se skládá z následujících položek:  
  
-   Makra map zpráv rozsahu:  
  
    -   [ON_COMMAND_RANGE –](reference/message-map-macros-mfc.md#on_command_range)  
  
    -   [ON_UPDATE_COMMAND_UI_RANGE –](reference/message-map-macros-mfc.md#on_update_command_ui_range)  
  
    -   [ON_CONTROL_RANGE –](reference/message-map-macros-mfc.md#on_control_range)  
  
-   Parametry pro makro:  
  
     První dva makra trvat tři parametry:  
  
    -   ID příkazu, který začíná rozsahu  
  
    -   ID příkazu, který končí rozsahu  
  
    -   Název obslužné rutiny zpráv  
  
     Rozsah ID příkazů musí být spojití.  
  
     Třetí makro `ON_CONTROL_RANGE`, provede další první parametr: oznámení ovládacího prvku zprávy, jako například **EN_CHANGE**.  
  
##  <a name="_core_declaring_the_handler_function"></a> Deklarování obslužné rutiny  
 Přidání vaší obslužné rutiny funkce deklarace v. Soubor H. Následující kód ukazuje, jak to může vypadat, jak je uvedeno níže:  
  
 [!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]  
  
 Funkce obslužných rutin pro jeden příkazy obvykle trvat žádné parametry. S výjimkou funkcí obslužné rutiny aktualizace, funkce obslužné rutiny pro oblasti map zpráv vyžadují další parametr *nID*, typu **Celé_číslo**. Tento parametr je první parametr. Speciálním parametrem přizpůsobí ID navíc příkazu, který je potřeba k určení příkazu, na který se uživatel rozhodl ve skutečnosti.  
  
 Další informace o požadavcích na parametr pro aktualizaci funkce obslužných rutin najdete v tématu [příklad pro určitý rozsah příkaz ID](#_core_example_for_a_range_of_command_ids).  
  
##  <a name="_core_example_for_a_range_of_command_ids"></a> Příklad pro příkaz rozsah ID  
 Když může použijete rozsahy jedním z příkladů je při zpracování příkazy, jako je příkaz zvětšení v ukázce MFC [HIERSVR](../visual-cpp-samples.md). Tento příkaz zvětší zobrazení, škálování mezi 25 % a 300 % jeho normální velikost. Třídy zobrazení na HIERSVR používá rozsah pro zpracování příkazy Zvětšení s položkou map zpráv tvaru toto:  
  
 [!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]  
  
 Když píšete položka mapování zpráv, zadejte:  
  
-   Dva identifikátory příkazů e-mailů, počáteční a koncové souvislý rozsah.  
  
     Tady jsou **ID_VIEW_ZOOM25** a **ID_VIEW_ZOOM300**.  
  
-   Název obslužné rutiny pro příkazy.  
  
     Zde je `OnZoom`.  
  
 Deklarace funkce by vypadat přibližně takto:  
  
 [!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]  
  
 V případě funkce obslužné rutiny aktualizace je podobné a mohly být více široce užitečné. Je celkem běžné zápis `ON_UPDATE_COMMAND_UI` obslužné rutiny pro řadu příkazů a najít sami zápisu nebo ke kopírování, stejný kód opakovaně. Řešení je mapovat rozsah ID na jednu aktualizaci, obslužné rutiny funkce pomocí příkazu `ON_UPDATE_COMMAND_UI_RANGE` makro. Identifikátory příkazů musí tvořit souvislý rozsah. Příklad, naleznete v části `OnUpdateZoom` obslužné rutiny a jeho `ON_UPDATE_COMMAND_UI_RANGE` položku mapování zpráv v ukázkové HIERSVR třídy zobrazení.  
  
 Aktualizovat funkce obslužných rutin pro jeden příkazy obvykle trvat jeden parametr *pCmdUI*, typu `CCmdUI*`. Na rozdíl od funkce obslužných rutin, obslužné rutiny funkce aktualizace pro oblasti map zpráv nevyžadují další parametr *nID*, typu **Celé_číslo**. ID příkazu, který je nutný k určení, který příkaz se uživatel rozhodl ve skutečnosti, je nalezena v `CCmdUI` objektu.  
  
##  <a name="_core_example_for_a_range_of_control_ids"></a> Příklad pro ID rozsahu ovládací prvek  
 Jiné zajímavé případ je mapování zpráv oznámení ovládacího prvku pro řadu ID ovládacích prvků k jedné obslužné rutině. Předpokládejme, že uživatel klepnutím na libovolné 10 tlačítek. Pro mapování všechny 10 tlačítka k jedné obslužné rutině, zadání map zpráv bude vypadat takto:  
  
 [!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]  
  
 Při psaní `ON_CONTROL_RANGE` makro na mapě zprávu, zadejte:  
  
-   Zpráva konkrétní oznámení ovládacího prvku.  
  
     Zde je **BN_CLICKED**.  
  
-   Hodnoty ID řízení přidružené souvislý rozsah ovládacích prvků.  
  
     Tady jsou **IDC_BUTTON1** a **IDC_BUTTON10**.  
  
-   Název obslužné rutiny zpráv.  
  
     Zde je `OnButtonClicked`.  
  
 Když píšete obslužné rutiny, zadejte nadbytečné **Celé_číslo** parametr, jak je znázorněno v následující:  
  
 [!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]  
  
 `OnButtonClicked` Obslužné rutiny pro jeden **BN_CLICKED** zpráva nepřijímá žádné parametry. Stejné obslužné rutiny pro řadu tlačítek má jednu **Celé_číslo**. Parametr navíc umožňuje identifikaci zodpovědný za generování ovládacího prvku konkrétní **BN_CLICKED** zprávy.  
  
 Kód v příkladu je typické: převodu hodnoty předaný `int` v rámci rozsahu zprávu a potvrzující, že se jedná o tento případ. Potom může trvat několik různé akce v závislosti na tom, které se kliknutí na tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace funkcí obslužných rutin zpráv](../mfc/declaring-message-handler-functions.md)
