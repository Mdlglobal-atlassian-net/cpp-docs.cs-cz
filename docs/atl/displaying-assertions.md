---
title: "Zobrazení kontrolních výrazů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ebfa692f422283e69395639295b3bf2ace1741ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="displaying-assertions"></a>Zobrazení kontrolní výrazy
Pokud klient pro připojení ke službě se zobrazí přestane reagovat, může služba prohlašovanou a zobrazí okno se zprávou, není možné zobrazit. Můžete to ověřit pomocí ladicí program Visual C++ pro ladění kódu (viz [pomocí Správce úloh](../atl/using-task-manager.md) nahoře v této části).  
  
 Pokud zjistíte, že služby zobrazit okno se zprávou, která se nezobrazí, můžete chtít nastavit **povolit služby interakcí s plochou** možnost před použitím služby znovu. Tato možnost je spuštění parametr, který umožňuje zprávami zobrazuje službu tak, aby se na ploše. Pokud chcete nastavit tuto možnost, otevřete aplikaci ovládacím panelu služby, vyberte službu, klikněte na **spuštění**a pak vyberte **povolit služby interakcí s plochou** možnost.  
  
## <a name="see-also"></a>Viz také  
 [Ladění tipy](../atl/debugging-tips.md)

