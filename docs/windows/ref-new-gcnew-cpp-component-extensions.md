---
title: REF nové, gcnew (rozšíření komponent C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
dev_langs:
- C++
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9533675d2894b3c3d99e3fb57abded8ea4e99d7a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ref-new-gcnew--c-component-extensions"></a>ref new, gcnew (rozšíření komponent C++)
`ref new` Agregační – klíčové slovo přiděluje instance typu, který je uvolnění z paměti při objektu se změní na nedostupné a která vrací popisovač ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) k objektu přidělená.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 Paměť pro instanci typu, která je přidělena `ref new` je automaticky navrácena.  
  
 A `ref new` operaci vyvolává `OutOfMemoryException` Pokud nelze přidělit paměť.  
  
 Další informace o tom, jak je paměť pro nativní typy C++ přidělené a navrácena najdete v tématu [nové a odstraňte operátory](../cpp/new-and-delete-operators.md).  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Použití `ref new` přidělit paměť pro prostředí Windows Runtime objekty, jejichž doba platnosti, které chcete spravovat automaticky. Objekt je automaticky navrácena, kdy přestane jeho počet odkazů na nulu, které dojde po poslední kopii odkaz byla mimo rozsah. Další informace najdete v tématu [Ref třídy a struktury](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 Tím se přidělí paměť pro spravovaný typ (referenční dokumentace nebo hodnota typu) `gcnew`a navrácena pomocí uvolňování paměti.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad používá `gcnew` přidělit objekt zprávy.  
  
```  
// mcppv2_gcnew_1.cpp  
// compile with: /clr  
ref struct Message {  
   System::String^ sender;  
   System::String^ receiver;  
   System::String^ data;  
};  
  
int main() {  
   Message^ h_Message  = gcnew Message;  
  //...  
}  
```  
  
 **Příklad**  
  
 Následující příklad používá `gcnew` vytvoření typu zabalené hodnoty pro použití jako odkazového typu.  
  
```  
// example2.cpp : main project file.  
// compile with /clr  
using namespace System;  
value class Boxed {  
    public:  
        int i;  
};  
int main()  
{  
    Boxed^ y = gcnew Boxed;  
    y->i = 32;  
    Console::WriteLine(y->i);  
    return 0;  
}  
```  
  
 **Output**  
  
```Output  
32  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)