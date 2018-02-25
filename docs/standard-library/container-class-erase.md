---
title: "Třída kontejneru::Erase | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 67eee4461f6618abd46bcfe94dab9da942b69955
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="container-classerase"></a>Třída kontejneru::erase
> [!NOTE]
>  Toto téma se v dokumentaci k Visual C++ jako funkční příklad kontejnery použít ve standardní knihovně C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).  
  
 Vymaže elementu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 
    iterator erase(
    iterator _Where);

iterator erase(
    iterator first,  
    iterator last);
```  
  
## <a name="remarks"></a>Poznámky  
 Odebere první členská funkce elementu řízené sekvenci, na kterou odkazuje *_Where*. Druhý členská funkce odebere elementy řízené sekvenci v rozsahu [`first`, `last`). Obě vrací iterátor, který označí první prvek zbývající nad rámec všechny elementy odebrán, nebo [end](../standard-library/container-class-end.md) Pokud neexistuje žádný takový prvek.  
  
 Členské funkce vyvolat výjimku pouze v případě, že operace kopírování vyvolá výjimku.  
  
## <a name="see-also"></a>Viz také  
 [Ukázkový kontejner – třída](../standard-library/sample-container-class.md)
