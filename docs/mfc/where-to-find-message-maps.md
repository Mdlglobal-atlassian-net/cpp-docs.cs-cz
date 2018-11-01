---
title: Kde hledat mapy zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: ab21369cecfa977a8397e7e2a7e68394e86e6927
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533468"
---
# <a name="where-to-find-message-maps"></a>Kde hledat mapy zpráv

Při vytváření nového kostru aplikace pomocí Průvodce aplikací, Průvodce aplikací zapíše mapy zpráv pro každou třídu cíli příkazu, které vytvoří za vás. To zahrnuje odvozené aplikace, dokumentu, zobrazení a třídy oken s rámečkem. Některé z těchto zprávy maps už máte položky zadané pomocí Průvodce aplikací pro určité zprávy a předdefinovaných příkazů a některé jsou jenom zástupné symboly pro obslužné rutiny, které přidáte.

Mapování třídy zpráv se nachází v. Soubor CPP pro třídu. Práce s mapami základní zpráv, které vytvoří Průvodce aplikací, použijte v okně Vlastnosti mohli přidat záznamy pro zprávy a příkazy, které bude zpracovávat jednotlivé třídy. Mapování typické zprávy může vypadat následovně, poté, co přidáte některé položky:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

Mapy zpráv se skládá z kolekce maker. Dvě makra [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) a [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), párování mapování zprávy. Dalších maker, jako například `ON_COMMAND`, vyplňte obsah v mapování zprávy.

> [!NOTE]
>  Makra map zpráv nejsou následuje středníkem.

Při použití průvodce Přidat třídu pro vytvoření nové třídy obsahuje mapy zpráv pro třídu. Alternativně můžete vytvořit mapu zpráv ručně pomocí editoru zdrojového kódu.

## <a name="see-also"></a>Viz také

[Jak framework prohledává mapy zpráv](../mfc/how-the-framework-searches-message-maps.md)

