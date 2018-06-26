---
title: Zprávy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d7544d92d55ec4a1f6d15f3c1d4358970bf2deb
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928338"
---
# <a name="messages"></a>Zprávy
Ve smyčce zpráv `Run` funkce člena třídy `CWinApp` načte zprávy vytvářené různých událostí zařazených do fronty. Například když uživatel klikne myš, systém Windows odešle několik zprávy týkající se myš, například WM_LBUTTONDOWN při stisknutí levým tlačítkem myši a WM_LBUTTONUP po vydání levé tlačítko. Implementace rozhraní framework zpráva smyčky aplikace odešle zprávy do příslušné okna.  
  
 Důležité kategorie zpráv jsou popsány v [kategorie zpráv](../mfc/message-categories.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)

