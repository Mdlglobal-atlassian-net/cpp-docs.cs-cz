---
title: "value_compare – třída (&lt;mapy&gt;) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
dev_langs: C++
helpviewer_keywords: std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dedc859a140b99d76b98a5109f9fdc56c1c1f90c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="valuecompare-class-ltmapgt"></a>value_compare – třída (&lt;mapy&gt;)
Poskytuje objekt funkce, který můžete porovnat elementy mapy srovnáním jejich klíčů určit jejich relativní pořadí v mapě.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class value_compare : public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(const value_type& left, const value_type& right) const;
    value_compare(key_compare pred) : comp(pred);
protected:
    key_compare comp;
};
```  
  
## <a name="remarks"></a>Poznámky  
 Toto kritérium porovnání poskytované `value_compare` mezi **value_types** celou elementů obsažených mapu je vyvolané z porovnání mezi klíče příslušných elementů ve vytváření pomocná třída. Operátor členské funkce používá objekt **comp** typu `key_compare` uložené v objektu funkce poskytované `value_compare` k porovnání klíč řazení součástí dva elementy.  
  
 Nastaví a multisets, které jsou jednoduché kontejnery, kde jsou hodnoty klíče shodné s hodnotami element, `value_compare` je ekvivalentní `key_compare`, mapy a multimaps nejsou, jako hodnota typu `pair` elementy není stejný jako Hodnota klíče elementu.  
  
## <a name="example"></a>Příklad  
  Podívejte se příklad [value_comp –](../standard-library/map-class.md#value_comp) příklad toho, jak deklarace a používání `value_compare`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<mapy >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [binary_function – struktura](../standard-library/binary-function-struct.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)



