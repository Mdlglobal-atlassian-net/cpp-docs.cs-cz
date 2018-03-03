---
title: "Kompilátoru (úroveň 4) upozornění C4435 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7136cfb61a7452b7e835030216d08f064874df8b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4435"></a>C4435 kompilátoru upozornění (úroveň 4)
'class1': z důvodu virtuální base 'class2' se změní rozložení objektů v /vd2  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 V části výchozí zkompilovat možnost/vd1, odvozené třídy nemá `vtordisp` pole pro uvedené virtuální základní.  Pokud /vd2 nebo `#pragma vtordisp(2)` je v platnosti `vtordisp` pole bude k dispozici, změna rozložení objektu.  To může vést k problémům binární kompatibilitu, pokud jsou vzájemně komunikující moduly zkompilovány jiné `vtordisp` nastavení.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4435.  
  
```cpp  
// C4435.cpp  
// compile with: /c /W4  
#pragma warning(default : 4435)  
class A  
{  
public:  
    virtual ~A() {}  
};  
  
class B : public virtual A  // C4435  
{};  
```  
  
## <a name="see-also"></a>Viz také  
 [vtordisp](../../preprocessor/vtordisp.md)   
 [/VD (zakázat posunutí konstrukcí)](../../build/reference/vd-disable-construction-displacements.md)