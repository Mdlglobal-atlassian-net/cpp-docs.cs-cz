---
title: Funkce Exit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d08ac1375fa383543eaafb5b3ce49cd2bbfbc4da
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941077"
---
# <a name="exit-function"></a>exit – funkce
`exit` Funkce deklarovaná ve standardním vloženém souboru \<stdlib.h >, ukončuje program jazyka C++.  
  
 Hodnota zadaná jako argument pro `exit` je vrácena operačnímu systému jako návratový nebo ukončovací kód programu. Dle konvence návratový kód nula znamená, že byl program dokončen úspěšně.  
  
> [!NOTE]
>  Můžete použít konstanty EXIT_FAILURE a EXIT_SUCCESS definované v \<stdlib.h >, indikující úspěch nebo neúspěch programu.  
  
 Vydání **vrátit** příkaz z `main` je ekvivalentní volání funkce `exit` funkce s návratovou hodnotou jako svůj argument.  
  
 Další informace najdete v tématu [ukončit](../c-runtime-library/reference/exit-exit-exit.md) v *Run-Time Library Reference*.  
  
## <a name="see-also"></a>Viz také  
 [Ukončení programu](../cpp/program-termination.md)