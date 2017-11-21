---
title: "operátor&lt; (&lt;ukázkový kontejner&gt;) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::operator<
- operator<
- std.<
- <
- std.operator<
- std::<
dev_langs: C++
helpviewer_keywords:
- < operator, comparing specific objects
- operator<, valarrays
- < operator
- operator <, valarrays
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3f7aab9f32e51123f15169f5ccbb591ff2d30b67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="operatorlt-ltsample-containergt"></a>operátor&lt; (&lt;ukázkový kontejner&gt;)
> [!NOTE]
>  Toto téma se v dokumentaci k Visual C++ jako funkční příklad kontejnery použít ve standardní knihovně C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).  
  
 Přetížení **operátor <** k porovnání dvou objektů třídy šablony [kontejneru](../standard-library/sample-container-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Ty>  
bool operator<(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `lexicographical_compare(left.begin, left.end, right.begin, right.end)`.  
  
## <a name="see-also"></a>Viz také  
[\<Ukázkový kontejner >](../standard-library/sample-container.md)  
[začít](../standard-library/container-class-begin.md)  
[end](../standard-library/container-class-end.md)  