---
title: Kde hledat mapy zpráv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81958eda508a3e0b4b93ac0d169f3aa3bfece2a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434268"
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

