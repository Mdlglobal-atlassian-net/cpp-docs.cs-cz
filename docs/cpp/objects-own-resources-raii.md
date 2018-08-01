---
title: Objekty vlastní prostředky (RAII) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f86b484e-5a27-4c3b-a92a-dfaa5dd6d93a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 265eccc4c1a9f51a03e5a84433a9f7e9cc6d6a92
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402133"
---
# <a name="objects-own-resources-raii"></a>Prostředky ve vlastnictví objektů (RAII)
Ujistěte se, že objekty vlastní prostředky. Tento princip se označuje také jako "získávání prostředků je inicializace" nebo "RAII."  
  
## <a name="example"></a>Příklad  
 Každý "nové" objekt předejte jako argument konstruktoru jiného pojmenovaný objekt, který ji (téměř vždy unique_ptr) vlastní.  
  
```cpp  
void f() {  
    unique_ptr<widget> p( new widget() );  
    my_class x( new widget() );  
    // ...  
} // automatic destruction and deallocation for both widget objects  
  // automatic exception safety, as if "finally { p->dispose(); x.w.dispose(); }"  
```  
  
 Nový prostředek bezprostředně předejte jiným objektem, který ho vlastní.  
  
```cpp  
void g() {  
    other_class y( OpenFile() );  
    // ...  
} // automatic closing and release for file resource  
  // automatic exception safety, as if "finally { y.file.dispose(); }"  
```  
  
## <a name="see-also"></a>Viz také:  
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)