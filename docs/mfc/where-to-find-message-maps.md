---
title: Kde hledat mapy zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: eec0ae43546e3cc0c08e3178c4808e21fa48686a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360167"
---
# <a name="where-to-find-message-maps"></a>Kde hledat mapy zpráv

Když vytvoříte novou aplikaci kostry pomocí Průvodce aplikací, Průvodce aplikací napíše mapu zpráv pro každou třídu cíle příkazu, kterou pro vás vytvoří. To zahrnuje odvozené aplikace, dokumentu, zobrazení a frame-window třídy. Některé z těchto map zpráv již mají položky zadané Průvodcem aplikací pro určité zprávy a předdefinované příkazy a některé jsou pouze zástupné symboly pro obslužné rutiny, které přidáte.

Mapa zpráv třídy je umístěna v rozhraní . CPP pro třídu. Při práci se základními mapami zpráv, které vytvoří Průvodce aplikací, můžete pomocí [Průvodce třídou](reference/mfc-class-wizard.md) přidávat položky pro zprávy a příkazy, které budou jednotlivé třídy zpracovávat. Po přidání některých položek může typické mapování zpráv vypadat takto:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

Mapa zpráv se skládá z kolekce maker. Mapa zpráv se mohou síta dvěma makry, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) a [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map). Ostatní makra, `ON_COMMAND`například , vyplňte obsah mapy zpráv.

> [!NOTE]
> Makra mapy zpráv nejsou následována středníky.

Při použití průvodce Přidat třídu k vytvoření nové třídy, poskytuje mapu zpráv pro třídu. Případně můžete vytvořit mapu zpráv ručně pomocí editoru zdrojového kódu.

## <a name="see-also"></a>Viz také

[Jak framework prohledává mapy zpráv](../mfc/how-the-framework-searches-message-maps.md)
