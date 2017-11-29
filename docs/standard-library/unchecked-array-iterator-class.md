---
title: "unchecked_array_iterator – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdext::unchecked_array_iterator
dev_langs: C++
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 82c040c4d3e773809d2202c553206e5c98f132db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator – třída
`unchecked_array_iterator` Třída umožňuje zabalit do nezaškrtnuté iterator pole nebo ukazatel. Tato třída slouží jako obálku (pomocí [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator) funkce) pro nezpracovanou ukazatele nebo pole jako cílové způsob, jak spravovat upozornění nezaškrtnuté ukazatel místo globálně silencing tato upozornění. Pokud je to možné, raději zaškrtnuté verze této třídy [checked_array_iterator –](../standard-library/checked-array-iterator-class.md).  
  
> [!NOTE]
>  Tato třída je rozšíření Microsoft standardní knihovny jazyka C++. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Iterator>  
class unchecked_array_iterator;
```  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je definována v [stdext –](../standard-library/stdext-namespace.md) oboru názvů.  
  
 Toto je zaškrtnuté políčko verzi [checked_array_iterator – třída](../standard-library/checked-array-iterator-class.md) a podporuje všechny stejné přetížení a členy. Další informace o funkci zaškrtnuté iterator s příklady kódu najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<iterator >  
  
 **Namespace:** stdext –  
  
## <a name="see-also"></a>Viz také  
 [\<iterator >](../standard-library/iterator.md)   
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)


