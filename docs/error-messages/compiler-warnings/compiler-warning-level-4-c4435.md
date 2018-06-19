---
title: Kompilátoru (úroveň 4) upozornění C4435 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72c29bd6d9ffdb4eabb036c61d85a6572cef8fe2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293933"
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
 [/vd (zakázání přesunutí konstrukcí)](../../build/reference/vd-disable-construction-displacements.md)