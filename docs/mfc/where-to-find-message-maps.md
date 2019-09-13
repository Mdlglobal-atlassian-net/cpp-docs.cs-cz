---
title: Kde hledat mapy zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: c50c6fc1134f579859530972dc864103c4e0ebcf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907358"
---
# <a name="where-to-find-message-maps"></a>Kde hledat mapy zpráv

Když vytváříte novou kostru aplikace pomocí Průvodce aplikací, Průvodce aplikací zapíše mapu zpráv pro každou třídu cílového příkazu, kterou vytvoří. To zahrnuje vaše odvozené třídy aplikace, dokumentu, zobrazení a oken s rámečkem. Některé z těchto map zpráv již mají položky zadané v Průvodci aplikací pro určité zprávy a předdefinované příkazy a některé jsou pouze zástupné symboly pro obslužné rutiny, které budete přidávat.

Mapa zpráv třídy je umístěna v. Soubor CPP pro třídu Práce se základními mapami zpráv, které Průvodce aplikací vytvoří, můžete použít [Průvodce třídou](reference/mfc-class-wizard.md) k přidání položek pro zprávy a příkazy, které budou zpracovávat jednotlivé třídy. Typická mapa zpráv může po přidání některých položek vypadat takto:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

Mapa zpráv se skládá z kolekce maker. Mapa zpráv se dvěma makry, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) a [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map). Další makra, například `ON_COMMAND`, vyplňte obsah v mapě zprávy.

> [!NOTE]
>  Makra map zpráv nejsou následována středníkem.

Použijete-li Průvodce přidáním třídy k vytvoření nové třídy, bude pro třídu k dispozici mapa zpráv. Případně můžete vytvořit mapu zpráv ručně pomocí editoru zdrojového kódu.

## <a name="see-also"></a>Viz také:

[Jak framework prohledává mapy zpráv](../mfc/how-the-framework-searches-message-maps.md)
