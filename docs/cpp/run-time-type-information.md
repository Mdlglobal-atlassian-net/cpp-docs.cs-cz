---
title: Informace běhového typu | Dokumentace Microsoftu
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77584e5fdd731c499629149a9163dbacb5eafb5e
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467323"
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
  
     Sloužící k uchování informací o typu vrácené **typeid** operátor.  
  
## <a name="see-also"></a>Viz také:  
 [Přetypování](../cpp/casting.md)