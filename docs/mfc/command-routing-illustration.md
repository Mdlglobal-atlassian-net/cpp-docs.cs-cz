---
title: Znázornění směrování příkazů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46449a90223bdb5e7774d4be5710014ff2c6ccae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406071"
---
# <a name="command-routing-illustration"></a>Znázornění směrování příkazů

Pro ilustraci, vezměte v úvahu zprávou příkazu z vymazat všechny položky nabídky v nabídce Úpravy aplikace MDI. Předpokládejme, že se stane, obslužné rutiny pro tento příkaz jako členské funkce třídy dokumentu aplikace. Zde je, jak tento příkaz dosáhne její obslužná rutina po kliknutí na položku nabídky:

1. Hlavní okno rámce nejprve obdrží zprávu příkazu.

1. Hlavní okno rámce MDI dává příležitost dobře se zpracování příkazu aktuálně aktivní podřízené okno MDI.

1. Standardní směrování podřízeným oknem rámce MDI poskytuje jeho zobrazení šanci na příkaz před vrácením vlastní mapu zpráv.

1. Toto zobrazení nejprve zkontroluje vlastní mapu zpráv a další hledání žádná obslužná rutina trasy příkaz jeho přidružený dokument.

1. Dokument ověří jeho mapu zpráv a vyhledá obslužnou rutinu. Tento dokument členská funkce je volána a směrování se zastaví.

Pokud dokument neměl obslužnou rutinu, ho by příkaz Další směrování do šablony dokumentu. Příkaz by vrátíte se do zobrazení a pak okno rámce. Okno rámce by nakonec zkontrolujte jeho mapování zprávy. Pokud tento kontrola selhala stejně, by se směroval příkaz zpět na hlavní okno rámce MDI a potom na objekt aplikace – ultimate cílové neošetřené příkazy.

## <a name="see-also"></a>Viz také

[Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

