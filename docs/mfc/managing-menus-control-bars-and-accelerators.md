---
title: "Správa nabídek, ovládacích pruhů a akcelerátorů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MDI [MFC], frame windows
- control bars [MFC], updating in frame windows
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- accelerator tables [MFC]
- sharing menus [MFC]
- updating user-interface objects [MFC]
- frame windows [MFC], updating
- status bars [MFC], updating
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 74b026f273eec0bc689cc6959890b07beb570893
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="managing-menus-control-bars-and-accelerators"></a>Správa nabídek, ovládacích pruhů a akcelerátorů
Okně s rámečkem spravuje aktualizace objektů uživatelského rozhraní, včetně nabídky, tlačítek panelu nástrojů, stavového řádku a akcelerátorů. Spravuje taky sdílení panelu nabídek v aplikace MDI.  
  
## <a name="managing-menus"></a>Správa nabídek  
 Okně s rámečkem účastní aktualizace položek uživatelského rozhraní pomocí `ON_UPDATE_COMMAND_UI` mechanismus popsané v [postup aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md). Tlačítka na panely nástrojů a dalších ovládací pruhy jsou aktualizovány během nečinné smyčky. Položky nabídky v rozevíracích nabídek v řádku nabídek se aktualizují těsně před rozbalení nabídky.  
  
 Pro aplikace MDI rámce okna MDI spravuje řádku nabídek a titulek. Rámec okna MDI vlastní jeden výchozí nabídka, která se používá jako panelu nabídek, pokud nejsou žádné aktivní podřízených oken MDI. Pokud nejsou aktivní, děti, řádku nabídek rámce okna MDI převzat nabídky aktivního okna podřízeného MDI. Pokud aplikace MDI podporuje více typů dokumentů, jako jsou dokumenty graf a listu, každý typ umístí vlastní nabídky do panelu nabídek a změní Titulek hlavního rámce okna.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) poskytuje výchozí implementaci pro standardní příkazy v zobrazené nabídce okna pro aplikace MDI. Konkrétně, příkaz nové okno (**id_window_new –**) je implementována pro vytvoření nové oken s rámečkem a zobrazení v aktuálním dokumentu. Je nutné přepsat tyto implementace, pouze pokud je potřeba upravit vlastní nastavení.  
  
 Více podřízených oken MDI stejného typu dokumentu sdílet prostředky nabídky. Pokud několik podřízených oken MDI jsou vytvořené pomocí stejné šablony dokumentu, můžete všechny používají stejný prostředek nabídky, ukládání na systémové prostředky v systému Windows.  
  
## <a name="managing-the-status-bar"></a>Správa stavového řádku  
 Okně s rámečkem také umisťuje stavového řádku v rámci své klientské oblasti a spravuje stav indikátory panelu. Okně s rámečkem vymaže a podle potřeby aktualizace oblast zprávy ve stavovém řádku a zobrazí výzva řetězce jako uživatel vybere položky nabídky nebo tlačítka panelu nástrojů, jak je popsáno v [postup zobrazení informací o příkazu ve stavovém řádku](../mfc/how-to-display-command-information-in-the-status-bar.md).  
  
## <a name="managing-accelerators"></a>Správa akcelerátorů  
 Každý oken s rámečkem udržuje tabulky akcelerátorů volitelné, klávesové překlad akcelerátoru pro vás automaticky. Tento mechanismus snadno definovat klávesy akcelerátoru (také nazývané klávesové zkratky), které vyvolají příkazy nabídky.  
  
## <a name="see-also"></a>Viz také  
 [Použití oken s rámečkem](../mfc/using-frame-windows.md)

