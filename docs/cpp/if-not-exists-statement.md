---
title: __if_not_exists – příkaz | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __if_not_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37148a3849e859d7ca77595416616cfa0b952ecf
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939946"
---
# <a name="ifnotexists-statement"></a>__if_not_exists – příkaz
**__If_not_exists** příkaz testuje, jestli existuje zadaný identifikátor. Pokud identifikátor neexistuje, je spuštěn zadaný blok příkazů.  
  
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
|`statements`|Jeden nebo více příkazů, které budou spuštěny, pokud `identifier` neexistuje.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  K dosažení nejspolehlivějších výsledků, použít **__if_not_exists** příkaz následujícími omezeními.  
  
-   Použít **__if_not_exists** příkazu pouze jednoduché typy, nikoli na šablony.  
  
-   Použít **__if_not_exists** příkaz na identifikátory uvnitř i vně třídy. Se nevztahují **__if_not_exists** příkaz pro lokální proměnné.  
  
-   Použití **__if_not_exists** příkaz jenom v těle funkce. Mimo tělo funkce **__if_not_exists** příkazu můžete testovat pouze plně definované typy.  
  
-   Při testování přetížených funkcí nelze testovat konkrétní formu přetížení.  
  
 Doplněk k **__if_not_exists** příkaz je [__if_exists](../cpp/if-exists-statement.md) příkazu.  
  
## <a name="example"></a>Příklad  
 Příklad použití **__if_not_exists**, naleznete v tématu [__if_exists – příkaz](../cpp/if-exists-statement.md).  
  
## <a name="see-also"></a>Viz také  
 [Příkazy výběru](../cpp/selection-statements-cpp.md)   
 [klíčová slova](../cpp/keywords-cpp.md)   
 [__if_exists – příkaz](../cpp/if-exists-statement.md)