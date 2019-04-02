---
title: Omezení obecných parametrů typů (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- where
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
ms.openlocfilehash: b2ea8c495d45ce465c2f3d960861a016ad618bc2
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786667"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>Omezení obecných parametrů typů (C++/CLI)

V obecném typu nebo deklarace metody se můžete kvalifikovat parametr typu s omezeními. Omezení je požadavek, který musí splňovat typy použité jako argumenty typu. Omezení může být například, že argument typu musí implementovat určité rozhraní nebo dědí určité třídy.

Omezení jsou volitelné. bez zadání omezení pro parametr je ekvivalentní k omezení pro tento parametr <xref:System.Object>.

## <a name="syntax"></a>Syntaxe

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>Parametry

*parametr typu*<br/>
Jeden z parametrů typu, chcete-li být omezený.

*seznam omezení*<br/>
*seznam omezení* je čárkou oddělený seznam omezení specifikací. Tento seznam může obsahovat rozhraní k implementaci parametr typu.

Tento seznam může také obsahovat třídu. Pro argument typu pro omezení základní třídy se musí být stejné třídy jako omezení nebo jsou odvozeny z omezení.

Můžete také určit **gcnew()** k označení, že argument typu musí mít veřejný konstruktor bez parametrů; nebo **třídy ref class** k označení, že argument typu musí být typ odkazu, včetně všechny třídy, rozhraní, delegáta nebo typ pole; nebo **hodnotu třídy** uvést typ argumentu musí být typem hodnoty. Některá hodnota typu s výjimkou Nullable\<T > je možné zadat.

Můžete také zadat obecný parametr jako omezení. Argument typu zadaný pro typ, že jsou omezení musí být nebo odvozen od typu omezení. Tomu se říká omezení holého typu.

## <a name="remarks"></a>Poznámky

Klauzule omezení se skládá z **kde** za nímž následuje parametr typu, dvojtečkou (**:**) a omezení, která určuje druh tohoto omezení na parametr typu. **kde** je kontextové klíčové slovo; viz [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md) Další informace. Oddělit více **kde** klauzule mezerou.

Omezení se použijí k zadání parametrů k umístění omezení na typy, které lze použít jako argumenty obecného typu nebo metody.

Omezení rozhraní a třídy určit, že typy argumentů musí být nebo dědí z dané třídy nebo implementovat zadané rozhraní.

Použití omezení do obecného typu nebo metody umožňuje kódu v tomto typu nebo metodě využívat známé funkce omezené typy. Například můžete deklarovat obecné třídy tak, aby parametr typu implementuje `IComparable<T>` rozhraní:

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

Toto omezení vyžaduje, že argument typu použít pro `T` implementuje `IComparable<T>` v době kompilace. Umožňuje také metody rozhraní, jako například `CompareTo`, která se má volat. Nepoužívat přetypování je potřeba na instanci parametr typu pro volání metody rozhraní.

Statické metody ve třídě argument typu nelze volat pomocí parametru typu; je možné volat jenom prostřednictvím skutečné pojmenovaného typu.

Omezení nemůže být typ hodnoty, včetně předdefinovaných typů, jako například **int** nebo **double**. Protože typy hodnot nemohou mít odvozené třídy, pouze jednu třídu by stále moct omezení. V takovém případě může být přepsán obecné s parametrem typu nahrazuje typ konkrétní hodnoty.

V některých případech se vyžadují omezení, protože kompilátor nebude povolit použití metod nebo jiné funkce neznámého typu, pokud omezení znamenají, že podporuje Neznámý typ metody nebo rozhraní.

V seznamu odděleném čárkami se dá nastavit několik omezení pro stejný parametr typu

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

S více typy parametrů, použijte jednu **kde** klauzuli pro každý parametr typu. Příklad:

```cpp
// generics_constraints_3.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;

generic <typename K, typename V>
   where K: IComparable<K>
   where V: IComparable<K>
ref class Dictionary {};
```

Souhrnně řečeno, použijte omezení v kódu podle následujících pravidel:

- Pokud nejsou uvedeny více omezení, omezení může být uvedena v libovolném pořadí.

- Omezení může být také typy tříd, jako je například abstraktní základní třídy. Omezení nemůže však být typy hodnot nebo zapečetěné třídy.

- Omezení nemůže být samy parametry typu, ale zahrnují parametry typu v otevřeném typu vytvořený. Příklad:

    ```cpp
    // generics_constraints_4.cpp
    // compile with: /c /clr
    generic <typename T>
    ref class G1 {};

    generic <typename Type1, typename Type2>
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter
    ref class G2{};
    ```

## <a name="example"></a>Příklad

Následující příklad ukazuje použití omezení k volání metody instance u parametrů typu.

```cpp
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

Je-li parametr obecného typu se používá jako omezení, nazývá základní typ omezení. Základní typ omezení jsou užitečné, pokud členskou funkci s vlastní parametr typu je potřeba omezit tento parametr na parametr typu nadřazeného typu.

V následujícím příkladu `T` je základní typ omezení v kontextu `Add` metody.

Základní typ omezení lze také v definicích obecnou třídu. Užitečnost holého typu omezení pomocí obecných tříd je omezený, protože kompilátor může převzít nic neříká o omezení neviditelných typu s tím rozdílem, že se odvozuje od <xref:System.Object>. Použijte základní typ omezení u obecných tříd ve scénářích, ve kterých chcete vynutit vztah dědičnosti mezi dvěma parametry typu.

```cpp
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

[Obecné typy](generics-cpp-component-extensions.md)