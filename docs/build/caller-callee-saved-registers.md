---
title: Volající volaný – uložené registry | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f65e88c8609d6a2097e9e54c3f52cbd27dce36d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="callercallee-saved-registers"></a>Volající/volaný – uložené registry
Poškození registrů RAX, RCX, RDX, R8, R9, R10, R11 jsou považovány za volatile a je třeba zvážit při volání funkce (pokud bezpečnost dokázat analýza například optimalizace celého programu).  
  
 Zaregistruje RBX, RBP, RDI, RSI, konfigurace, r 12, R13, R14 a R15 se považují za stálé a musí být uložena a obnoveny funkcí, která je používá.  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)