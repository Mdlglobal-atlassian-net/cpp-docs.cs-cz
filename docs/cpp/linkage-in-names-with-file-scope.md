---
title: "Propojení v názvech s rozsahem souboru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- static modifier, file scope
- static names and file scope
- file scope [C++]
- declarations [C++], external
- external linkage, scope linkage rules
- static variables, external declarations
ms.assetid: 38d3fa5e-1861-466e-a590-84b86f7b184e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5896c1c50b6e7d73c259ba19e6e2bbab77e86d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linkage-in-names-with-file-scope"></a>Propojení v názvech s rozsahem souboru
Pro názvy s oborem souboru (kromě názvů `typedef` a výčtů) platí následující pravidla propojení:  
  
-   Pokud je název explicitně deklarován jako **statické**, má vnitřní propojení a identifikuje elementu programu uvnitř vlastní překlad jednotky.  
  
-   Názvy výčtů a názvy `typedef` nemají žádné propojení.  
  
-   Všechny ostatní názvy v oboru souboru mají vnější propojení.  
  
 **Konkrétní Microsoft**  
  
-   Pokud je název funkce s rozsahem souboru explicitně deklarován jako **vložené**, má externí propojení, pokud je vytvořena instance nebo jeho adresy odkazuje. Funkce s oborem souboru proto může mít vnitřní i vnější propojení.  
  
 **Konkrétní Microsoft END**  
  
 Třída má vnitřní propojení, pokud:  
  
-   Nepoužívá žádné funkce jazyka C++ (například řízení přístupu k členům, členské funkce, konstruktory, destruktory a podobně).  
  
-   Není používána v deklaraci jiného názvu s vnějším propojením. Toto omezení znamená, že vlivem objektů typu třídy předaných funkcím s vnějším propojením mají třídy vnější propojení.  
  
## <a name="see-also"></a>Viz také  
 [Program a propojení](../cpp/program-and-linkage-cpp.md)