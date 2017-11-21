---
title: atribut | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.attribute
dev_langs: C++
helpviewer_keywords:
- __typeof keyword
- custom attributes, creating
- attribute attribute
- attributes [C++], custom
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6d5233e5b3f2a27fc821c786d99cb3d996e5c039
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="attribute"></a>– atribut
Umožňuje vytvořit vlastní atribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ attribute(  
   AllowOn,  
   AllowMultiple=boolean,  
   Inherited=boolean  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *AllowOn*  
 Určuje jazyk prvky, na které můžete použít vlastní atribut. Výchozí hodnota je **System::AttributeTargets::All** (viz [System::AttributeTargets](https://msdn.microsoft.com/en-us/library/system.attributetargets.aspx)).  
  
 `AllowMultiple`  
 Určuje, zda vlastní atribut můžete opakovaně použít pro konstrukt. Výchozí hodnota je **FALSE**.  
  
 `Inherited`  
 Značí, zda atribut převezmou podtřídy. Kompilátor poskytuje žádné speciální podporu pro tuto funkci; Úloha atribut příjemců (třeba reflexe) je dodržovat tyto informace. Pokud `Inherited` je **TRUE**, zdědí atribut. Pokud `AllowMultiple` je **TRUE**, atribut budou se hromadit na odvozené člen; Pokud `AllowMultiple` je **FALSE**, atribut bude přepsat (nebo nahradit) v dědičnosti. Pokud `Inherited` je **FALSE**, nebude možné zdědit atribut. Výchozí hodnota je **TRUE**.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  `attribute` Atribut je nyní zastaralý.  Běžné language runtime atribut System.Attribute k přímo použijte k vytvoření attirbutes definovaný uživatelem.  Další informace najdete v tématu [uživatelem definované atributy](../windows/user-defined-attributes-cpp-component-extensions.md).  
  
 Můžete definovat [vlastní atribut](../windows/custom-attributes-cpp.md) tím, že `attribute` atribut na spravované definici třídě nebo struktuře. Název třídy je vlastní atribut. Příklad:  
  
```  
[ attribute(Parameter) ]  
public ref class MyAttr {};  
```  
  
 definuje atribut nazvaný MyAttr, který lze použít na parametry funkce. Třída musí být veřejné, pokud atribut má použít v jiné sestavení.  
  
> [!NOTE]
>  Pokud chcete zabránit kolize názvů, všechny názvy atributů implicitně končit "Atribut"; v tomto příkladu název atributu a třída je ve skutečnosti MyAttrAttribute, ale MyAttr a MyAttrAttribute zaměnitelné.  
  
 Veřejné konstruktory třídy definují atributu nepojmenované parametry. Přetížené konstruktory povolit více způsobů určení atribut, aby vlastní atribut, který je definován následujícím způsobem:  
  
```  
// cpp_attr_ref_attribute.cpp  
// compile with: /c /clr  
using namespace System;  
[ attribute(AttributeTargets::Class) ]   // apply attribute to classes  
public ref class MyAttr {  
public:  
   MyAttr() {}   // Constructor with no parameters  
   MyAttr(int arg1) {}   // Constructor with one parameter  
};  
  
[MyAttr]  
ref class ClassA {};   // Attribute with no parameters  
  
[MyAttr(123)]  
ref class ClassB {};   // Attribute with one parameter  
```  
  
 Veřejná data členy třídy a vlastnosti jsou volitelné parametry s názvem atributu:  
  
```  
// cpp_attr_ref_attribute_2.cpp  
// compile with: /c /clr  
using namespace System;  
[ attribute(AttributeTargets::Class) ]  
ref class MyAttr {  
public:  
   // Property Priority becomes attribute's named parameter Priority  
    property int Priority {  
       void set(int value) {}  
       int get() { return 0;}  
   }  
   // Data member Version becomes attribute's named parameter Version  
   int Version;  
   MyAttr() {}   // constructor with no parameters  
   MyAttr(int arg1) {}   // constructor with one parameter  
};  
  
[MyAttr(123, Version=2)]   
ref class ClassC {};  
```  
  
 Seznam typů parametr možné atributů najdete v tématu [vlastní atributy](../windows/custom-attributes-cpp.md).  
  
 V tématu [uživatelem definované atributy](../windows/user-defined-attributes-cpp-component-extensions.md) podrobné informace o cíle atributů.  
  
 `attribute` Atribut má `AllowMultiple` parametr, který určuje, zda je vlastní atribut jedno použití nebo multiuse (může vyskytovat více než jednou u stejné entity).  
  
```  
// cpp_attr_ref_attribute_3.cpp  
// compile with: /c /clr  
using namespace System;  
[ attribute(AttributeTargets::Class, AllowMultiple = true) ]  
ref struct MyAttr {  
   MyAttr(){}  
};   // MyAttr is a multiuse attribute  
  
[MyAttr, MyAttr()]  
ref class ClassA {};  
```  
  
 Vlastní atribut třídy jsou odvozené přímo nebo nepřímo od <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>, které díky Identifikace definice atributu v metadatech rychlé a snadné. `attribute` Atribut znamená dědění ze System::Attribute, takže není nutné explicitní odvození:  
  
```  
[ attribute(Class) ]  
ref class MyAttr  
```  
  
 je ekvivalentem  
  
```  
[ attribute(Class) ]  
ref class MyAttr : System::Attribute   // OK, but redundant.  
```  
  
 `attribute`je alias <xref:System.AttributeUsageAttribute?displayProperty=fullName> (ne atributAtribut; Toto je výjimka do atribut pravidla pojmenování).  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`ref`**třída**, **ref struct**|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="example"></a>Příklad  
  
```  
// cpp_attr_ref_attribute_4.cpp  
// compile with: /c /clr  
using namespace System;  
[attribute(AttributeTargets::Class)]  
ref struct ABC {  
   ABC(Type ^) {}  
};  
  
[ABC(String::typeid)]   // typeid operator yields System::Type ^  
ref class MyClass {};  
```  
  
## <a name="example"></a>Příklad  
 `Inherited` Pojmenovaný argument určuje, zda vlastní atribut použít na základní třídě se zobrazí na reflexi odvozené třídy.  
  
```  
// cpp_attr_ref_attribute_5.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Reflection;  
  
[attribute( AttributeTargets::Method, Inherited=false )]  
ref class BaseOnlyAttribute { };  
  
[attribute( AttributeTargets::Method, Inherited=true )]  
ref class DerivedTooAttribute { };  
  
ref struct IBase {  
public:  
   [BaseOnly, DerivedToo]  
   virtual void meth() {}  
};  
  
// Reflection on Derived::meth will show DerivedTooAttribute   
// but not BaseOnlyAttribute.  
ref class Derived : public IBase {  
public:  
   virtual void meth() override {}  
};  
  
int main() {  
   IBase ^ pIB = gcnew Derived;  
  
   MemberInfo ^ pMI = pIB->GetType( )->GetMethod( "meth" );  
   array<Object ^> ^ pObjs = pMI->GetCustomAttributes( true );  
   Console::WriteLine( pObjs->Length ) ;  
}  
```  
  
```Output  
2  
```  
  
## <a name="see-also"></a>Viz také  
 [Abecedně řazená referenční dokumentace k atributům](../windows/attributes-alphabetical-reference.md)   
 [Vlastní atributy](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)