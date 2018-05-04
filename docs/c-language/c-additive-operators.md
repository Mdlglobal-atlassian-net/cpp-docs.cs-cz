---
title: Operátory sčítání jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df491508f7898fe3c97bc02a83e5259baa9c89f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-additive-operators"></a>Operátory sčítání jazyka C
Operátory sčítání provést přidání (**+**) a odčítání (**-**).  
  
## <a name="syntax"></a>Syntaxe  
 *doplňkové výraz*:  
 *multiplikativní výraz*  
  
 *doplňkové výraz***+***multiplikativní výraz*   
  
 *doplňkové výraz***-***multiplikativní výraz*   
  
> [!NOTE]
>  I když syntaxe *doplňkové výraz* zahrnuje *multiplikativní výraz*, to neznamená, že pomocí násobení výrazy jsou povinné. V tématu Syntaxe [souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md), pro *multiplikativní výraz*, *výraz cast*, a *unární výraz*.  
  
 Operandy může být nedílnou nebo plovoucí hodnoty. Některé sčítání operace lze také provést na ukazatel hodnoty, jak je uvedeno v části diskuzi o každé operátor.  
  
 Operátory sčítání provést obvyklé aritmetické převody plovoucí a integrální operandy. Typ výsledku je typ operandy po převodu. Vzhledem k tomu, že převody provádí operátorů sčítání neposkytují přetečení nebo podtečení podmínky, informace mohou být ztraceny, pokud výsledek operace sčítání není možné vyjádřit v typ operandy po převodu.  
  
## <a name="see-also"></a>Viz také  
 [Operátory sčítání: + a -](../cpp/additive-operators-plus-and.md)