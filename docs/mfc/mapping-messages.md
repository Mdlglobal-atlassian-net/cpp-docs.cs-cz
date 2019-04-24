---
title: Mapování zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], about message maps
- mappings [MFC], commands
- commands [MFC], mapping
- command mapping [MFC]
- message handling [MFC], connecting to handler functions
- commands [MFC], connecting to handler functions
- mappings [MFC], messages
- messages [MFC], mapping
ms.assetid: 996f0652-0698-4b8c-b893-cdaa836d9d0f
ms.openlocfilehash: 82c55c82d6b7a3faa65906345137885555a57d08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279227"
---
# <a name="mapping-messages"></a>Mapování zpráv

Každá třída framework, která může přijímat zprávy nebo příkazy má svůj vlastní "mapování zprávy." Rozhraní používá mapy zpráv pro připojení k příslušným obslužným funkcím zprávy a příkazy. Všechny třídy odvozené od třídy `CCmdTarget` může mít mapy zpráv. Další články popisují mapy zpráv podrobně a popisují, jak je používat.

Přestože název "mapu zpráv," zprávy maps zpracovat oba zprávy a příkazy – všechny tři kategorie zpráv, které jsou uvedeny v [kategorie zpráv](../mfc/message-categories.md).

## <a name="see-also"></a>Viz také:

[Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)
