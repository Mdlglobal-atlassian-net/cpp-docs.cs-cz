---
title: Kolekce (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: 59e73b803a0878e88361c7fe75cff556b8eeedcd
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032314"
---
# <a name="collections-ccx"></a>Kolekce (C++/CX)

V programu C++/CX můžete bezplatně využívat kontejnery knihovny šablon (STL) nebo jakýkoli jiný uživatelem definovaný typ kolekce. Však při předání kolekce tam a zpět přes binární rozhraní aplikace Prostředí Windows Runtime (ABI) – například do ovládacího prvku XAML nebo do klienta JavaScriptu – je nutné použít typy kolekcí prostředí Windows Runtime.

Prostředí Windows Runtime definuje rozhraní pro kolekce a související typy a C++/CX poskytuje konkrétní implementace jazyka C++ v souboru hlavičky collection.h. Tento obrázek znázorňuje vztahy mezi typy kolekcí:

![C&#43;&#43;&#47;Strom dědičnosti CX pro typy kolekcí](../cppcx/media/cppcxcollectionsinheritancetree.png "C&#43;&#43;&#47;Strom dědičnosti CX pro typy kolekcí")

- [Platforma::Kolekce::Vector třída](../cppcx/platform-collections-vector-class.md) se podobá [std::vector class](../standard-library/vector-class.md).

- [Platforma::Kolekce::Třída Map](../cppcx/platform-collections-map-class.md) se podobá [třídě std::map](../standard-library/map-class.md).

- [Platforma::Kolekce::VectorView Class](../cppcx/platform-collections-vectorview-class.md) a[Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md) jsou `Vector` verze `Map`třídy a .

- Iterátory jsou definovány v [platformě::Collections Namespace](../cppcx/platform-collections-namespace.md). Tyto iterátory splňují požadavky na iterátory STL a umožňují použití [std::find](../standard-library/algorithm-functions.md#find), [std::count_if](../standard-library/algorithm-functions.md#count_if)a dalších algoritmů STL v libovolném [systému Windows::Foundation::Collections](/uwp/api/windows.foundation.collections) typ rozhraní nebo [platforma::Kolekce](../cppcx/platform-collections-namespace.md) konkrétní typ. Například to znamená, že můžete iterate kolekce v komponentě prostředí Windows Runtime, která je vytvořena v C# a použít algoritmus STL na něj.

   > [!IMPORTANT]
   > Proxy iterátory `VectorIterator` `VectorViewIterator` a využít `VectoryProxy<T>` `ArrowProxy<T>` proxy objekty a povolit použití s KONTEJNERY STL. Další informace naleznete v části "VectorProxy prvky" dále v tomto článku.

- Typy kolekce C++/CX podporují stejné záruky bezpečnosti podprocesu, které podporují kontejnery STL.

- [Windows::Foundation::Collections::IObservableVector](/uwp/api/windows.foundation.collections.iobservablevector-1) a [Windows::Foundation::Collections::IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) definují události, které jsou aktivovány, když se kolekce mění různými způsoby. Implementací těchto rozhraní [platforma::Kolekce::Map](../cppcx/platform-collections-map-class.md) a [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) podporují datové vazby s kolekcemi XAML. Například pokud `Vector` máte, který je vázán `Grid`na data , při přidání položky do kolekce, změna se projeví v gridu uj.

## <a name="vector-usage"></a>Využití vektorů

Když vaše třída má předat kontejner sekvence do jiné součásti prostředí Windows Runtime, použijte [Windows::Foundation::Collections:: IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1) jako parametr nebo návratový typ a [Platform::Collections::Vector\<T>](../cppcx/platform-collections-vector-class.md) jako konkrétní implementace. Pokud se pokusíte `Vector` použít typ ve veřejné vrácené hodnotě nebo parametru, bude vyvolána chyba kompilátoru C3986. Chybu můžete opravit změnou `Vector` na `IVector`.

> [!IMPORTANT]
> Pokud předáváte sekvenci v rámci `Vector` `std::vector` vlastního programu, použijte `IVector`buď nebo protože jsou efektivnější než . Používejte `IVector` pouze v případě, že předáte kontejner přes ABI.
>
> Systém typu Prostředí Windows Runtime nepodporuje koncept zubatých polí, a proto nelze\<předat platformu IVector<::Array T>> jako parametr návratové hodnoty nebo metody. Chcete-li předat zubaté pole nebo posloupnost `IVector<IVector<T>^>`sekvencí přes ABI, použijte .

`Vector<T>`Poskytuje metody, které jsou požadovány pro přidání, odebrání a přístup k položkám v kolekci a je implicitně převoditelný na `IVector<T>`. Algoritmy STL můžete také použít `Vector<T>`na instancích . Následující příklad ukazuje některé základní použití. Počáteční [a](../cppcx/begin-function.md) [koncová funkce](../cppcx/end-function.md) zde `Platform::Collections` jsou z `std` oboru názvů, nikoli z oboru názvů.

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

Pokud máte existující kód, který `std::vector` používá a chcete jej znovu použít v součásti prostředí Windows Runtime, stačí použít jeden z `Vector` `Vector` konstruktorů, který trvá `std::vector` nebo pár iterátorů k vytvoření v místě, kde předáte kolekci přes ABI. Následující příklad ukazuje, jak `Vector` použít konstruktor move pro `std::vector`efektivní inicializaci z . Po operaci přesunutí původní `vec` proměnná již není platná.

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

Pokud máte vektor řetězců, které je nutné předat přes ABI v určitém budoucím okamžiku, musíte `std::wstring` se `Platform::String^` rozhodnout, zda chcete vytvořit řetězce zpočátku jako typy nebo jako typy. Pokud máte udělat hodně zpracování na řetězce, pak `wstring`použijte . V opačném případě vytvořte řetězce jako `Platform::String^` typy a vyhněte se nákladům na jejich pozdější převod. Musíte se také rozhodnout, zda `std:vector` chcete `Platform::Collections::Vector` umístit tyto řetězce do nebo interně. Jako obecné postupy, `std::vector` použijte a `Platform::Vector` potom vytvořit z něj pouze při předání kontejneru přes ABI.

## <a name="value-types-in-vector"></a>Typy hodnot ve vektoru

Každý prvek, který má být uložen v [platformě::Collections::Vector](../cppcx/platform-collections-vector-class.md) musí podporovat porovnání rovnosti, implicitně nebo pomocí vlastního srovnávače [std::equal_to,](../standard-library/equal-to-struct.md) který zadáte. Všechny typy odkazů a všechny skalární typy implicitně podporují porovnání rovnosti. Pro jiné než skalární typy hodnot, jako je [Windows::Foundation::DateTime](/uwp/api/windows.foundation.datetime) `objA->UniqueID == objB->UniqueID`, nebo pro vlastní porovnání – například – je nutné zadat vlastní objekt funkce.

## <a name="vectorproxy-elements"></a>Prvky VectorProxy

[Platforma::Kolekce::VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) a [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) umožňují `range for` použití smyček a algoritmů, jako [je std::sort](../standard-library/algorithm-functions.md#sort) s [\<kontejnerem IVector T>.](/uwp/api/windows.foundation.collections.ivector-1) Ale `IVector` prvky nelze přistupovat prostřednictvím c++ ukazatel dereference; jsou přístupné pouze prostřednictvím [GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) a [SetAt](/uwp/api/windows.foundation.collections.ivector-1.setat) metody. Proto tyto iterátory používají proxy `Platform::Details::VectorProxy<T>` `Platform::Details::ArrowProxy<T>` třídy a poskytují přístup __\*__ __->__ k jednotlivým prvkům prostřednictvím , a __ \[]__ operátory, jak to vyžaduje standardní knihovny. Přísně vzato, `IVector<Person^> vec`vzhledem `*begin(vec)` k `VectorProxy<Person^>`tomu, , typ je . Objekt proxy je však téměř vždy transparentní pro váš kód. Tyto proxy objekty nejsou dokumentovány, protože jsou určeny pouze pro vnitřní použití iterátory, ale je užitečné vědět, jak funguje mechanismus.

Při použití `range for` smyčky `IVector` přes kontejnery, použijte `auto&&` k povolení iterátor `VectorProxy` proměnné správně vázat na prvky. Pokud `auto` používáte `auto&`nebo , upozornění kompilátoru `VectoryProxy` C4239 je aktivována a je uvedeno v textu upozornění.

Následující obrázek `range for` znázorňuje `IVector<Person^>`smyčku přes . Všimněte si, že spuštění je zastaveno na zarážky na řádku 64. Okno **QuickWatch** ukazuje, že proměnná `p` iterátoru je ve skutečnosti proměnná, `VectorProxy<Person^>` která má `m_v` a `m_i` členské proměnné. Však při `GetType` volání na tuto proměnnou vrátí `Person` stejný `p2`typ instance . Stánek s jídlem `VectorProxy` `ArrowProxy` je, že i když a může se objevit v **QuickWatch**, ladicí program některé chyby kompilátoru, nebo na jiných místech, obvykle není třeba explicitně kód pro ně.

![VectorProxy v rozsahu&#45;založené na smyčce](../cppcx/media/vectorproxy-1.png "VectorProxy v rozsahu&#45;založené na smyčce")

Jeden scénář, ve kterém budete muset kód kolem proxy `dynamic_cast` objektu je, když máte provést na prvky – například `UIElement` při hledání XAML objekty určitého typu v kolekci prvků. V takovém případě musíte nejprve přetypovat prvek [platformy::Object](../cppcx/platform-object-class.md)^ a potom provést dynamické přetypádku:

```cpp
void FindButton(UIElementCollection^ col)
{
    // Use auto&& to avoid warning C4239
    for (auto&& elem : col)
    {
        Button^ temp = dynamic_cast<Button^>(static_cast<Object^>(elem));
        if (nullptr != temp)
        {
            // Use temp...
        }
    }
}
```

## <a name="map-usage"></a>Využití mapy

Tento příklad ukazuje, jak vložit položky a vyhledat je v [platformě::Collections::Map](../cppcx/platform-collections-map-class.md), a potom vrátit `Map` jako Windows jen pro [čtení::Foundation::Collections::IMapView](/uwp/api/windows.foundation.collections.imapview-2) typ.

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

Obecně platí pro funkce vnitřní mapy, upřednostňujte `std::map` typ z důvodů výkonu. Pokud máte předat kontejner přes ABI, postavit [platformu::Collections::Map](../cppcx/platform-collections-map-class.md) z [std::map](../standard-library/map-class.md) a vrátit `Map` jako [Windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2). Pokud se pokusíte `Map` použít typ ve veřejné vrácené hodnotě nebo parametru, bude vyvolána chyba kompilátoru C3986. Chybu můžete opravit změnou `Map` na `IMap`. V některých případech – například pokud neprovádíte velký počet vyhledávání nebo vložení a často předáváte kolekci přes ABI – `Platform::Collections::Map` může být levnější používat od `std::map`začátku a vyhnout se nákladům na převod . V každém případě se vyhněte `IMap` vyhledávání a vložení operace na, protože se jedná o nejméně výkonný ze tří typů. Převést `IMap` pouze v okamžiku, kdy předáte kontejner přes ABI.

## <a name="value-types-in-map"></a>Typy hodnot v mapě

Prvky v [platformě::Collections::Map](../cppcx/platform-collections-map-class.md) jsou seřazeny. Jakýkoli prvek, který `Map` má být uložen v musí podporovat méně než porovnání s přísné slabé řazení, implicitně nebo pomocí vlastní [stl::less](../standard-library/less-struct.md) comparator, který zadáte. Scalární typy podporují porovnání implicitně. Pro neskalární typy hodnot, jako `Windows::Foundation::DateTime`je například , `objA->UniqueID < objB->UniqueID`nebo pro vlastní porovnání – musíte zadat vlastní komparátor.

## <a name="collection-types"></a>Typy kolekcí

Kolekce spadají do čtyř kategorií: upravitelné verze a verze kolekce sekvence jen pro čtení a asociativní kolekce. Kromě toho C++/CX vylepšuje kolekce tím, že poskytuje tři iterátor třídy, které zjednodušují přístup k kolekcím.

Prvky upravitelné kolekce lze změnit, ale prvky kolekce jen pro čtení, která se označuje jako *zobrazení*, lze číst pouze. Prvky [Platform::Collections:::Vector](../cppcx/platform-collections-vector-class.md) nebo[Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) kolekce lze přistupovat pomocí iterátoru nebo [kolekce Vector::GetAt](../cppcx/platform-collections-vector-class.md#getat) a index. Prvky asociativní kolekce lze přistupovat pomocí [mapy kolekce::Vyhledávání](../cppcx/platform-collections-map-class.md#lookup) a klíč.

[Platform::Collections::Map – třída](../cppcx/platform-collections-map-class.md)<br/>
Upravitelné, asociativní kolekce. Prvky mapy jsou dvojice klíč-hodnota. Vyhledání klíče pro načtení přidružené hodnoty a iterace prostřednictvím všech párů klíč-hodnota jsou podporovány.

`Map`a `MapView` jsou přeřazeny na `<K, V, C = std::less<K>>`; proto můžete přizpůsobit komparátor.  Navíc `Vector` a `VectorView` jsou šablony `<T, E = std::equal_to<T>>` na tak, že můžete `IndexOf()`přizpůsobit chování . To je důležité `Vector` `VectorView` především pro a hodnoty struktur. Chcete-li například\<vytvořit vektorový systém Windows::Foundation::DateTime>, musíte zadat vlastní komparátor, protože DateTime nepřetěžuje operátor ==.

[Platform::Collections::MapView – třída](../cppcx/platform-collections-mapview-class.md)<br/>
Verze aplikace jen pro `Map`čtení .

[Platform::Collections::Vector – třída](../cppcx/platform-collections-vector-class.md)<br/>
Modifikovatelné sekvence kolekce. `Vector<T>`podporuje konstantní čas náhodný přístup a amortizované-konstantní čas [připojit](../cppcx/platform-collections-vector-class.md#append) operace..

[Platform::Collections::VectorView – třída](../cppcx/platform-collections-vectorview-class.md)<br/>
Verze aplikace jen pro `Vector`čtení .

[Platform::Collections::InputIterator – třída](../cppcx/platform-collections-inputiterator-class.md)<br/>
Iterátor STL, který splňuje požadavky vstupního iterátoru STL.

[Platform::Collections::VectorIterator – třída](../cppcx/platform-collections-vectoriterator-class.md)<br/>
Iterátor STL, který splňuje požadavky stl mutable random-access iterator.

[Platforma::Kolekce::Třída VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
Iterátor STL, který splňuje požadavky iterátoru náhodného přístupu STL. `const`

### <a name="begin-and-end-functions"></a>begin() a end() funkce

Pro zjednodušení použití STL ke `Vector` `VectorView`zpracování `Map` `MapView`, , `Windows::Foundation::Collections` , a libovolných objektů podporuje C++/CX přetížení [nečlenských](../cppcx/begin-function.md) funkcí počáteční funkce a [koncové funkce.](../cppcx/end-function.md)

V následující tabulce jsou uvedeny dostupné iterátory a funkce.

|Iterátory|Functions|
|---------------|---------------|
|[Platforma::Kolekce::VectorIterator\<T>](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Interně ukládá [Windows::Foundation::Collections::\<IVector T>](/uwp/api/windows.foundation.collections.ivector-1) a int.)|[začátek](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md)([Windows::Foundation::Collections::\<IVector T>](/uwp/api/windows.foundation.collections.ivector-1))|
|[Platforma::Kolekce::VectorViewIterator\<T>](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Interně ukládá [IVectorView\<T>](/uwp/api/windows.foundation.collections.ivectorview-1)^ a int.)|[začátek](../cppcx/begin-function.md)/ [(](../cppcx/end-function.md) [\<IVectorView T>](/uwp/api/windows.foundation.collections.ivectorview-1)^)|
|[Platforma::Kolekce::InputIterator\<T>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [\<IIterator T>](/uwp/api/windows.foundation.collections.iiterator-1)^ a T.)|[začátek](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IIterable\<T>](/uwp/api/windows.foundation.collections.iiterable-1))|
|[Platforma::Kolekce::InputIterator<IKeyValuePair\<K, V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [\<IIterator T>](/uwp/api/windows.foundation.collections.iiterator-1)^ a T.)|[začátek](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IMap\<K,V>](/uwp/api/windows.foundation.collections.imap-2).|
|[Platforma::Kolekce::InputIterator<IKeyValuePair\<K, V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [\<IIterator T>](/uwp/api/windows.foundation.collections.iiterator-1)^ a T.)|[začátek](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([Windows::Foundation::Collections::IMapView](/uwp/api/windows.foundation.collections.imapview-2))|

### <a name="collection-change-events"></a>Události změny kolekce

`Vector`a `Map` podporují datové vazby v kolekcích XAML implementací událostí, ke kterým dochází při změně nebo resetování objektu kolekce nebo při vložení, odebrání nebo změně libovolného prvku kolekce. Můžete napsat vlastní typy, které podporují datové vazby, i když nelze dědit z `Map` nebo `Vector` protože tyto typy jsou zapečetěny.

Delegáti [Windows::Foundation::Collections::VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1) a [Windows::Foundation::Collections::MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) delegáti určují podpisy pro obslužné rutiny událostí pro události změny kolekce. [Windows::Foundation::Collections::CollectionChange třídy](/uwp/api/windows.foundation.collections.collectionchange) veřejnévýčtáčtu a `Platform::Collection::Details::MapChangedEventArgs` a `Platform::Collections::Details::VectorChangedEventArgs` ref třídy, uložte argumenty události k určení, co způsobilo událost. Typy `*EventArgs` jsou definovány `Details` v oboru názvů, protože není třeba je explicitně vytvářet nebo využívat při použití `Map` nebo `Vector`.

## <a name="see-also"></a>Viz také

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
