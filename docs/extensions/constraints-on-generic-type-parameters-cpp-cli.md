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
ms.openlocfilehash: be5af8f6b2edaa8f93fef7ae06b2175b54b25396
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172475"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>Omezení obecných parametrů typů (C++/CLI)

V deklaracích obecného typu nebo metody můžete kvalifikovat parametr typu s omezeními. Omezení je požadavek, aby typy používané jako argumenty typu splňovaly požadavky. Omezení například může být, že argument typu musí implementovat určité rozhraní nebo zdědit z konkrétní třídy.

Omezení jsou volitelná; Nezadání omezení pro parametr je ekvivalentní k omezení tohoto parametru na <xref:System.Object>.

## <a name="syntax"></a>Syntaxe

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>Parametry

*typ – parametr*<br/>
Jeden z parametrů typu, který má být omezen.

*seznam omezení*<br/>
*seznam omezení* je čárkami oddělený seznam specifikací omezení. Seznam může obsahovat rozhraní, která mají být implementována parametrem typu.

Seznam může obsahovat také třídu. Pro argument typu pro splnění omezení základní třídy musí být stejná třída jako omezení nebo odvozena z omezení.

Můžete také zadat **gcnew ()** označující, že argument typu musí mít veřejný konstruktor bez parametrů; nebo **ref class** k označení argumentu typu musí být odkazový typ, včetně libovolné třídy, rozhraní, delegáta nebo typu pole; nebo **Třída hodnoty** k označení argumentu typu musí být typ hodnoty. Dá se zadat libovolný typ hodnoty kromě Nullable\<T >.

Můžete také zadat obecný parametr jako omezení. Argument typu zadaný pro typ, který je omezen, musí být nebo odvozen od typu omezení. Toto omezení se nazývá holého typu.

## <a name="remarks"></a>Poznámky

Klauzule omezení se skládá z **WHERE** následovaný parametrem typu, dvojtečkou ( **:** ) a omezením, které určuje povahu omezení u parametru typu. **kde** je klíčové slovo závislé na kontextu; Další informace najdete v tématu [Kontextově závislá klíčová slova](context-sensitive-keywords-cpp-component-extensions.md) . Oddělte více klauzulí **WHERE** s mezerou.

Omezení se použijí pro parametry typu k omezení typů, které lze použít jako argumenty pro obecný typ nebo metodu.

Omezení třídy a rozhraní určují, že typy argumentů musí být nebo zděděné ze zadané třídy nebo implementovat zadané rozhraní.

Použití omezení na obecný typ nebo metodu umožňuje kódu v tomto typu nebo metodě využít známé funkce omezených typů. Například můžete deklarovat obecnou třídu tak, že parametr typu implementuje rozhraní `IComparable<T>`:

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

Toto omezení vyžaduje, aby argument typu používaného pro `T` implementoval `IComparable<T>` v době kompilace. Umožňuje také volání metod rozhraní, jako je například `CompareTo`. Pro instanci parametru typu pro volání metod rozhraní není vyžadováno žádné přetypování.

Statické metody v třídě argumentu typu nelze volat prostřednictvím parametru typu. mohou být volány pouze pomocí skutečného pojmenovaného typu.

Omezení nemůže být typ hodnoty, včetně předdefinovaných typů, jako je **int** nebo **Double**. Vzhledem k tomu, že typy hodnot nemohou mít odvozené třídy, může být někdy možné vyhovět pouze jedné třídě. V takovém případě lze obecný typ přepsat parametrem typu nahrazeným konkrétním typem hodnoty.

Omezení jsou vyžadována v některých případech, protože kompilátor nepovoluje použití metod nebo jiných funkcí neznámého typu, pokud omezení nezpůsobí, že neznámý typ podporuje metody nebo rozhraní.

V seznamu odděleném čárkami se dá zadat víc omezení pro stejný parametr typu.

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

S více parametry typu použijte jednu klauzuli **WHERE** pro každý parametr typu. Příklad:

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

Pro Shrnutí použijte omezení v kódu podle následujících pravidel:

- Pokud je uvedeno více omezení, mohou být omezení uvedena v libovolném pořadí.

- Omezení mohou být také typy třídy, jako jsou abstraktní základní třídy. Omezení ale nemůžou být typy hodnot ani zapečetěné třídy.

- Omezení nemohou být samotnými parametry typu, ale mohou zahrnovat parametry typu v otevřeném konstruovaném typu. Příklad:

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

Následující příklad ukazuje použití omezení pro volání metod instancí v parametrech typu.

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

Pokud je parametr obecného typu použit jako omezení, nazývá se omezení holého typu. Omezení holého typu jsou užitečná, pokud členská funkce s vlastním parametrem typu musí omezit tento parametr na parametr typu nadřazeného typu.

V následujícím příkladu je `T` omezení holého typu v kontextu metody `Add`.

Omezení holého typu lze také použít v definicích obecných tříd. Užitečnost omezení typu holého typu s obecnými třídami je omezená, protože kompilátor nepředpokládá nic o omezení holého typu s tím rozdílem, že je odvozen z <xref:System.Object>. Používejte omezení holého typu u obecných tříd ve scénářích, ve kterých chcete vynutit vztah dědičnosti mezi dvěma parametry typu.

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
