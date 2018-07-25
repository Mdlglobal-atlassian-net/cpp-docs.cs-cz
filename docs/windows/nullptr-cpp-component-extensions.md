---
title: nullptr (rozšíření komponent C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33a276c383618531103a76b1f20c6ad478d57c10
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880680"
---
# <a name="nullptr--c-component-extensions"></a>nullptr (rozšíření komponent C++)
`nullptr` Představuje – klíčové slovo *hodnota ukazatele null*. Použijte ukazatele null hodnotu indikující, že popisovač objektu, vnitřní ukazatel nebo nativní ukazatel typu neodkazuje na objekt.  
  
 Použití `nullptr` se spravovaným nebo nativním kódem. Kompilátor vydává odpovídající ale jiné pokyny pro hodnoty spravovaná a nativní ukazatele null. Informace o používání ISO standardní C++ verzi klíčového slova, najdete v tématu [nullptr](../cpp/nullptr.md).  
  
 `__nullptr` – Klíčové slovo je specifické pro společnost Microsoft klíčové slovo, který má stejný význam jako `nullptr`, ale platí pro pouze nativního kódu. Pokud používáte `nullptr` s nativní C/C++ kód a potom kompilovat s [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru, kompilátor nemůže určit, zda `nullptr` označuje hodnotu nativní nebo spravovaný ukazatele null. Chcete-li svůj záměr zrušte pro kompilátor, použijte `nullptr` zadat spravovaných hodnotu nebo `__nullptr` zadat nativní hodnotu.  
  
 `nullptr` – Klíčové slovo je ekvivalentní `Nothing` v jazyce Visual Basic a `null` v jazyce C#.  
  
## <a name="usage"></a>Použití  
 `nullptr` – Klíčové slovo lze použít kdekoli popisovač, nativní ukazatel nebo argument funkce lze použít.  
  
 `nullptr` – Klíčové slovo není typu a není podporována pro použití se službou:  
  
-   [sizeof](../cpp/sizeof-operator.md)  
  
-   [typeid](../cpp/typeid-operator.md)  
  
-   `throw nullptr` (i když `throw (Object^)nullptr;` bude fungovat)  
  
 `nullptr` – Klíčové slovo lze použít při inicializaci z následujících typů ukazatele:  
  
-   Nativní ukazatel  
  
-   Obslužná rutina prostředí Windows Runtime  
  
-   Spravované popisovač  
  
-   Spravované vnitřních ukazatelů  
  
 `nullptr` – Klíčové slovo lze použít k testování Pokud ukazatel nebo popisovač odkaz má hodnotu null, před použitím odkaz.  
  
 Volání funkcí mezi jazyky, které používají hodnoty ukazatele null chyby kontroly by se daly správně interpretovat.  
  
 Nelze inicializovat popisovač pro nula; pouze `nullptr` lze použít. Vytvoří přiřazení konstantní 0 pro popisovač objektu zabalené `Int32` a přetypování na `Object^`.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, který `nullptr` – klíčové slovo lze použít bez ohledu na popisovač, nativní ukazatel, nebo můžete použít jako argument funkce. A ukazuje příklad, který `nullptr` – klíčové slovo lze použít ke kontrole odkaz, než bude použit.  
  
```  
// mcpp_nullptr.cpp  
// compile with: /clr  
value class V {};  
ref class G {};  
void f(System::Object ^) {}  
  
int main() {  
// Native pointer.  
   int *pN = nullptr;  
// Managed handle.  
   G ^pG = nullptr;  
   V ^pV1 = nullptr;  
// Managed interior pointer.  
   interior_ptr<V> pV2 = nullptr;  
// Reference checking before using a pointer.  
   if (pN == nullptr) {}  
   if (pG == nullptr) {}  
   if (pV1 == nullptr) {}  
   if (pV2 == nullptr) {}  
// nullptr can be used as a function argument.  
   f(nullptr);   // calls f(System::Object ^)  
}  
```  
  
## <a name="example"></a>Příklad  
 **Příklad**  
  
 Následující příklad kódu ukazuje, že `nullptr` a nula zaměnitelné v nativních ukazatele.  
  
```  
// mcpp_nullptr_1.cpp  
// compile with: /clr  
class MyClass {  
public:  
   int i;  
};  
  
int main() {  
   MyClass * pMyClass = nullptr;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
  
   pMyClass = 0;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
}  
```  
  
 **Output**  
  
```Output  
pMyClass == nullptr  
  
pMyClass == 0  
  
pMyClass == nullptr  
  
pMyClass == 0  
```  
  
## <a name="example"></a>Příklad  
 **Příklad**  
  
 Následující příklad kódu ukazuje, že `nullptr` interpretována jako popisovač pro jakýkoli typ nebo nativní ukazatel na libovolného typu. V případě přetížení funkcí s obslužné rutiny pro různé typy, vygeneruje chybu nejednoznačnosti. `nullptr` By musel být explicitně přetypovat na typ.  
  
```  
// mcpp_nullptr_2.cpp  
// compile with: /clr /LD  
void f(int *){}  
void f(int ^){}  
  
void f_null() {  
   f(nullptr);   // C2668  
   // try one of the following lines instead  
   f((int *) nullptr);  
   f((int ^) nullptr);  
}  
```  
  
## <a name="example"></a>Příklad  
 **Příklad**  
  
 Následující příklad kódu ukazuje, že přetypování `nullptr` je povolena a vrátí ukazatel nebo popisovač přetypování typu, který obsahuje `nullptr` hodnotu.  
  
```  
// mcpp_nullptr_3.cpp  
// compile with: /clr /LD  
using namespace System;  
template <typename T>   
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type  
  
int main() {  
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)  
  
   // Delete the following line to resolve.  
   f(nullptr);  
  
   f(0);   // T = int, call f(int)  
}  
```  
  
## <a name="example"></a>Příklad  
 **Příklad**  
  
 Následující příklad kódu ukazuje, že `nullptr` lze použít jako parametr funkce.  
  
```  
// mcpp_nullptr_4.cpp  
// compile with: /clr  
using namespace System;  
void f(Object ^ x) {  
   Console::WriteLine("test");  
}  
  
int main() {  
   f(nullptr);  
}  
```  
  
 **Output**  
  
```Output  
test  
```  
  
## <a name="example"></a>Příklad  
 **Příklad**  
  
 Následující příklad kódu ukazuje, že když popisovače deklarovat a není explicitně inicializován, jsou výchozí inicializována tak, aby `nullptr`.  
  
```  
// mcpp_nullptr_5.cpp  
// compile with: /clr  
using namespace System;  
ref class MyClass {  
public:  
   void Test() {  
      MyClass ^pMyClass;   // gc type  
      if (pMyClass == nullptr)  
         Console::WriteLine("NULL");  
   }  
};  
  
int main() {  
   MyClass ^ x = gcnew MyClass();  
   x -> Test();  
}  
```  
  
 **Output**  
  
```Output  
NULL  
```  
  
## <a name="example"></a>Příklad  
 **Příklad**  
  
 Následující příklad kódu ukazuje, že `nullptr` lze přiřadit k nativní ukazatel při kompilaci s **/CLR**.  
  
```  
// mcpp_nullptr_6.cpp  
// compile with: /clr  
int main() {  
   int * i = 0;  
   int * j = nullptr;  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: (není povinná, podporuje všechny možnosti generování kódu, včetně **/ZW** a **/CLR**)  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)   
 [nullptr](../cpp/nullptr.md)