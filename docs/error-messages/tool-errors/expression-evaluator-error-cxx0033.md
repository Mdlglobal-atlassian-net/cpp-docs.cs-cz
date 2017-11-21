---
title: "CXX0033 Chyba vyhodnocování výrazu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0033
dev_langs: C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 618dbe464adc64f36e35b9c329eb476166b8b5e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0033"></a>Chyba při vyhodnocování výrazu CXX0033
došlo k chybě v informace o typu OMF  
  
 Spustitelný soubor nemá platný objekt modulu formátu (OMF) pro ladění.  
  
 Tato chyba je stejný jako CAN0033.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Spustitelný soubor nebyl vytvořen s linkeru vydané s touto verzí aplikace Visual C++. Znovu připojit pomocí aktuální verze LINK.exe kód objektu.  
  
2.  Soubor .exe mohlo dojít k poškození. Znovu zkompiluje a znovu připojit programu.