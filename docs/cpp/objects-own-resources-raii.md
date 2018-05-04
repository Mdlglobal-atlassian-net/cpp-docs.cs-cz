---
title: Objekty vlastní prostředky (RAII) | Microsoft Docs
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
ms.openlocfilehash: dfd3f1df54e5b5881ed15efeb98a6e6070f400a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="objects-own-resources-raii"></a>Prostředky ve vlastnictví objektů (RAII)
Ujistěte se, které objekty vlastní prostředky. Tento princip je známý také jako "získávání prostředků je inicializace" nebo "RAII."  
  
## <a name="example"></a>Příklad  
 Každý "new" objekt předejte jako argument konstruktoru jiné s názvem objektu, který je vlastníkem ho (téměř vždy unique_ptr).  
  
```cpp  
void f() {  
    unique_ptr<widget> p( new widget() );  
    my_class x( new widget() );  
    // ...  
} // automatic destruction and deallocation for both widget objects  
  // automatic exception safety, as if "finally { p->dispose(); x.w.dispose(); }"  
```  
  
 Vždy okamžitě předejte všechny nový prostředek k jinému objektu, který ho vlastní.  
  
```cpp  
void g() {  
    other_class y( OpenFile() );  
    // ...  
} // automatic closing and release for file resource  
  // automatic exception safety, as if "finally { y.file.dispose(); }"  
```  
  
## <a name="see-also"></a>Viz také  
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)