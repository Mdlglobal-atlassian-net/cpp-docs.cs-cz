---
title: "exit – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee6a34a70465904e6725f42e68eb4a00c03a1661
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="exit-function"></a>exit – funkce
**Ukončete** funkce, deklarován v souboru standardní zahrnout \<stdlib.h >, ukončí programu C++.  
  
 Hodnota zadaná jako argument pro **ukončete** je vrácen do operačního systému jako návratový kód nebo ukončovací kód programu. Dle konvence návratový kód nula znamená, že byl program dokončen úspěšně.  
  
> [!NOTE]
>  Můžete použít konstanty `EXIT_FAILURE` a `EXIT_SUCCESS`, definované v \<stdlib.h >, indikující úspěch nebo selhání vašeho programu.  
  
 Vydání `return` příkaz z **hlavní** je ekvivalentní volání funkce **ukončete** funkce s návratovou hodnotu jako její argument.  
  
 Další informace najdete v tématu [ukončete](../c-runtime-library/reference/exit-exit-exit.md) v *referenční dokumentace běhové knihovny*.  
  
## <a name="see-also"></a>Viz také  
 [Ukončení programu](../cpp/program-termination.md)