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
ms.openlocfilehash: abd49410f9982788e9403f0cb83ca8656473417d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344101"
---
# <a name="messages"></a>Zprávy
Ve smyčce zpráv **spustit** funkce člena třídy `CWinApp` načte zprávy vytvářené různých událostí zařazených do fronty. Například po kliknutí myší, systém Windows odešle několik zprávy týkající se myš, například `WM_LBUTTONDOWN` při stisknutí levým tlačítkem myši a `WM_LBUTTONUP` uvolnění levé tlačítko. Implementace rozhraní framework zpráva smyčky aplikace odešle zprávy do příslušné okna.  
  
 Důležité kategorie zpráv jsou popsány v [kategorie zpráv](../mfc/message-categories.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)

