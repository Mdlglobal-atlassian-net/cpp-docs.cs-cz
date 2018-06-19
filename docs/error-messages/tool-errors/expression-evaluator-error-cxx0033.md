---
title: CXX0033 Chyba vyhodnocování výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0033
dev_langs:
- C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 720b1aec6c9be16879119bc0e8148a301507577a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299497"
---
# <a name="expression-evaluator-error-cxx0033"></a>Chyba při vyhodnocování výrazu CXX0033
došlo k chybě v informace o typu OMF  
  
 Spustitelný soubor nemá platný objekt modulu formátu (OMF) pro ladění.  
  
 Tato chyba je stejný jako CAN0033.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Spustitelný soubor nebyl vytvořen s linkeru vydané s touto verzí aplikace Visual C++. Znovu připojit pomocí aktuální verze LINK.exe kód objektu.  
  
2.  Soubor .exe mohlo dojít k poškození. Znovu zkompiluje a znovu připojit programu.