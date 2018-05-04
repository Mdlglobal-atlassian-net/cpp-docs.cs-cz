---
title: Řízení přístupu ke členu (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1f36b23ce76c4f4e639e824116f7f80063a8748
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="member-access-control-c"></a>řízení přístupu ke členu (C++)
Řízení přístupu vám umožňují oddělit [veřejné](../cpp/public-cpp.md) rozhraní třídy z [privátní](../cpp/private-cpp.md) podrobnosti implementace a [chráněné](../cpp/protected-cpp.md) členů, které jsou pouze pro použití s odvozené třídy. Specifikátor přístupu se vztahuje na všechny členy deklarovaný po jeho až do další specifikátor přístup.  
  
```  
class Point  
{  
public:                   
    Point( int, int ) // Declare public constructor.;  
    Point();// Declare public default constructor.  
    int &x( int ); // Declare public accessor.  
    int &y( int ); // Declare public accessor.  
  
private:                 // Declare private state variables.  
    int _x;  
    int _y;  
  
protected:      // Declare protected function for derived classes only.  
    Point ToWindowCoords();  
};  
  
```  
  
 Výchozí úroveň přístupu je `private` v třídě, a `public` v struktura nebo union. Specifikátory přístupu do třídy lze použít libovolný počet časy v libovolném pořadí. Přidělení úložiště pro objekty typů třídy je závislé na implementaci, ale je zaručeno, že členům budou přiřazeny postupné vyšší adresy paměti mezi specifikátory přístupu.  
  
### <a name="member-access-control"></a>Ovládací prvek přístupu členů  
  
|Typ přístupu|Význam|  
|--------------------|-------------|  
|[private](../cpp/private-cpp.md)|Členy třídy deklarované jako `private` lze použít pouze členskými funkcemi a přáteli třídy (třídy nebo funkce).|  
|[protected](../cpp/protected-cpp.md)|Členy třídy deklarován jako `protected` mohou být využívána členských funkcí a přátel třídy (třídy nebo funkce). Navíc je možné je použít třídami odvozenými z třídy.|  
|[public](../cpp/public-cpp.md)|Členy třídy deklarován jako **veřejné** můžou používat žádné funkce.|  
  
 Řízení přístupu pomůže zabránit používání objektů způsoby, které nebyly k použití určeny. Tato ochrana je ztracena při provedení explicitních převodů typu (přetypování).  
  
> [!NOTE]
>  Řízení přístupu se vztahuje rovněž na všechny názvy: členské funkce, data členů, vnořené třídy a enumerátory.  
  
## <a name="access-control-in-derived-classes"></a>Řízení přístupu v odvozených třídách  
 Ovládací prvek dva faktory, které členy základní třídy jsou k dispozici v odvozené třídě; Tyto faktory stejné řízení přístupu k zděděné členy v odvozené třídě:  
  
-   Jestli deklaruje odvozené třídy základní třídy pomocí **veřejné** přístup specifikace v *třída head* (*head – třída* je popsaný v části gramatika [ Definování typů třída](http://msdn.microsoft.com/en-us/e8c65425-0f3a-4dca-afc2-418c3b1e57da)).  
  
-   Přístup ke členu Novinky v základní třídě.  
  
 Následující tabulka ukazuje interakce mezi tyto faktory a jak určit přístup ke členu základní třídy.  
  
### <a name="member-access-in-base-class"></a>Přístup ke členu v základní třídě  
  
|private|protected|Public|  
|-------------|---------------|------------|  
|Vždy nepřístupný bez ohledu na to odvození přístup|Privátní odvozené třídy, pokud použijete privátní odvození|Privátní odvozené třídy, pokud použijete privátní odvození|  
||Pokud používáte chráněné odvození chráněné v odvozené třídě|Pokud používáte chráněné odvození chráněné v odvozené třídě|  
||Pokud používáte veřejné odvození chráněné odvozené třídy|Veřejné odvozené třídy, pokud používáte veřejné odvození|  
  
 Následující příklad ilustruje toto:  
  
```  
// access_specifiers_for_base_classes.cpp  
class BaseClass  
{  
public:  
    int PublicFunc();    // Declare a public member.  
protected:  
    int ProtectedFunc(); // Declare a protected member.  
private:  
    int PrivateFunc();   // Declare a private member.  
};  
  
// Declare two classes derived from BaseClass.  
class DerivedClass1 : public BaseClass  
{  
};  
  
class DerivedClass2 : private BaseClass  
{  
};  
  
int main()  
{  
}  
```  
  
 V `DerivedClass1`, – členská funkce `PublicFunc` členem veřejné a `ProtectedFunc` je chráněného člena, protože `BaseClass` je veřejný základní třídu. `PrivateFunc` soukromý `BaseClass`, a není přístupný na všechny odvozené třídy.  
  
 V `DerivedClass2`, funkce `PublicFunc` a `ProtectedFunc` jsou považovány za soukromé členy, protože `BaseClass` je privátní základní třídu. Znovu `PrivateFunc` soukromý `BaseClass`, a není přístupný na všechny odvozené třídy.  
  
 Je možné deklarovat odvozené třídě bez specifikátor přístup základní třídy. V takovém případě je odvození považovány za soukromé, pokud používá deklarace odvozené třídy **třída** – klíčové slovo. Odvození je považovány za veřejné, pokud používá deklarace odvozené třídy `struct` – klíčové slovo. Například následující kód:  
  
```  
class Derived : Base  
...  
```  
  
 je ekvivalentní:  
  
```  
class Derived : private Base  
...  
```  
  
 Podobně následující kód:  
  
```  
struct Derived : Base  
...  
```  
  
 je ekvivalentní:  
  
```  
struct Derived : public Base  
...  
```  
  
 Všimněte si, že nejsou dostupné pro funkce členy jako soukromý přístup nebo odvozené třídy, pokud tyto funkce nebo třídy jsou deklarováno s použitím `friend` deklarace v základní třídě.  
  
 A **sjednocení** typ nemůže mít základní třídu.  
  
> [!NOTE]
>  Při zadávání privátní základní třídu, doporučuje se explicitně použít `private` – klíčové slovo uživatelů, aby odvozené třídy pochopili přístup ke členu.  
  
## <a name="access-control-and-static-members"></a>Řízení přístupu a statické členy  
 Pokud zadáte základní třídu jako `private`, ovlivní to pouze nestatické členy. Veřejné statické členy jsou v odvozených třídách stále přístupné. Avšak přístup ke členům základní třídy pomocí ukazatelů, odkazů nebo objektů může vyžadovat převod, kdy se znovu uplatní časové řízení přístupu. Podívejte se na následující příklad:  
  
```  
// access_control.cpp  
class Base  
{  
public:  
    int Print();             // Nonstatic member.  
    static int CountOf();    // Static member.  
};  
  
// Derived1 declares Base as a private base class.  
class Derived1 : private Base  
{  
};  
// Derived2 declares Derived1 as a public base class.  
class Derived2 : public Derived1  
{  
    int ShowCount();    // Nonstatic member.  
};  
// Define ShowCount function for Derived2.  
int Derived2::ShowCount()  
{  
   // Call static member function CountOf explicitly.  
    int cCount = Base::CountOf();     // OK.  
  
   // Call static member function CountOf using pointer.  
    cCount = this->CountOf();  // C2247. Conversion of  
                               //  Derived2 * to Base * not  
                               //  permitted.  
    return cCount;  
}  
```  
  
 V předchozím kódu řízení přístupu zakazuje převod z ukazatele na typ `Derived2` na ukazatele na typ `Base`. **To** ukazatel je implicitně typu `Derived2 *`. Chcete-li vybrat `CountOf` funkce, **to** musí převést na typ `Base *`. Takový převod není povolen, protože typ `Base` je privátní nepřímá základní třída typu `Derived2`. Převod na typ soukromé základní třídy je přijatelný pouze pro ukazatele na přímé odvozené třídy. Proto lze ukazatele typu `Derived1 *` převést na typ `Base *`.  
  
 Explicitní volání funkce `CountOf` bez použití ukazatele, odkazu nebo objektu neprovede žádný převod. Proto je toto volání povoleno.  
  
 Členové a přátelé odvozené třídy `T` mohou převést ukazatel na typ `T` na ukazatel na přímou soukromou základní třídu typu `T`.  
  
## <a name="access-to-virtual-functions"></a>Přístup k virtuálním funkcím  
 Řízení přístupu se použijí k [virtuální](../cpp/virtual-cpp.md) funkce je určen podle typu použít k volání funkce. Přepisovací deklarace funkce neovlivňují řízení přístupu pro daný typ. Příklad:  
  
```  
// access_to_virtual_functions.cpp  
class VFuncBase  
{  
public:  
    virtual int GetState() { return _state; }  
protected:  
    int _state;  
};  
  
class VFuncDerived : public VFuncBase  
{  
private:  
    int GetState() { return _state; }  
};  
  
int main()  
{  
   VFuncDerived vfd;             // Object of derived type.  
   VFuncBase *pvfb = &vfd;       // Pointer to base type.  
   VFuncDerived *pvfd = &vfd;    // Pointer to derived type.  
   int State;  
  
   State = pvfb->GetState();     // GetState is public.  
   State = pvfd->GetState();     // C2248 error expected; GetState is private;  
}  
```  
  
 V předchozím příkladu volání virtuální funkce `GetState` pomocí ukazatele na typ `VFuncBase` volá funkci `VFuncDerived::GetState` a funkce `GetState` je považována za veřejnou. Volání funkce `GetState` pomocí ukazatele na typ `VFuncDerived` je však narušením řízení přístupu, protože funkce `GetState` je ve třídě `VFuncDerived` deklarována jako soukromá.  
  
> [!CAUTION]
>  Virtuální funkci `GetState` lze zavolat pomocí ukazatele na základní třídu `VFuncBase`. To neznamená, že volaná funkce je verzí této funkce obsaženou v základní třídě.  
  
## <a name="access-control-with-multiple-inheritance"></a>Řízení přístupu pomocí vícenásobná dědičnost  
 Ve svazech vícenásobné dědičnosti zahrnujících virtuální základní třídy lze konkrétního názvu dosáhnout více cestami. Protože v případě těchto různých cest mohou platit různá řízení přístupu, volí kompilátor volí, která poskytuje nejvíce přístupu. Prohlédněte si následující obrázek.  
  
 ![Přístup podél cesty grafu dědičnosti](../cpp/media/vc38v91.gif "vc38V91")  
Přístup podél cest grafu dědičnosti  
  
 Na obrázku je název deklarovaný ve třídě `VBase` vždy dosažen prostřednictvím třídy `RightPath`. Pravá cesta je přístupnější, protože třída `RightPath` deklaruje třídu `VBase` jako veřejnou základní, zatímco třída `LeftPath` deklaruje třídu `VBase` jako soukromou.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)