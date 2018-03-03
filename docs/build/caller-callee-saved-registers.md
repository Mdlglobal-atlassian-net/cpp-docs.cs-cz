---
title: "Volající volaný – uložené registry | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 61e8d57c177ded8102f257cf84adedc0de0e312a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="callercallee-saved-registers"></a>Volající/volaný – uložené registry
Poškození registrů RAX, RCX, RDX, R8, R9, R10, R11 jsou považovány za volatile a je třeba zvážit při volání funkce (pokud bezpečnost dokázat analýza například optimalizace celého programu).  
  
 Zaregistruje RBX, RBP, RDI, RSI, konfigurace, r 12, R13, R14 a R15 se považují za stálé a musí být uložena a obnoveny funkcí, která je používá.  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)