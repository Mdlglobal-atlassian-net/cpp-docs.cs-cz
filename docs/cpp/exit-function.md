---
title: exit – funkce | Microsoft Docs
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
ms.openlocfilehash: 5767f6b08b4adcd3d1a8d367c6286a746eeecec3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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