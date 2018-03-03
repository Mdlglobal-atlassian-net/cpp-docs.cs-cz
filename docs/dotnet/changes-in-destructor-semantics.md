---
title: "Změny v sémantice | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- finalizers [C++]
- destructors, C++
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c85ac0b082e8ea1dfbff007a68061e6a286390cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="changes-in-destructor-semantics"></a>Změny v sémantice destruktorů
Sémantika pro destruktory třídy změnily výrazně ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Ve spravovaných rozšíření byl destruktor povoleny v rámci referenční třídy, ale není v rámci třídy hodnotu. To se nezměnilo v nové syntaxe. Změnily se však sémantika destruktoru třídy. Toto téma se zaměřuje na důvody těchto změn a popisuje, jak ovlivňuje překlad existujícího kódu modulu CLR. Je pravděpodobně nejdůležitější změna úrovně programátory mezi dvěma verzemi jazyka.  
  
## <a name="non-deterministic-finalization"></a>Nedeterministické dokončení  
 Předtím, než je paměť přidružená k objektu je uvolnit modulem garbage collector, přiřazený `Finalize` metoda, pokud existuje, je vyvolána. Si můžete představit tato metoda druh nadtypem destruktor vzhledem k tomu, že není vázána k programu doba života objektu. Označujeme jako finalizace k tomuto. Načasování kdy nebo zda `Finalize` je volána metoda není definován. Je to, co jsme znamená, když jsme Řekněme, že uvolňování paměti vykazuje nedeterministické dokončení.  
  
 Nedeterministické dokončení dobře funguje s Správa dynamické paměti. Když se stane omezených dostupné paměti, uvolňování paměti. V části uvolnění paměti shromažďují prostředí destruktory pro uvolnění paměti nejsou potřeba. Nedeterministické dokončení nefunguje správně, ale pokud objekt udržuje kritické prostředků, jako je například připojení k databázi nebo druh zámku. V takovém případě jsme měli tento zdroj uvolnit co nejdříve. Nativní světě, které je dosaženo pomocí pár konstruktor/destruktor. Jakmile skončí doba života objektu, buď když místní bloku, ve kterém je deklarovaná končí, nebo když zásobníku automatiky z důvodu výjimky, destruktor a uvolní prostředek. Tento postup funguje dobře, a jeho nepřítomnost pod spravovaných rozšíření byla příliš opomíjená.  
  
 Řešení, které poskytuje modulu CLR je pro třídu pro implementaci `Dispose` metodu `IDisposable` rozhraní. Problémem je, že `Dispose` vyžaduje explicitní volání uživatelem. Toto je k chybám. Jazyk C# poskytuje mírnou formu automatizace ve formě speciální `using` příkaz. Návrh spravovaných rozšíření neposkytuje žádnou zvláštní podporu.  
  
## <a name="destructors-in-managed-extensions-for-c"></a>Destruktory v spravovaná rozšíření pro C++  
 Ve spravovaných rozšíření je destruktor referenční třídy implementovat pomocí následující dva kroky:  
  
1.  Zadaný uživatel destruktor přejmenován interně na `Finalize`. Pokud třída má základní třídu (Nezapomeňte, že v rámci modelu objektu CLR, je podporována pouze jedna dědičnost), kompilátor vloží volání své finalizační kód zadanou uživatelem. Zvažte například následující jednoduchou hierarchii převzat ze spravovaných rozšíření specifikace jazyka:  
  
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
  
 V tomto příkladu jsou oba destruktory přejmenované `Finalize`. `B`na `Finalize` má k vyvolání `A`na `Finalize` metoda přidat následující volání `WriteLine`. Je to, co uvolňování vyvolá ve výchozím nastavení během dokončení. Zde je, jak může vypadat tato vnitřní transformace:  
  
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
  
1.  V druhém kroku kompilátor syntetizuje virtuální destruktor. Tento destruktor je co naše aplikace uživatele spravovaných rozšíření vyvolání přímo nebo prostřednictvím aplikace výrazu odstranit. Vyvolá se nikdy modulem garbage collector.  
  
     Dva příkazy jsou umístěny v rámci této syntetizovaná destruktor. Jedna je volání `GC::SuppressFinalize` a ujistěte se, že neexistují žádná další volání `Finalize`. Druhá je skutečný vyvolání `Finalize`, která představuje destruktor uživatelem zadané pro tuto třídu. Zde je, jak to může vypadat:  
  
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
  
 Zatímco tato implementace umožňuje uživateli explicitně vyvolání třídy `Finalize` metoda teď místo v době, nemáte žádnou kontrolu nad, je opravdu nestačí s `Dispose` metoda řešení. To se změní v jazyce Visual C++.  
  
## <a name="destructors-in-new-syntax"></a>Destruktory v nové syntaxe  
 V nové syntaxe je destruktor přejmenován interně na `Dispose` metoda a referenční třída je automaticky rozšířena implementovat `IDispose` rozhraní. To znamená v části Visual C++, naše dvojice tříd převede následujícím způsobem:  
  
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
  
 Když buď destruktor volán explicitně nové syntaxe, nebo když `delete` se použije pro sledování popisovače, základní `Dispose` metoda je volána automaticky. Pokud je odvozená třída, volání `Dispose` metoda základní třídy vloženo na konec syntetizovaná metody.  
  
 Ale to není zobrazit nám úplně deterministické dokončení. Aby bylo možné dosáhnout, potřebujeme další podporu místní odkaz objektů. (Tato akce nemá žádné podobá podpory v rámci spravovaných rozšíření, a proto se nejedná o problém s překladem.)  
  
## <a name="declaring-a-reference-object"></a>Deklarování referenční objekt.  
 Visual C++ podporuje deklarace objektu referenční třídy na místním zásobníku nebo jako člen třídy, jako kdyby byly přímo přístupné. V kombinaci s přidružení destruktoru s `Dispose` metoda, výsledek je automatické vyvolání dokončovací sémantiky pro odkazové typy.  
  
 Nejprve definujeme naše referenční třída tak, že vytvoření objektu funguje jako získání zdroje prostřednictvím konstruktor třídy. Za druhé v rámci destruktoru třídy vydáváme prostředků získali při vytvoření objektu.  
  
```  
public ref class R {  
public:  
   R() { /* acquire expensive resource */ }  
   ~R() { /* release expensive resource */ }  
  
   // everything else...  
};  
```  
  
 Objekt je deklarován místně pomocí název typu, ale bez doprovodného pokrytí. Všechny používá objekt, jako je například volání metody, jsou prováděny prostřednictvím výběru člena tečkou (`.`) namísto šipku (`->`). Na konci bloku, přidružené destruktor převede na `Dispose`, je vyvoláno automaticky, jak je vidět tady:  
  
```  
void f() {  
   R r;   
   r.methodCall();  
  
   // r is automatically destructed here -  
   // that is, r.Dispose() is invoked  
}  
```  
  
 Stejně jako u `using` příkazu v C#, nebude toto porušovat základní omezení modulu CLR, že všechny referenční typy musí být přidělena na haldě CLR. Základní sémantiku zůstanou beze změny. Uživatel může ekvivalentně napsat následující (a je pravděpodobně vnitřní transformace provádí kompilátor):  
  
```  
// equivalent implementation  
// except that it should be in a try/finally clause  
void f() {  
   R^ r = gcnew R;   
   r->methodCall();  
  
   delete r;  
}  
```  
  
 Ve skutečnosti podle nové syntaxe destruktory opět svázány s konstruktory jako automatické získání a verze mechanismus, vázaný doba života objektu místní.  
  
## <a name="declaring-an-explicit-finalize"></a>Deklarování explicitního dokončení  
 V nové syntaxe, jak jste viděli, je destruktor syntetizován do `Dispose` metoda. To znamená, že když destruktor není explicitně vyvolán, uvolňování paměti během dokončení, nebude nalezena přiřazený `Finalize` metoda pro objekt. Pro podporu, odstraňování a dokončení, jsme zavedli speciální syntaxi pro poskytování finalizační metody. Příklad:  
  
```  
public ref class R {  
public:  
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }  
};  
```  
  
 `!` Předpona je obdobou znak tilda (`~`), představuje destruktor – tedy obě metody po životnost mít objekt název třídy. Pokud syntetizovaná `Finalize` metoda vyskytuje v odvozené třídě, k vyvolání základní třídy `Finalize` metoda je vložen v jeho koncem. Pokud je destruktor explicitně vyvolán, finalizační metodu potlačeno. Zde je, jak může vypadat transformace:  
  
```  
// internal transformation under new syntax  
public ref class R {  
public:  
   void Finalize() {  
      Console::WriteLine( "I am the R::finalizer()!" );  
   }  
};   
```  
  
## <a name="moving-from-managed-extensions-for-c-to-visual-c-2010"></a>Přesunutí ze spravovaných rozšíření jazyka C++ na Visual C++ 2010  
 Modul runtime chování spravovaných rozšíření pro C++ program se změní, když je přeložen v jazyce Visual C++ vždy, když referenční třídy obsahuje netriviální – destruktor. Algoritmus vyžaduje překlad je podobný následujícímu:  
  
1.  Pokud je k dispozici destruktor, přepište to finalizační metodu třídy.  
  
2.  Pokud `Dispose` je k dispozici metoda, která přepisování do destruktoru třídy.  
  
3.  Pokud je k dispozici destruktor, ale neexistuje žádné `Dispose` metody zachovat destruktoru při provádění první položka.  
  
 Při přesouvání kódu ze spravovaných rozšíření pro nové syntaxe, můžete přijít o provádění této transformace. Pokud aplikace závisí na provádění metody přidružené finalizace nějakým způsobem, chování aplikace se oproti je ta, kterou jste zamýšleli.  
  
## <a name="see-also"></a>Viz také  
 [Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)   
 [Destruktory a finalizační metody v postupy: definování a používání tříd a struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)