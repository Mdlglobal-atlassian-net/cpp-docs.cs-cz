---
title: "Informace běhového typu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b0b0124a69a0110bda94055964fbcdb54e5a754
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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