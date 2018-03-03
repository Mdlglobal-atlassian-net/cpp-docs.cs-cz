---
title: "Prostředí Windows Runtime a spravované šablony (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81e803db04ebd9d3a851a04e8656131d85649751
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windows-runtime-and-managed-templates-c-component-extensions"></a>Windows Runtime a spravované šablony (rozšíření komponent C++)
Šablony umožňují definovat prototyp prostředí Windows Runtime nebo běžné typ modulu runtime jazyka a potom vytvořte instanci daného typu variant pomocí parametrů typu jinou šablonu.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 Můžete vytvořit šablony z typů hodnotu nebo odkaz.  Další informace o vytváření hodnotu nebo odkaz typy najdete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md).  
  
 Další informace o standardní šablony třídy C++ najdete v tématu [šablony třídy](../cpp/class-templates.md).  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 (Existují žádné poznámky pro tuto funkci jazyka, která se týkají jenom prostředí Windows Runtime).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime)  
 K vytvoření šablony třídy ze spravovaných typů, které je ukázán v následujících příkladech kódu existují určitá omezení.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Je možné vytvořit instanci obecného typu pomocí parametru šablony spravovaného typu, ale nelze vytvořit instanci spravovaného šablonu s parametru šablony obecného typu.  Toto je, protože obecné typy jsou vyřešeny za běhu.  Další informace najdete v tématu [obecné typy a šablony (Visual C++)](../windows/generics-and-templates-visual-cpp.md).  
  
```cpp  
// managed_templates.cpp  
// compile with: /clr /c  
  
generic<class T>   
ref class R;   
  
template<class T>   
ref class Z {  
   // Instantiate a generic with a template parameter.  
   R<T>^ r;    // OK  
};  
  
generic<class T>   
ref class R {  
   // Cannot instantiate a template with a generic parameter.  
   Z<T>^ z;   // C3231  
};  
```  
  
 **Příklad**  
  
 Obecného typu nebo funkce nemůže být vnořena ve spravované šablony.  
  
```cpp  
// managed_templates_2.cpp  
// compile with: /clr /c  
  
template<class T> public ref class R {  
   generic<class T> ref class W {};   // C2959  
};  
```  
  
 **Příklad**  
  
 Nelze získat přístup šablony definovaných v odkazované sestavení s C + +/ CLI syntaxe jazyka, ale můžete použít reflexe.  Pokud není vytvořit instanci šablony, není vygenerované v metadatech.  Šablonu je vytvořena, zobrazí se pouze odkazované členské funkce v metadatech.  
  
```cpp  
// managed_templates_3.cpp  
// compile with: /clr  
  
// Will not appear in metadata.  
template<class T> public ref class A {};  
  
// Will appear in metadata as a specialized type.  
template<class T> public ref class R {  
public:  
   // Test is referenced, will appear in metadata  
   void Test() {}  
  
   // Test2 is not referenced, will not appear in metadata  
   void Test2() {}  
};  
  
// Will appear in metadata.  
generic<class T> public ref class G { };  
  
public ref class S { };  
  
int main() {  
   R<int>^ r = gcnew R<int>;  
   r->Test();  
}  
```  
  
 **Příklad**  
  
 Spravované Modifikátor třídy v částečná specializace nebo explicitní specializace šablon třídy, můžete změnit.  
  
```cpp  
// managed_templates_4.cpp  
// compile with: /clr /c  
  
// class template  
// ref class  
template <class T>  
ref class A {};  
  
// partial template specialization  
// value type  
template <class T>  
value class A <T *> {};  
  
// partial template specialization  
// interface  
template <class T>   
interface class A<T%> {};  
  
// explicit template specialization  
// native class  
template <>  
class A <int> {};  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)