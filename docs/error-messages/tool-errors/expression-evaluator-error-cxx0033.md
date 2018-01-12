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
ms.workload: cplusplus
ms.openlocfilehash: 49f2b6221d385587fa5e62af51d37eb7d3b78872
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0033"></a>Chyba při vyhodnocování výrazu CXX0033
došlo k chybě v informace o typu OMF  
  
 Spustitelný soubor nemá platný objekt modulu formátu (OMF) pro ladění.  
  
 Tato chyba je stejný jako CAN0033.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Spustitelný soubor nebyl vytvořen s linkeru vydané s touto verzí aplikace Visual C++. Znovu připojit pomocí aktuální verze LINK.exe kód objektu.  
  
2.  Soubor .exe mohlo dojít k poškození. Znovu zkompiluje a znovu připojit programu.