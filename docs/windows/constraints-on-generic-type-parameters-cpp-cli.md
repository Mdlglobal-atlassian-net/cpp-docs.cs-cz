---
title: Omezení obecných parametrů typů (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- where
dev_langs:
- C++
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9787eb87ab701d067762a436d92b2fba3fabcbb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883339"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>Omezení obecných parametrů typů (C++/CLI)
Obecný typ nebo metoda deklarace kvalifikovat parametr typu s omezeními. Omezení je požadavek, který musí splňovat typy používané jako argumenty typu. Například omezení může být, že argument typu musí implementovat určité rozhraní nebo konkrétní třídy dědí.  
  
 Omezení jsou volitelné. bez zadání omezení parametr je ekvivalentní chovaly tohoto parametru <xref:System.Object>.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
where type-parameter: constraint list  
```  
  
#### <a name="parameters"></a>Parametry  
 *parametr typu*  
 Jeden z parametrů typu, chcete-li být omezené.  
  
 *seznam omezení*  
 *seznam omezení* je čárkami oddělený seznam omezení specifikace. Tento seznam může obsahovat rozhraní má být implementováno atributy parametr typu.  
  
 Tento seznam může obsahovat také třídu. Pro argument typu vyhovět omezení základní třídy musí to být stejnou třídou jako omezení nebo odvozena od omezení.  
  
 Můžete také zadat `gcnew()` znamená argument typu musí mít veřejný konstruktor; nebo `ref class` k označení argument typu musí být odkazového typu, včetně třídu, rozhraní, delegát nebo typ pole; nebo `value class` na označují, že argument typu musí být typ hodnoty. Některé hodnoty typ s výjimkou Nullable\<T > lze zadat.  
  
 Můžete také určit obecný parametr jako omezení. Argument typu pro typ zadaný, že jsou chovaly musí být nebo jsou odvozeny od typu omezení. Tomu se říká holé typ omezení.  
  
## <a name="remarks"></a>Poznámky  
 V klauzuli omezení se skládá z **kde** následuje parametr typu, dvojtečka (**:**) a omezení, která určuje povaha omezení na parametr typu. **kde** je kontextová – klíčové slovo, najdete v části [klíčová slova Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md) Další informace. Oddělte více **kde** klauzule mezerami.  
  
 Omezení se použijí pro parametry umístit omezení na typy, které lze použít jako argumenty pro obecný typ nebo metoda typu.  
  
 Omezení třídy a rozhraní uvést, že typy argumentů musí být nebo zdědit ze zadané třídy nebo zadaný rozhraní implementovat.  
  
 O omezení aplikace pro obecný typ nebo metoda umožňuje kódu v této typ nebo metoda využít výhod funkce známých typů omezené. Například deklarovat obecné třídy tak, aby implementuje parametr typu **IComparable\<T >** rozhraní:  
  
```  
// generics_constraints_1.cpp  
// compile with: /c /clr  
using namespace System;  
generic <typename T>  
where T : IComparable<T>  
ref class List {};  
```  
  
 Toto omezení vyžaduje, aby argument typu nepoužíval pro `T` implementuje `IComparable<T>` v době kompilace. Umožňuje také metody rozhraní, jako například **CompareTo**, která se má volat. Na instanci parametr typu je potřeba žádné přetypování k volání metody rozhraní.  
  
 Statické metody ve třídě argument typu nelze volat pomocí parametru typu; je možné volat pouze prostřednictvím skutečný typ s názvem.  
  
 Omezení nemůže být typu hodnoty, včetně vestavěné typy, jako například `int` nebo **dvojité**. Vzhledem k tomu, že typy hodnot nemohou mít odvozené třídy, by se jenom jedna třída někdy vyhovět omezením v atributu. V takovém případě může být přepsán obecná s parametrem typu nahrazuje typ konkrétní hodnoty.  
  
 V některých případech se vyžadují omezení, protože kompilátor nebude povolovat použití metody nebo jiné funkce neznámého typu, pokud omezení neznamená, že podporuje Neznámý typ metody nebo rozhraní.  
  
 V seznamu textový soubor s oddělovači lze zadat více omezení pro stejný parametr typu  
  
```  
// generics_constraints_2.cpp  
// compile with: /c /clr  
using namespace System;  
using namespace System::Collections::Generic;  
generic <typename T>  
where T : List<T>, IComparable<T>  
ref class List {};  
```  
  
 S více typů parametrů, použijte jednu **kde** klauzuli pro každý typ parametru. Příklad:  
  
```  
// generics_constraints_3.cpp  
// compile with: /c /clr  
using namespace System;  
using namespace System::Collections::Generic;  
  
generic <typename K, typename V>  
   where K: IComparable<K>  
   where V: IComparable<K>  
ref class Dictionary {};  
```  
  
 To Shrneme, použijte omezení ve vašem kódu podle následujících pravidel:  
  
-   Pokud nejsou uvedeny více omezení, omezení nemusí být zobrazeny v libovolném pořadí.  
  
-   Omezení může být také typy tříd, jako je například abstraktní základní třídy. Omezení však nelze typy hodnot nebo zapečetěné třídy.  
  
-   Sami omezení nemůže být parametry typu, ale zahrnují parametry typu v otevřeném typu vytvořený. Příklad:  
  
    ```  
    // generics_constraints_4.cpp  
    // compile with: /c /clr  
    generic <typename T>  
    ref class G1 {};  
  
    generic <typename Type1, typename Type2>  
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter  
    ref class G2{};  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití omezení pro volání metody instance na parametry typu.  
  
```  
// generics_constraints_5.cpp  
// compile with: /clr  
using namespace System;  
  
interface class IAge {  
   int Age();  
};  
  
ref class MyClass {  
public:  
   generic <class ItemType> where ItemType : IAge   
   bool isSenior(ItemType item) {  
      // Because of the constraint,  
      // the Age method can be called on ItemType.  
      if (item->Age() >= 65)   
         return true;  
      else  
         return false;  
   }  
};  
  
ref class Senior : IAge {  
public:  
   virtual int Age() {  
      return 70;  
   }  
};  
  
ref class Adult: IAge {  
public:  
   virtual int Age() {  
      return 30;  
   }  
};  
  
int main() {  
   MyClass^ ageGuess = gcnew MyClass();  
   Adult^ parent = gcnew Adult();  
   Senior^ grandfather = gcnew Senior();  
  
   if (ageGuess->isSenior<Adult^>(parent))  
      Console::WriteLine("\"parent\" is a senior");  
   else  
      Console::WriteLine("\"parent\" is not a senior");  
  
   if (ageGuess->isSenior<Senior^>(grandfather))  
      Console::WriteLine("\"grandfather\" is a senior");  
   else  
      Console::WriteLine("\"grandfather\" is not a senior");  
}  
```  
  
```Output  
"parent" is not a senior  
"grandfather" is a senior  
```  
  
## <a name="example"></a>Příklad  
 Pokud je jako omezení použit parametr obecného typu, nazývá holé typ omezení. Omezení typu holé jsou užitečné, pokud členské funkce s vlastní parametr typu je potřeba omezit tento parametr pro parametr typu nadřazeného typu.  
  
 V následujícím příkladu je T omezení holé typu v kontextu metodu Add.  
  
 Omezení typu holé mohou sloužit také v definicích – obecná třída. Užitečnost holé typu omezení s obecné třídy je omezená, protože kompilátor můžete předpokládat nic o omezení holé typu s tím rozdílem, že je odvozena z <xref:System.Object>. Použijte omezení holé typu obecné třídy ve scénářích, ve kterých chcete vynutit vztah dědičnosti mezi dvěma parametry typu.  
  
```  
// generics_constraints_6.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct List {  
   generic <class U>  
   where U : T  
   void Add(List<U> items)  {}  
};  
  
generic <class A, class B, class C>  
where A : C  
ref struct SampleClass {};  
```  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy](../windows/generics-cpp-component-extensions.md)