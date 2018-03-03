---
title: "Postupy: deklarace obslužných rutin v nativních typech | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- gcroot
dev_langs:
- C++
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 097889acd9a77cea5e0a81dd3bd13be712a70550
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-declare-handles-in-native-types"></a>Postupy: Deklarace obslužných rutin v nativních typech
Typ popisovače v nativním typu nelze deklarovat. Vcclr.h poskytuje šablony bezpečnost typů obálku `gcroot` odkazovat na objekt CLR z haldy jazyka C++. Tato šablona umožňuje vložit virtuální popisovač v nativním typu a s nimi zacházet jako by šlo podkladovým typem. Ve většině případů můžete použít `gcroot` objektu jako vložený typ bez žádné přetypování. Nicméně s [, v](../dotnet/for-each-in.md), budete muset použít `static_cast` načíst odkaz na základní spravovaný.  
  
 `gcroot` Šablony je implementovaná pomocí zařízení hodnota třídy System::Runtime, který poskytuje "popisovače" do haldy uvolňování paměti. Všimněte si, že popisovače samy o sobě nejsou uvolnění z paměti a jsou uvolněny už v použití destruktoru ve `gcroot` – třída (Tento destruktor nelze volat ručně). Pokud vytvoříte instanci `gcroot` objekt v nativní haldy, musí volat odstraníte tento prostředek.  
  
 Modul runtime bude udržovat přidružení mezi popisovač a objekt CLR, který odkazuje. Pokud se objekt CLR se přesune s haldě uvolňování paměti, popisovač vrátí novou adresu objektu. Proměnná nemá být připojena před je přiřazena k `gcroot` šablony.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje postup vytvoření `gcroot` objekt v nativní zásobníku.  
  
```  
// mcpp_gcroot.cpp  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
class CppClass {  
public:  
   gcroot<String^> str;   // can use str as if it were String^  
   CppClass() {}  
};  
  
int main() {  
   CppClass c;  
   c.str = gcnew String("hello");  
   Console::WriteLine( c.str );   // no cast required  
}  
```  
  
```Output  
hello  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje postup vytvoření `gcroot` objekt v nativní haldě.  
  
```  
// mcpp_gcroot_2.cpp  
// compile with: /clr  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
struct CppClass {  
   gcroot<String ^> * str;  
   CppClass() : str(new gcroot<String ^>) {}  
  
   ~CppClass() { delete str; }  
  
};  
  
int main() {  
   CppClass c;  
   *c.str = gcnew String("hello");  
   Console::WriteLine( *c.str );  
}  
```  
  
```Output  
hello  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje způsob použití `gcroot` pro udržení odkazů na typy hodnot (ne odkazové typy) v nativním typu pomocí `gcroot` na zabalené typu.  
  
```  
// mcpp_gcroot_3.cpp  
// compile with: /clr  
#include < vcclr.h >  
using namespace System;  
  
public value struct V {  
   String^ str;  
};  
  
class Native {  
public:  
   gcroot< V^ > v_handle;  
};  
  
int main() {  
   Native native;  
   V v;  
   native.v_handle = v;  
   native.v_handle->str = "Hello";  
   Console::WriteLine("String in V: {0}", native.v_handle->str);  
}  
```  
  
```Output  
String in V: Hello  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)