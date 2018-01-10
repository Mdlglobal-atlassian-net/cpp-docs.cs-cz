---
title: "exit – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Exit
dev_langs: C++
helpviewer_keywords: exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b9e0d6a7f903d4af39698b2d98c005cbf64515eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exit-function"></a>exit – funkce
**Ukončete** funkce, deklarován v souboru standardní zahrnout STDLIB. H, ukončí programu C++.  
  
 Hodnota zadaná jako argument pro **ukončete** je vrácen do operačního systému jako návratový kód nebo ukončovací kód programu. Dle konvence návratový kód nula znamená, že byl program dokončen úspěšně.  
  
> [!NOTE]
>  Úspěch nebo neúspěch programu lze indikovat konstantami `EXIT_FAILURE` a `EXIT_SUCCESS` definovanými v souboru STDLIB.H.  
  
 Vydání `return` příkaz z **hlavní** je ekvivalentní volání funkce **ukončete** funkce s návratovou hodnotu jako její argument.  
  
 Další informace najdete v tématu [ukončete](../c-runtime-library/reference/exit-exit-exit.md) v *referenční dokumentace běhové knihovny*.  
  
## <a name="see-also"></a>Viz také  
 [Ukončení programu](../cpp/program-termination.md)