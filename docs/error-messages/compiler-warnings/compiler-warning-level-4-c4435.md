---
title: "Kompilátoru (úroveň 4) upozornění C4435 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c3e907aac68727b752ac0516d2b6fbcbc5d4de84
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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