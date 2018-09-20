---
title: Mapování zpráv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7324da5eaff15d240cabbaede2c2982021361257
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410975"
---
# <a name="mapping-messages"></a>Mapování zpráv

Každá třída framework, která může přijímat zprávy nebo příkazy má svůj vlastní "mapování zprávy." Rozhraní používá mapy zpráv pro připojení k příslušným obslužným funkcím zprávy a příkazy. Všechny třídy odvozené od třídy `CCmdTarget` může mít mapy zpráv. Další články popisují mapy zpráv podrobně a popisují, jak je používat.

Přestože název "mapu zpráv," zprávy maps zpracovat oba zprávy a příkazy – všechny tři kategorie zpráv, které jsou uvedeny v [kategorie zpráv](../mfc/message-categories.md).

## <a name="see-also"></a>Viz také

[Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)

