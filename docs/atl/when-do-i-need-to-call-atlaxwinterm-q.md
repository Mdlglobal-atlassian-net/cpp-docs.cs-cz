---
title: "Když je potřeba volat AtlAxWinTerm? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AtlAxWinTerm
dev_langs: C++
helpviewer_keywords: AtlAxWinTerm method
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cdba5255560f220a80a016f17e574721b12f486d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="when-do-i-need-to-call-atlaxwinterm"></a>Když je potřeba volat AtlAxWinTerm?
[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) zrušení registrace **"AtlAxWin80"** třídy oken. Tato funkce by měly volat (pokud už je potřeba vytvořit hostitele windows), po všechny existující hostitele windows zničena. Pokud nemáte volání této funkce, třída okno bude zrušena automaticky při ukončení procesu.  
  
## <a name="see-also"></a>Viz také  
 Když je potřeba volat AtlAxWinInit  
[Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)
