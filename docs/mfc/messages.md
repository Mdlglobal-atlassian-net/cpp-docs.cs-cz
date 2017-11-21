---
title: "Zprávy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1766075663ef924e9a731169a09c3d396d643d2e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="messages"></a>Zprávy
Ve smyčce zpráv **spustit** funkce člena třídy `CWinApp` načte zprávy vytvářené různých událostí zařazených do fronty. Například po kliknutí myší, systém Windows odešle několik zprávy týkající se myš, například `WM_LBUTTONDOWN` při stisknutí levým tlačítkem myši a `WM_LBUTTONUP` uvolnění levé tlačítko. Implementace rozhraní framework zpráva smyčky aplikace odešle zprávy do příslušné okna.  
  
 Důležité kategorie zpráv jsou popsány v [kategorie zpráv](../mfc/message-categories.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprávy a příkazy v rozhraní Framework](../mfc/messages-and-commands-in-the-framework.md)

