---
title: 'Postupy: Zobrazení informací o příkazu ve stavovém řádku'
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: c93787b3799306d6008299e7c1be6e429bc4c2d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160286"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Postupy: Zobrazení informací o příkazu ve stavovém řádku

Při spuštění Průvodce aplikací k vytvoření kostra aplikace může podporovat panelu nástrojů a stavový řádek. Pouze jedna z možností v Průvodci aplikací podporuje oboje. Když stavový řádek je k dispozici, aplikace automaticky poskytují užitečné zpětnou vazbu, jak uživatel přesouvá ukazatel myši nad položkami v nabídkách. Řetězec výzvy aplikace automaticky zobrazí ve stavovém řádku, při zvýraznění položky nabídky. Například když uživatel přesune ukazatel myši **Vyjmout** příkaz **upravit** nabídky, může ve stavovém řádku zobrazí "Vyjme výběr a umístí jej do schránky" v oblasti zpráv ve stavovém řádku. Na řádku pomáhá uživatelům pochopit účel položky nabídky. Tento postup funguje i když uživatel klikne na tlačítko panelu nástrojů.

Můžete přidat tuto nápovědu stavový řádek tak, že definujete řetězce výzev pro položky nabídky, které přidáte do programu. K tomuto účelu poskytuje řetězce výzev při úpravě vlastností položky nabídky v nabídce editoru. Řetězce, které definujete jsou uloženy v souboru prostředků aplikace. mají stejné ID jako příkazy, které jsou zde popsány.

Ve výchozím nastavení, Průvodce aplikací přidá **AFX_IDS_IDLEMESSAGE**, ID pro standardní zprávy "Připraveno", které se zobrazí, když program čeká na nové zprávy. Pokud zadáte možnost Context-Sensitive Help v Průvodci aplikací, zprávy se změní na "Nápovědy, stiskněte klávesu F1."

## <a name="see-also"></a>Viz také:

[Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)
