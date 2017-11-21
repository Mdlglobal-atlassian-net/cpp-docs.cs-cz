---
title: "Informace běhového typu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs: C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4fb5f7413f613aab2d02ee2548a460adfca57b90
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="run-time-type-information"></a>Informace běhového typu
Informace o typu modulu runtime (RTTI) je mechanismus, který umožňuje stanovit typ objektu při provádění programu. RTTI byl přidán do jazyka C++, protože mnoho dodavatelů knihoven tříd implementovalo tuto funkci samostatně. Tím došlo k nekompatibilitě mezi knihovnami. Podpora informací o typu modulu runtime na úrovni jazyka se stala samozřejmostí.  
  
 V zájmu přehlednosti je popis mechanismu RTTI téměř zcela omezen na ukazatele. Uvedenou koncepci lze však také použít pro odkazy.  
  
 Existují tři hlavní prvky jazyka C++ informující o typu modulu runtime:  
  
-   [Dynamic_cast](../cpp/dynamic-cast-operator.md) operátor.  
  
     Používá se pro převod polymorfních typů.  
  
-   [Typeid](../cpp/typeid-operator.md) operátor.  
  
     Používá se k identifikaci přesného typu objektu.  
  
-   [Type_info](../cpp/type-info-class.md) třídy.  
  
     Používá se pro uchovávání informací o typu vráceném operátorem `typeid`.  
  
## <a name="see-also"></a>Viz také  
 [Přetypování](../cpp/casting.md)