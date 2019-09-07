---
title: Kolekce (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: ff3fb9899355ec05083dc15c16d74c9aa1d3fd8f
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740321"
---
# <a name="collections-ccx"></a>Kolekce (C++/CX)

V programu C++/CX můžete využít bezplatné použití kontejnerů knihovny STL (Standard Template Library) nebo jakýkoli jiný uživatelem definovaný typ kolekce. Pokud však předáte kolekce zpátky a zpátky v binárním rozhraní aplikace prostředí Windows Runtime (ABI) – například na ovládací prvek XAML nebo na klienta jazyka JavaScript – je nutné použít typy kolekce prostředí Windows Runtime.

Prostředí Windows Runtime definuje rozhraní pro kolekce a související typy a C++/CX poskytuje konkrétní C++ implementace v souboru hlaviček Collection. h. Tento obrázek znázorňuje vztahy mezi typy kolekce:

![Strom&#43;&#43;&#47;dědičnosti c CX pro typy kolekcí]–(../cppcx/media/cppcxcollectionsinheritancetree.png "strom dědičnosti c&#43;&#43;&#47;CX pro typy kolekcí")

- [Třída Platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) se podobá [třídě std:: Vector](../standard-library/vector-class.md).

- Třída [Platform:: Collections:: map](../cppcx/platform-collections-map-class.md) se podobá [třídě std:: map](../standard-library/map-class.md).

- [Platform:: Collections:: VectorView třída](../cppcx/platform-collections-vectorview-class.md) a[Platform:: Collections:: MapView](../cppcx/platform-collections-mapview-class.md) jsou verze `Vector` a `Map`.

- Iterátory jsou definovány v [oboru názvů Platform:: Collections](../cppcx/platform-collections-namespace.md). Tyto iterátory splňují požadavky na iterátory STL a umožňují použití algoritmů [std:: Find](../standard-library/algorithm-functions.md#find), [std:: count_if](../standard-library/algorithm-functions.md#count_if)a dalších algoritmů STL na libovolných typech rozhraní [Windows:: Foundation:: Collections](/uwp/api/windows.foundation.collections) nebo [Platform:: Collections.](../cppcx/platform-collections-namespace.md) konkrétní typ. Například to znamená, že můžete iterovat kolekci ve prostředí Windows Runtime komponentě, která je vytvořena v C# a použít pro ni algoritmus STL.

   > [!IMPORTANT]
   > Iterátory `VectorIterator` proxy serveru `VectorViewIterator` a používání objektů `VectoryProxy<T>` proxy `ArrowProxy<T>` a umožňují použití s kontejnery STL. Další informace naleznete v části "VectorProxy elementy" dále v tomto článku.

- Typy C++kolekce/CX podporují stejné záruky bezpečnosti vlákna, které podporují kontejnery STL.

- [Windows:: Foundation:: Collections:: IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) a [Windows:: Foundation:: Collections:: IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) definují události, které se aktivují, když se kolekce mění různými způsoby. Implementací těchto rozhraní [Platform:: Collections:: map](../cppcx/platform-collections-map-class.md) a [Platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) podporují datovou vazbu s kolekcemi XAML. Například pokud máte objekt `Vector` , který je vázán `Grid`na data, když přidáte položku do kolekce, tato změna se projeví v uživatelském rozhraní mřížky.

## <a name="vector-usage"></a>Využití vektoru

Pokud vaše třída musí předat kontejner sekvence jiné součásti prostředí Windows Runtime, použijte [Windows:: Foundation:: Collections:: IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) jako parametr nebo návratový typ a jako konkrétní implementaci [> Platform:: Collections\<:: Vector T](../cppcx/platform-collections-vector-class.md) . Pokud se pokusíte použít `Vector` typ ve veřejné návratové hodnotě nebo parametru, bude vyvolána chyba kompilátoru C3986. Chybu lze opravit změnou `Vector` objektu `IVector`na.

> [!IMPORTANT]
> Pokud předáte sekvenci ve vlastním programu, použijte buď `Vector` nebo `std::vector` , protože jsou efektivnější než `IVector`. Používejte `IVector` pouze při předávání kontejneru v rámci ABI.
>
> Systém typů prostředí Windows Runtime nepodporuje koncept vícenásobných polí, a proto nelze předat IVector < Platform:: array\<T > > jako návratovou hodnotu nebo parametr metody. Chcete-li předat vícenásobné pole nebo sekvenci sekvencí v rámci ABI, `IVector<IVector<T>^>`použijte.

`Vector<T>`poskytuje metody, které jsou požadovány pro přidání, odebrání a přístup k položkám v kolekci, a je implicitně převoditelná `IVector<T>`na. Můžete také použít algoritmy STL pro instance `Vector<T>`. Následující příklad znázorňuje základní použití. [Funkce Begin](../cppcx/begin-function.md) a [End Function](../cppcx/end-function.md) tady `Platform::Collections` je z oboru názvů, nikoli `std` oboru názvů.

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

Pokud máte existující kód, který používá `std::vector` a chcete ho znovu použít ve prostředí Windows Runtime komponentě, stačí použít jeden `Vector` z `std::vector` konstruktorů, který přebírá nebo dvojici iterátorů k vytvoření `Vector` v místě, kam předáte kolekce v rámci ABI. Následující příklad ukazuje, jak použít `Vector` konstruktor Move pro efektivní inicializaci `std::vector`z. Po operaci přesunu již původní `vec` proměnná není platná.

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

Pokud máte vektor řetězců, které je nutné předat v rámci určitého budoucího bodu, musíte se rozhodnout, zda chcete vytvořit řetězce jako `std::wstring` typy nebo jako `Platform::String^` typy. Pokud je nutné provést v řetězcích velké množství zpracování, použijte `wstring`. V opačném případě vytvořte řetězce `Platform::String^` jako typy a vyhněte se nákladům na jejich převod později. Musíte také rozhodnout, zda mají být tyto řetězce vloženy `std:vector` do `Platform::Collections::Vector` nebo interně. Obecně je vhodné použít `std::vector` a `Platform::Vector` vytvořit z něj pouze v případě, že předáte kontejner napříč ABI.

## <a name="value-types-in-vector"></a>Typy hodnot v vektoru

Všechny prvky, které mají být uloženy v [Platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) , musí podporovat porovnání rovnosti implicitně nebo pomocí vlastního typu [std:: equal_to](../standard-library/equal-to-struct.md) komparátor, který zadáte. Všechny typy odkazů a všechny skalární typy implicitně podporují porovnání rovnosti. Pro neskalární typy hodnot, jako je například [Windows:: Foundation::D atetime](/uwp/api/windows.foundation.datetime)nebo pro vlastní porovnávání – například `objA->UniqueID == objB->UniqueID`je třeba zadat vlastní objekt funkce.

## <a name="vectorproxy-elements"></a>VectorProxy elementy

[Platform:: Collections:: VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) a [Platform:: Collections:: VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) povolí použití `range for` smyček a algoritmů jako [std:: Sort](../standard-library/algorithm-functions.md#sort) s kontejnerem [IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) . K `IVector` elementům ale nelze přistoupit C++ prostřednictvím zpětného odkazování ukazatele. k nim lze přistoupit pouze prostřednictvím metod [GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) a [SetAt](/uwp/api/windows.foundation.collections.ivector-1.setat) . `Platform::Details::VectorProxy<T>` Proto tyto iterátory používají proxy třídy a `Platform::Details::ArrowProxy<T>` k poskytnutí přístupu k jednotlivým prvkům pomocí __\*__ operátorů, __->__ a  __\[]__ , jak je vyžadováno standardní knihovnou. Výhradně řečeno, s ohledem `IVector<Person^> vec`na, `*begin(vec)` je `VectorProxy<Person^>`typ typu. Objekt proxy je však téměř vždy transparentní pro váš kód. Tyto objekty proxy nejsou zdokumentovány, protože jsou pouze pro interní použití iterátory, ale je užitečné zjistit, jak mechanismus funguje.

Použijete-li `IVector` `auto&&` `VectorProxy` smyčku nad kontejnery, použijte k povolení správné vazby proměnné iterátoru na prvky. `range for` Použijete `auto` -li `auto&`nebo, je vyvolána upozornění kompilátoru C4239 `VectoryProxy` a je uvedena v textu upozornění.

Na následujícím obrázku je znázorněna `range for` smyčka `IVector<Person^>`přes. Všimněte si, že provádění je zastaveno na zarážce na řádku 64. Okno **QuickWatch** ukazuje, že proměnná `p` iterátoru `VectorProxy<Person^>` je ve skutečnosti a, která `m_v` má `m_i` a členské proměnné. Při volání `GetType` této proměnné však vrátí `Person` instanci `p2`stejného typu. Poznatkem je to, že `VectorProxy` i `ArrowProxy` když se může zobrazit v **QuickWatch**, ladicí program některé chyby kompilátoru nebo jiné místa, obvykle nemusíte pro ně explicitně kódovat kód.

![VectorProxy v rozsahu&#45;založeném na smyčce](../cppcx/media/vectorproxy-1.png "VectorProxy v&#45;rozsahu založeném na smyčce")

Jeden scénář, ve kterém je nutné kód kolem objektu proxy, je v případě, že je nutné `dynamic_cast` provést prvky, například při hledání objektů XAML určitého typu `UIElement` v kolekci elementů. V takovém případě je nutné nejprve přetypovat element na [Platform:: Object](../cppcx/platform-object-class.md)^ a pak provést dynamické přetypování:

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

## <a name="map-usage"></a>Použití mapy

Tento příklad ukazuje, jak vložit položky a vyhledat je v objektu [Platform:: Collections:: map](../cppcx/platform-collections-map-class.md)a pak vracet `Map` jako jen pro čtení [Windows:: Foundation:: Collections:: IMapView]/UWP/API/Windows.Foundation.Collections.IMapView_K_V_). textový.

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

Obecně platí, že `std::map` pro funkci interní mapy je vhodnější typ z hlediska výkonu. Pokud je nutné předat kontejner v rámci ABI, sestavte [Platform:: Collections:: map](../cppcx/platform-collections-map-class.md) z [std:: map](../standard-library/map-class.md) a vraťte se `Map` jako [Windows:: Foundation:: Collections:: IMAP](/uwp/api/Windows.Foundation.Collections.IMap_K_V_). Pokud se pokusíte použít `Map` typ ve veřejné návratové hodnotě nebo parametru, bude vyvolána chyba kompilátoru C3986. Chybu lze opravit změnou `Map` objektu `IMap`na. V některých případech – například pokud neprovádíte velký počet hledání nebo vkládání a často předáváte kolekci v rámci ABI, může být levnější použít `Platform::Collections::Map` od začátku a vyhnout se nákladům na převod `std::map`. V každém případě se vyhněte operacím vyhledávání a vkládání `IMap` na, protože se jedná o nejméně tyto tři typy. Převod na `IMap` pouze v bodu, který předáváte kontejneru napříč ABI.

## <a name="value-types-in-map"></a>Typy hodnot v mapě

Prvky v objektu [Platform:: Collections:: map](../cppcx/platform-collections-map-class.md) jsou seřazené. Všechny prvky, které mají být uloženy `Map` v prvku, musí podporovat méně než porovnání s přísným slabým řazením implicitně nebo pomocí vlastní [STL:: less](../standard-library/less-struct.md) komparátor, kterou zadáte. Skalární typy podporují porovnání implicitně. Pro neskalární typy hodnot `Windows::Foundation::DateTime`, jako například, nebo pro vlastní porovnávání – `objA->UniqueID < objB->UniqueID`například je třeba zadat vlastní komparátor.

## <a name="collection-types"></a>Typy kolekcí

Kolekce spadají do čtyř kategorií: upravitelné verze a verze kolekcí sekvencí a asociativní kolekce pouze pro čtení. Kromě toho C++/CX vylepšuje kolekce tím, že poskytuje tři třídy iterátoru, které zjednodušují přístup k kolekcím.

Prvky s upravitelnou kolekcí lze změnit, ale prvky kolekce jen pro čtení, které se označují jako *zobrazení*, lze číst pouze. K prvkům kolekce [Platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) nebo[Platform:: Collections:: VectorView](../cppcx/platform-collections-vectorview-class.md) lze přistupovat pomocí iterátoru nebo [vektoru kolekce:: GetAt](../cppcx/platform-collections-vector-class.md#getat) a indexu. K prvkům asociativní kolekce lze přistupovat pomocí [mapování:: Lookup](../cppcx/platform-collections-map-class.md#lookup) a Key.

[Platform::Collections::Map – třída](../cppcx/platform-collections-map-class.md)<br/>
Upravitelná, asociativní kolekce. Prvky mapy jsou páry klíč-hodnota. Vyhledání klíče pro načtení přidružené hodnoty a iterace všemi páry klíč-hodnota jsou podporovány.

`Map`a `MapView` jsou šablony `<K, V, C = std::less<K>>`, a proto můžete přizpůsobit komparátor.  `Vector` Dále a `VectorView` jsou šablony `<T, E = std::equal_to<T>>` , abybylo`IndexOf()`možné přizpůsobit chování. To je důležité hlavně pro `Vector` a `VectorView` struktury hodnot. Chcete-li například vytvořit objekt Vector\<Windows:: Foundation::D atetime >, je nutné zadat vlastní komparátor, protože DateTime neprovádí přetížení operátoru = =.

[Platform::Collections::MapView – třída](../cppcx/platform-collections-mapview-class.md)<br/>
Verze, která je `Map`jen pro čtení.

[Platform::Collections::Vector – třída](../cppcx/platform-collections-vector-class.md)<br/>
Kolekce sekvencí s upravitelnou příponou. `Vector<T>`podporuje náhodný přístup v čase a operace [připojení](../cppcx/platform-collections-vector-class.md#append) s konstantním časem.

[Platform::Collections::VectorView – třída](../cppcx/platform-collections-vectorview-class.md)<br/>
Verze, která je `Vector`jen pro čtení.

[Platform::Collections::InputIterator – třída](../cppcx/platform-collections-inputiterator-class.md)<br/>
Iterátor STL, který splňuje požadavky vstupního iterátoru STL.

[Platform::Collections::VectorIterator – třída](../cppcx/platform-collections-vectoriterator-class.md)<br/>
Iterátor STL, který splňuje požadavky aplikace STL proměnlivý iterátor s náhodným přístupem.

[Platform::Collections::VectorViewIterator – třída](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
Iterátor STL, který splňuje požadavky iterátoru náhodného přístupu `const` STL.

### <a name="begin-and-end-functions"></a>funkce begin () a end ()

Pro zjednodušení použití `Vector`STL pro zpracování, `VectorView`, `Map` `MapView`, `Windows::Foundation::Collections` a libovolných objektů podporuje/CX/CX přetížení C++ [funkcí Begin](../cppcx/begin-function.md) a [koncových funkcí](../cppcx/end-function.md) , které nečlení. POZVYHLEDAT.

V následující tabulce jsou uvedené dostupné iterátory a funkce.

|Iterátory|Funkce|
|---------------|---------------|
|[Platform:: Collections::\<VectorIterator T >](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Interně [ukládá Windows:: Foundation:: Collections:: IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) a int.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md)([Windows::Foundation::Collections:: IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_))|
|[Platform:: Collections::\<VectorViewIterator T >](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Interně [ukládá\<IVectorView T >](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)^ a int.)|[](../cppcx/begin-function.md)Begin/ [End](../cppcx/end-function.md) ([IVectorViewT\<>](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)^)|
|[Platform:: Collections::\<InputIterator T >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně [ukládá\<IIterator T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ a T)|[](../cppcx/begin-function.md)Begin/ [End](../cppcx/end-function.md) ([IIterableT\<>](/uwp/api/Windows.Foundation.Collections.IIterable_T_))|
|[Platform::Collections::InputIterator<IKeyValuePair\<K, V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně [ukládá\<IIterator T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ a T)|[](../cppcx/begin-function.md)Begin/ [End](../cppcx/end-function.md) ([IMAPK\<, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).|
|[Platform::Collections::InputIterator<IKeyValuePair\<K, V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně [ukládá\<IIterator T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ a T)|[](../cppcx/begin-function.md)Begin/ [End](../cppcx/end-function.md) ([Windows:: Foundation:: Collections:: IMapView]/UWP/API/Windows.Foundation.Collections.IMapView_K_V_))|

### <a name="collection-change-events"></a>Události změny kolekce

`Vector`a `Map` podporují vazby v kolekcích XAML implementací událostí, ke kterým dochází při změně nebo obnovení objektu kolekce, nebo při vložení, odebrání nebo změně jakéhokoliv prvku kolekce. Můžete napsat vlastní typy, které podporují datovou vazbu, i když nemůžete `Vector` dědit z `Map` nebo, protože tyto typy jsou zapečetěné.

Delegáty [Windows:: Foundation:: Collections:: VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler) a [Windows:: Foundation:: Collections:: MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler) určují signatury obslužných rutin událostí pro události změny kolekce. Třídy s veřejným výčtem [Windows:: Foundation:: Collections:: CollectionChange](/uwp/api/windows.foundation.collections.collectionchange) a `Platform::Collection::Details::MapChangedEventArgs` `Platform::Collections::Details::VectorChangedEventArgs` ref class, uložte argumenty události, abyste zjistili, co způsobilo událost. Typy jsou definovány `Details` v oboru názvů, protože nemusíte je vytvářet ani je nespotřebovávat explicitně při použití `Map` nebo `Vector`. `*EventArgs`

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
