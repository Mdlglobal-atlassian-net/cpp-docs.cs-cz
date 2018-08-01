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
ms.openlocfilehash: ce4272ecfee4b3d02d8bf79f7816200a392c9735
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404825"
---
# <a name="exit-function"></a>exit – funkce
**Ukončit** funkce deklarovaná ve standardním vloženém souboru \<stdlib.h >, ukončuje program jazyka C++.  
  
 Hodnota zadaná jako argument **ukončit** je vrácena operačnímu systému jako návratový nebo ukončovací kód programu. Dle konvence návratový kód nula znamená, že byl program dokončen úspěšně.  
  
> [!NOTE]
>  Můžete použít konstanty EXIT_FAILURE a EXIT_SUCCESS definované v \<stdlib.h >, indikující úspěch nebo neúspěch programu.  
  
 Vydání **vrátit** příkaz z `main` je ekvivalentní volání funkce **ukončit** funkce s návratovou hodnotou jako svůj argument.  
  
 Další informace najdete v tématu [ukončit](../c-runtime-library/reference/exit-exit-exit.md) v *Run-Time Library Reference*.  
  
## <a name="see-also"></a>Viz také:  
 [Ukončení programu](../cpp/program-termination.md)