---
title: Změny v sémantice destruktorů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- finalizers [C++]
- destructors, C++
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c25045291afed1e8072867ee668716b2f396ef30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420020"
---
# <a name="changes-in-destructor-semantics"></a>Změny v sémantice destruktorů

Sémantika pro destruktory třídy změnily výrazně ze spravovaného rozšíření jazyka C++ pro Visual C++.

Ve spravovaných rozšíření byla povolené destruktor třídy v rámci referenční třídy, ale není v hodnotové třídě. To nedošlo ke změně v nové syntaxi. Změnily se ale sémantiky destruktoru třídy. Toto téma se zaměřuje na důvody, proč, změnit a popisuje, jak ovlivňuje překladu existujícího kódu modulu CLR. Je pravděpodobně nejdůležitější změny programátor úrovni mezi oběma verzemi jazyka.

## <a name="non-deterministic-finalization"></a>Deterministické dokončení

Předtím, než paměť přidružená k objektu je uvolněn systémem uvolňování paměti, přidružené `Finalize` metodu, pokud jsou k dispozici, je vyvolána. Můžete představit jako druh nadtypem destruktor tuto metodu, protože není vázaný na program životnosti objektu. Označujeme to jako finalizace. Načasování pouze při nebo dokonce, jestli `Finalize` vyvolání metody není definován. Tím je myšleno, když říkáme, že uvolňování paměti vykazuje nedeterministické dokončení.

Nedeterministické dokončení pracuje s dynamickou pamětí správy. Jakmile je dostupná paměť vzácné, uvolňování paměti. V části uvolňování paměti shromažďují prostředí, destruktory pro uvolnění paměti nejsou potřeba. Nedeterministické dokončení nefunguje dobře, ale pokud objekt udržuje důležitých prostředků jako je například připojení k databázi nebo jenom některé řazení. V takovém případě by měl vydáváme tento prostředek co nejdříve. Nativní světě, který se dosahuje pomocí dvojice konstruktor nebo destruktor. Co nejdříve po skončení životnosti objektu při ukončení místní bloku, ve kterém je deklarována, nebo když zásobník automatiky z důvodu výjimky, destruktor, a prostředek je automaticky uvolněn. Tento přístup dobře funguje, a jeho absenci v rámci spravovaného rozšíření byla opomíjená.

Řešení poskytuje modul CLR je pro třídu pro implementaci `Dispose` metodu `IDisposable` rozhraní. Problémem je, že `Dispose` vyžaduje explicitního volání uživatelem. Toto je náchylné k chybě. Jazyk C# poskytuje mírné formu automatizace ve formě speciální `using` příkazu. Návrh spravovaných rozšíření k dispozici žádné speciální podporu.

## <a name="destructors-in-managed-extensions-for-c"></a>Destruktory v spravovaná rozšíření pro C++

Ve spravovaných rozšíření destruktor třídy odkazu implementovaná pomocí následujících dvou kroků:

1. Zadaný uživatel destruktor je přejmenován na interně `Finalize`. Pokud má třída základní třídu (mějte na paměti, v rámci modelu objektu CLR je podporována pouze jedna dědičnost), kompilátor vkládá volání jeho finalizační uživatelský kód. Představte si třeba následující jednoduchý hierarchie z specifikaci spravovaného rozšíření jazyka:

```
__gc class A {
public:
   ~A() { Console::WriteLine(S"in ~A"); }
};

__gc class B : public A {
public:
   ~B() { Console::WriteLine(S"in ~B");  }
};
```

V tomto příkladu jsou oba destruktory přejmenované `Finalize`. `B`společnosti `Finalize` má vyvolání `A`společnosti `Finalize` přidána metoda po vyvolání `WriteLine`. Je to, co systému uvolňování paměti se ve výchozím nastavení má volat během finalizace. Zde je, jak může vypadat toto vnitřní transformace:

```
// internal transformation of destructor under Managed Extensions
__gc class A {
public:
   void Finalize() { Console::WriteLine(S"in ~A"); }
};

__gc class B : public A {
public:
   void Finalize() {
      Console::WriteLine(S"in ~B");
      A::Finalize();
   }
};
```

1. V druhém kroku kompilátor syntetizuje virtuální destruktor. Tento destruktor je, co naše aplikace uživatele spravovaného rozšíření vyvolat přímo nebo prostřednictvím aplikace výraz delete. Nikdy není vyvolán modulem garbage collector.

     Dva příkazy jsou umístěny v rámci této syntetizovaný destruktor. Jeden je volání `GC::SuppressFinalize` abyste měli jistotu, že neexistují žádné další vyvolání `Finalize`. Druhým je skutečná vyvolání `Finalize`, která představuje destruktoru uživatelem zadaný pro danou třídu. Zde je, jak to může vypadat:

```
__gc class A {
public:
   virtual ~A() {
      System::GC::SuppressFinalize(this);
      A::Finalize();
   }
};

__gc class B : public A {
public:
   virtual ~B() {
      System::GC::SuppressFinalize(this);
      B::Finalize();
   }
};
```

Zatímco tato implementace umožňuje uživateli explicitně vyvolat třídy `Finalize` – metoda nyní spíše než v době nemáte žádnou kontrolu nad ji opravdu nestačí se `Dispose` metoda řešení. V jazyce Visual C++ je toto nastavení změnit.

## <a name="destructors-in-new-syntax"></a>Destruktory v nové syntaxi

V nové syntaxi destruktoru je přejmenován na interně `Dispose` metoda a referenční třída je automaticky rozšířena k implementaci `IDispose` rozhraní. To znamená v rámci jazyka Visual C++, naše dvojice tříd se transformuje následujícím způsobem:

```
// internal transformation of destructor under the new syntax
__gc class A : IDisposable {
public:
   void Dispose() {
      System::GC::SuppressFinalize(this);
      Console::WriteLine( "in ~A");
   }
};

__gc class B : public A {
public:
   void Dispose() {
      System::GC::SuppressFinalize(this);
      Console::WriteLine( "in ~B");
      A::Dispose();
   }
};
```

Když buď destruktoru volány explicitně v nové syntaxi, nebo když `delete` platí pro sledovací popisovač, základní `Dispose` je automaticky vyvolána metoda. Pokud je odvozená třída je volání `Dispose` metody základní třídy bude vložena na konec syntetizovaný metody.

Ale to není nám narostl až deterministické dokončení. Aby bylo možné dosáhnout, budeme potřebovat další podporu místní odkazů na objekty. (Tato akce nemá žádné obdobná podpory v rámci spravovaného rozšíření, a to není problém s překladem.)

## <a name="declaring-a-reference-object"></a>Deklarace objektu referenční dokumentace

Jazyk Visual C++ podporuje deklarace objektu referenční třídy v místní zásobníku nebo jako člen třídy, jako kdyby byly přímo přístupné. V kombinaci s přidružení destruktor s `Dispose` metoda, výsledek je automatické vyvolání finalizace sémantiky pro referenční typy.

Nejprve jsme naše referenční třídy definujte tak, že vytvoření objektu funguje jako pořízení prostředků prostřednictvím konstruktoru třídy. Za druhé v rámci destruktor třídy vydáváme prostředků získané při vytvoření objektu.

```
public ref class R {
public:
   R() { /* acquire expensive resource */ }
   ~R() { /* release expensive resource */ }

   // everything else...
};
```

Objekt je deklarovaná místně pomocí názvu typu, ale bez doprovodnou hat. Všechna použití objektu, například volání metody, jsou prováděny prostřednictvím tečkou výběru člena (`.`) namísto šipka (`->`). Na konci bloku přidruženým destruktorem transformuje na `Dispose`, je vyvolán automaticky, jak je znázorněno zde:

```
void f() {
   R r;
   r.methodCall();

   // r is automatically destructed here -
   // that is, r.Dispose() is invoked
}
```

Stejně jako u `using` příkazu v C#, nebude toto porušovat základní CLR omezení, že všechny typy odkazů musí být přidělený k haldě modulu CLR. Základní sémantika zůstává beze změny. Uživatel může ekvivalentně napsat následující (a to je pravděpodobně vnitřní transformace provedené kompilátorem za):

```
// equivalent implementation
// except that it should be in a try/finally clause
void f() {
   R^ r = gcnew R;
   r->methodCall();

   delete r;
}
```

V důsledku toho v nové syntaxi, destruktory jsou znovu spárovat s konstruktory jako automatické získání nebo vydání mechanismu spojený s místní objekt životnost.

## <a name="declaring-an-explicit-finalize"></a>Deklarace explicitního dokončení

V nové syntaxi, jak jsme viděli, destruktor je syntetizovat do `Dispose` metody. To znamená, že když destruktor není vyvolán explicitně, systému uvolňování paměti během finalizace, stejně jako předtím nenajde přidružené `Finalize` metody pro objekt. Pro podporu zničení a dokončení, zavedli jsme zvláštní syntaxi pro poskytování finalizační metodu. Příklad:

```
public ref class R {
public:
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }
};
```

`!` Předpona je obdobou tilda (`~`), který představuje destruktor třídy – to znamená, že obě metody po dobu života mají token předpony názvu třídy. Pokud syntetizovaný `Finalize` metoda vyskytuje v odvozené třídě, vyvolání této základní třídy `Finalize` metoda disku do mechaniky na jeho konci. Pokud je destruktor je explicitně vyvolána, je potlačeno finalizační metodu. Zde je, jak může vypadat transformace:

```
// internal transformation under new syntax
public ref class R {
public:
   void Finalize() {
      Console::WriteLine( "I am the R::finalizer()!" );
   }
};
```

## <a name="moving-from-managed-extensions-for-c-to-visual-c-2010"></a>Přesunutí ze spravovaného rozšíření jazyka C++ pro Visual C++ 2010

Chování za běhu spravovaných rozšíření pro C++ program se změní při kompilaci v rámci jazyka Visual C++ pokaždé, když se referenční třída obsahuje netriviální destruktor. Algoritmus vyžaduje překladu je podobný následujícímu:

1. Pokud je k dispozici destruktor, přepíše se finalizační metodu třídy.

1. Pokud `Dispose` metoda je k dispozici, přepsání, která do destruktor třídy.

1. Pokud destruktor je k dispozici, ale neexistuje žádná `Dispose` metoda, zachovat destruktor při provádění první položky.

Při přesouvání kódu ze spravovaných rozšíření novou syntaxi, můžete přijít o provádění této transformace. Pokud aplikace je nějakým způsobem závisí na spuštění přidružených finalizační metody, chování aplikace se než ty, které jste zamýšleli.

## <a name="see-also"></a>Viz také

[Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Destruktory a finalizační metody v tom, jak: definice a používání tříd a struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)