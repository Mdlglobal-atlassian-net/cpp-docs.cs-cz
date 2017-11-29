---
title: "__if_not_exists – příkaz | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __if_not_exists_cpp
dev_langs: C++
helpviewer_keywords: __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5bd11ed833b54082d7ea2a394bdd4cad3c3e1321
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ifnotexists-statement"></a>__if_not_exists – příkaz
Příkaz `__if_not_exists` testuje, zda existuje zadaný identifikátor. Pokud identifikátor neexistuje, je spuštěn zadaný blok příkazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__if_not_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`identifier`|Identifikátor, jehož existence bude testována.|  
|`statements`|Jeden nebo více příkazů k provedení Pokud `identifier` neexistuje.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  K dosažení nejspolehlivějších výsledků je třeba použít příkaz `__if_not_exists` s následujícími omezeními.  
  
-   Příkaz `__if_not_exists` je třeba použít pouze na jednoduché typy, nikoli na šablony.  
  
-   Příkaz `__if_not_exists` je třeba použít na identifikátory uvnitř i vně třídy. Příkaz `__if_not_exists` se nepoužívá pro lokální proměnné.  
  
-   Příkaz `__if_not_exists` je třeba použít pouze v rámci těla funkce. Mimo tělo funkce může příkaz `__if_not_exists` testovat pouze plně definované typy.  
  
-   Při testování přetížených funkcí nelze testovat konkrétní formu přetížení.  
  
 Doplněk k `__if_not_exists` příkaz [__if_exists –](../cpp/if-exists-statement.md) příkaz.  
  
## <a name="example"></a>Příklad  
 Příklad o tom, jak používat `__if_not_exists`, najdete v části [__if_exists – příkaz](../cpp/if-exists-statement.md).  
  
## <a name="see-also"></a>Viz také  
 [Příkazy výběru](../cpp/selection-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [__if_exists – příkaz](../cpp/if-exists-statement.md)