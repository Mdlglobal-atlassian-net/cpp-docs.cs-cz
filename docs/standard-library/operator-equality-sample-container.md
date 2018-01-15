---
title: "Operator == (&lt;ukázkový kontejner&gt;) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
dev_langs: C++
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8172f9723ac5ed0a2db0905e22299595be057804
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="operator-ltsample-containergt"></a>Operator == (&lt;ukázkový kontejner&gt;)
> [!NOTE]
>  Toto téma se v dokumentaci k Visual C++ jako funkční příklad kontejnery použít ve standardní knihovně C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).  
  
 Přetížení `operator==` k porovnání dvou objektů třídy šablony [kontejneru](../standard-library/sample-container-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Ty>  
bool operator==(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `left.` [velikost](../standard-library/container-class-size.md) ` == right.size && equal(left.` [začít](../standard-library/container-class-begin.md)`, left.`[end](../standard-library/container-class-end.md)`, right.begin)`.  
  
## <a name="see-also"></a>Viz také  
 [\<Ukázkový kontejner >](../standard-library/sample-container.md)

