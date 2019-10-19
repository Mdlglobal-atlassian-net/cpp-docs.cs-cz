---
title: Kolekce (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: ff3fb9899355ec05083dc15c16d74c9aa1d3fd8f
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "70740321"
---
# <a name="collections-ccx"></a>Kolekce (C++/CX)

V programu C++/CX můžete využít bezplatné použití kontejnerů knihovny STL (Standard Template Library) nebo jakýkoli jiný uživatelem definovaný typ kolekce. Pokud však předáte kolekce zpátky a zpátky v binárním rozhraní aplikace prostředí Windows Runtime (ABI) – například na ovládací prvek XAML nebo na klienta jazyka JavaScript – je nutné použít typy kolekce prostředí Windows Runtime.

Prostředí Windows Runtime definuje rozhraní pro kolekce a související typy a C++/CX poskytuje konkrétní C++ implementace v souboru hlaviček Collection. h. Tento obrázek znázorňuje vztahy mezi typy kolekce:

![Strom&#43;&#43;&#47;dědičnosti C CX pro typy kolekcí](../cppcx/media/cppcxcollectionsinheritancetree.png "Strom&#43;&#43;&#47;dědičnosti C CX pro typy kolekcí")

- [Třída Platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) se podobá [třídě std:: Vector](../standard-library/vector-class.md).

- Třída [Platform:: Collections:: map](../cppcx/platform-collections-map-class.md) se podobá [třídě std:: map](../standard-library/map-class.md).

- [Platform:: Collections:: VectorView Class](../cppcx/platform-collections-vectorview-class.md) a[Platform:: Collections:: MapView](../cppcx/platform-collections-mapview-class.md) jsou verze `Vector` a `Map` jen pro čtení.

- Iterátory jsou definovány v [oboru názvů Platform:: Collections](../cppcx/platform-collections-namespace.md). Tyto iterátory splňují požadavky na iterátory STL a umožňují použití algoritmů [std:: Find](../standard-library/algorithm-functions.md#find), [std:: count_if](../standard-library/algorithm-functions.md#count_if)a dalších algoritmů STL na libovolných typech rozhraní [Windows:: Foundation:: Collections](/uwp/api/windows.foundation.collections) nebo [Platform:: Collections.](../cppcx/platform-collections-namespace.md) konkrétní typ. Například to znamená, že můžete iterovat kolekci ve prostředí Windows Runtime komponentě, která je vytvořena v C# a použít pro ni algoritmus STL.

   > [!IMPORTANT]
   > Iterátory proxy `VectorIterator` a `VectorViewIterator` využívají proxy objekty `VectoryProxy<T>` a `ArrowProxy<T>`, aby bylo možné použití s kontejnery STL. Další informace naleznete v části "VectorProxy elementy" dále v tomto článku.

- Typy C++kolekce/CX podporují stejné záruky bezpečnosti vlákna, které podporují kontejnery STL.

- [Windows:: Foundation:: Collections:: IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) a [Windows:: Foundation:: Collections:: IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) definují události, které se aktivují, když se kolekce mění různými způsoby. Implementací těchto rozhraní [Platform:: Collections:: map](../cppcx/platform-collections-map-class.md) a [Platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) podporují datovou vazbu s kolekcemi XAML. Například pokud máte `Vector`, které jsou vázány na data `Grid`, když přidáte položku do kolekce, projeví se změna v uživatelském rozhraní mřížky.

## <a name="vector-usage"></a>Využití vektoru

Pokud vaše třída musí předat kontejneru sekvence jiné součásti prostředí Windows Runtime, použijte [Windows:: Foundation:: Collections:: IVector \<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) jako parametr nebo návratový typ a [Platform:: Collections:: Vector \<T >](../cppcx/platform-collections-vector-class.md) jako konkrétní implementace. Pokud se pokusíte použít typ `Vector` ve veřejné návratové hodnotě nebo parametru, bude vyvolána chyba kompilátoru C3986. Chybu můžete opravit změnou `Vector` na `IVector`.

> [!IMPORTANT]
> Pokud předáváte sekvenci ve vlastním programu, použijte buď `Vector`, nebo `std::vector`, protože jsou efektivnější než `IVector`. @No__t_0 použijte pouze v případě, že předáte kontejner napříč ABI.
>
> Systém typů prostředí Windows Runtime nepodporuje koncept vícenásobných polí, a proto nelze předat IVector < Platform:: Array \<T > > jako návratovou hodnotu nebo parametr metody. Chcete-li předat vícenásobné pole nebo sekvenci sekvencí v rámci ABI, použijte `IVector<IVector<T>^>`.

`Vector<T>` poskytuje metody, které jsou požadovány pro přidání, odebrání a přístup k položkám v kolekci a je implicitně převoditelná na `IVector<T>`. Můžete také použít algoritmy STL na instancích `Vector<T>`. Následující příklad znázorňuje základní použití. [Funkce Begin](../cppcx/begin-function.md) a [End Function](../cppcx/end-function.md) tady je z oboru názvů `Platform::Collections`, nikoli z oboru názvů `std`.

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

Pokud máte existující kód, který používá `std::vector` a chcete ho znovu použít v komponentě prostředí Windows Runtime, stačí použít jeden z konstruktorů `Vector`, které přebírají `std::vector` nebo dvojici iterátory k sestavení `Vector` v místě, kde předáte kolekci. v rámci ABI. Následující příklad ukazuje, jak použít konstruktor `Vector` Move pro efektivní inicializaci z `std::vector`. Po operaci přesunu již není původní proměnná `vec` platná.

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

Pokud máte vektor řetězců, které je nutné předat v rámci určitého budoucího bodu, musíte se rozhodnout, zda chcete vytvořit řetězce původně jako `std::wstring` typy nebo jako `Platform::String^` typů. Pokud je nutné provést v řetězcích velké množství zpracování, použijte `wstring`. V opačném případě vytvořte řetězce jako `Platform::String^` typy a vyhněte se nákladům na jejich převod později. Také je nutné rozhodnout, zda mají být tyto řetězce vloženy do `std:vector` nebo `Platform::Collections::Vector` interně. Obecně je vhodné použít `std::vector` a pak vytvořit `Platform::Vector` z něj pouze v případě, že předáte kontejner v rámci ABI.

## <a name="value-types-in-vector"></a>Typy hodnot v vektoru

Všechny prvky, které mají být uloženy v [Platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) , musí podporovat porovnání rovnosti implicitně nebo pomocí vlastního typu [std:: equal_to](../standard-library/equal-to-struct.md) komparátor, který zadáte. Všechny typy odkazů a všechny skalární typy implicitně podporují porovnání rovnosti. Pro neskalární typy hodnot, jako je například [Windows:: Foundation::D atetime](/uwp/api/windows.foundation.datetime)nebo pro vlastní porovnávání – například `objA->UniqueID == objB->UniqueID`, je nutné zadat objekt vlastní funkce.

## <a name="vectorproxy-elements"></a>VectorProxy elementy

[Platform:: Collections:: VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) a [Platform:: Collections:: VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) povolí použití smyček `range for` a algoritmů, jako je například [std:: sort](../standard-library/algorithm-functions.md#sort) pomocí kontejneru [IVector \<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) . Ale k elementům `IVector` nelze přistoupit prostřednictvím C++ zpětného odkazování ukazatele; k nim lze přistupovat pouze prostřednictvím metod [GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) a [SetAt](/uwp/api/windows.foundation.collections.ivector-1.setat) . Proto tyto iterátory používají třídy proxy `Platform::Details::VectorProxy<T>` a `Platform::Details::ArrowProxy<T>` k poskytnutí přístupu k jednotlivým prvkům prostřednictvím operátorů __\*__ , __->__ a __\[]__ , jak je vyžadováno standardní knihovnou. V případě, že `IVector<Person^> vec`, je typ `*begin(vec)` `VectorProxy<Person^>`. Objekt proxy je však téměř vždy transparentní pro váš kód. Tyto objekty proxy nejsou zdokumentovány, protože jsou pouze pro interní použití iterátory, ale je užitečné zjistit, jak mechanismus funguje.

Použijete-li smyčku `range for` přes `IVector` kontejnery, použijte `auto&&` k povolení správné vazby proměnné iterátoru na `VectorProxy` elementy. Použijete-li `auto` nebo `auto&`, je vyvolána C4239 upozornění kompilátoru a v textu upozornění je uvedeno `VectoryProxy`.

Na následujícím obrázku je znázorněna `range for`ová smyčka přes `IVector<Person^>`. Všimněte si, že provádění je zastaveno na zarážce na řádku 64. Okno **QuickWatch** ukazuje, že proměnná iterátoru `p` je ve skutečnosti `VectorProxy<Person^>`, která má `m_v` a `m_i` členské proměnné. Nicméně při volání `GetType` u této proměnné vrátí stejný typ jako `p2` instance `Person`. Poznatkem je, že i když se `VectorProxy` a `ArrowProxy` mohou objevit v **QuickWatch**, ladicí program některé chyby kompilátoru nebo jiná místa, obvykle nemusíte pro ně explicitně kódovat kód.

![VectorProxy v rozsahu&#45;založeném na smyčce](../cppcx/media/vectorproxy-1.png "VectorProxy v rozsahu&#45;založeném na smyčce")

Jeden scénář, ve kterém je nutné kód kolem objektu proxy, je v případě, že je nutné provést `dynamic_cast` na prvcích, například při hledání objektů XAML určitého typu v kolekci elementů `UIElement`. V takovém případě je nutné nejprve přetypovat element na [Platform:: Object](../cppcx/platform-object-class.md)^ a pak provést dynamické přetypování:

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

Tento příklad ukazuje, jak vložit položky a vyhledat je v objektu [Platform:: Collections:: map](../cppcx/platform-collections-map-class.md)a pak vrátit `Map` jako typ jen pro čtení [Windows:: Foundation:: Collections:: IMapView]/UWP/API/Windows.Foundation.Collections.IMapView_K_V_).

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

Obecně platí, že pro funkce interní mapy preferovat `std::map` typ z hlediska výkonu. Pokud je nutné předat kontejner napříč ABI, sestavte [Platform:: Collections:: map](../cppcx/platform-collections-map-class.md) z [std:: map](../standard-library/map-class.md) a vraťte `Map` jako [Windows:: Foundation:: Collections:: IMAP](/uwp/api/Windows.Foundation.Collections.IMap_K_V_). Pokud se pokusíte použít typ `Map` ve veřejné návratové hodnotě nebo parametru, bude vyvolána chyba kompilátoru C3986. Chybu můžete opravit změnou `Map` na `IMap`. V některých případech – například pokud neprovádíte velký počet hledání nebo vkládání a často předáváte kolekci v rámci ABI, může být levnější použít `Platform::Collections::Map` od začátku a vyhnout se nákladům na převod `std::map`. V každém případě se vyhněte operacím vyhledávání a vkládání na `IMap`, protože se jedná o nejméně tyto tři typy. Převést na `IMap` pouze v bodě, který kontejner předává napříč ABI.

## <a name="value-types-in-map"></a>Typy hodnot v mapě

Prvky v objektu [Platform:: Collections:: map](../cppcx/platform-collections-map-class.md) jsou seřazené. Všechny prvky, které mají být uloženy v `Map`, musí podporovat méně než porovnání s přísným slabým řazením implicitně nebo pomocí vlastní [STL:: less](../standard-library/less-struct.md) komparátor, kterou zadáte. Skalární typy podporují porovnání implicitně. Pro neskalární typy hodnot, jako je například `Windows::Foundation::DateTime`, nebo pro vlastní porovnávání – například `objA->UniqueID < objB->UniqueID`, je třeba zadat vlastní komparátor.

## <a name="collection-types"></a>Typy kolekcí

Kolekce spadají do čtyř kategorií: upravitelné verze a verze kolekcí sekvencí a asociativní kolekce pouze pro čtení. Kromě toho C++/CX vylepšuje kolekce tím, že poskytuje tři třídy iterátoru, které zjednodušují přístup k kolekcím.

Prvky s upravitelnou kolekcí lze změnit, ale prvky kolekce jen pro čtení, které se označují jako *zobrazení*, lze číst pouze. K prvkům kolekce [Platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) nebo[Platform:: Collections:: VectorView](../cppcx/platform-collections-vectorview-class.md) lze přistupovat pomocí iterátoru nebo [vektoru kolekce:: GetAt](../cppcx/platform-collections-vector-class.md#getat) a indexu. K prvkům asociativní kolekce lze přistupovat pomocí [mapování:: Lookup](../cppcx/platform-collections-map-class.md#lookup) a Key.

[Platform::Collections::Map – třída](../cppcx/platform-collections-map-class.md)<br/>
Upravitelná, asociativní kolekce. Prvky mapy jsou páry klíč-hodnota. Vyhledání klíče pro načtení přidružené hodnoty a iterace všemi páry klíč-hodnota jsou podporovány.

`Map` a `MapView` jsou šablonou `<K, V, C = std::less<K>>`; Proto můžete přizpůsobit komparátor.  Kromě toho jsou `Vector` a `VectorView` šablonou `<T, E = std::equal_to<T>>`, takže můžete přizpůsobit chování `IndexOf()`. To je důležité hlavně pro `Vector` a `VectorView` struktur hodnot. Chcete-li například vytvořit vektor \<Windows:: Foundation::D ateTime >, je nutné zadat vlastní komparátor, protože DateTime neprovádí přetížení operátoru = =.

[Platform::Collections::MapView – třída](../cppcx/platform-collections-mapview-class.md)<br/>
Verze `Map` jen pro čtení.

[Platform::Collections::Vector – třída](../cppcx/platform-collections-vector-class.md)<br/>
Kolekce sekvencí s upravitelnou příponou. `Vector<T>` podporuje náhodný přístup s náhodným přístupem a operace [připojení](../cppcx/platform-collections-vector-class.md#append) s konstantním časem.

[Platform::Collections::VectorView – třída](../cppcx/platform-collections-vectorview-class.md)<br/>
Verze `Vector` jen pro čtení.

[Platform::Collections::InputIterator – třída](../cppcx/platform-collections-inputiterator-class.md)<br/>
Iterátor STL, který splňuje požadavky vstupního iterátoru STL.

[Platform::Collections::VectorIterator – třída](../cppcx/platform-collections-vectoriterator-class.md)<br/>
Iterátor STL, který splňuje požadavky aplikace STL proměnlivý iterátor s náhodným přístupem.

[Platform::Collections::VectorViewIterator – třída](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
Iterátor STL, který splňuje požadavky STL `const` iterátoru s náhodným přístupem.

### <a name="begin-and-end-functions"></a>funkce begin () a end ()

Pro zjednodušení použití aplikace STL pro zpracování `Vector`, `VectorView`, `Map`, `MapView` a libovolných `Windows::Foundation::Collections` objektů, C++/CX podporuje přetížení [funkcí Begin](../cppcx/begin-function.md) a [End Function](../cppcx/end-function.md) , které nečlení funkce.

V následující tabulce jsou uvedené dostupné iterátory a funkce.

|Iterátory|Funkce|
|---------------|---------------|
|[Platform:: Collections:: VectorIterator \<T >](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Interně ukládá [Windows:: Foundation:: Collections:: IVector \<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) a int.)|[začátek](../cppcx/begin-function.md) / [End](../cppcx/end-function.md)([Windows:: Foundation:: collections:: IVector \<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_))|
|[Platform:: Collections:: VectorViewIterator \<T >](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Interně ukládá [IVectorView \<T >](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)^ a int.)|[začátek](../cppcx/begin-function.md) / [end](../cppcx/end-function.md) ([IVectorView \<T >](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)^)|
|[Platform:: Collections:: InputIterator \<T >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [IIterator \<T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ a t.)|[začátek](../cppcx/begin-function.md) / [end](../cppcx/end-function.md) ([IIterable \<T >](/uwp/api/Windows.Foundation.Collections.IIterable_T_))|
|[Platform:: Collections:: InputIterator < IKeyValuePair \<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [IIterator \<T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ a t.)|[začátek](../cppcx/begin-function.md) / [end](../cppcx/end-function.md) ([IMAP \<K, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).|
|[Platform:: Collections:: InputIterator < IKeyValuePair \<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [IIterator \<T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ a t.)|[begin](../cppcx/begin-function.md) / [End](../cppcx/end-function.md) ([Windows:: Foundation:: Collections:: IMapView]/UWP/API/Windows.Foundation.Collections.IMapView_K_V_))|

### <a name="collection-change-events"></a>Události změny kolekce

`Vector` a `Map` podporují datovou vazbu v kolekcích XAML implementací událostí, ke kterým dochází při změně nebo obnovení objektu kolekce, nebo při vložení, odebrání nebo změně jakéhokoliv prvku kolekce. Můžete napsat vlastní typy, které podporují datovou vazbu, i když nemůžete dědit z `Map` nebo `Vector`, protože tyto typy jsou zapečetěné.

Delegáty [Windows:: Foundation:: Collections:: VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler) a [Windows:: Foundation:: Collections:: MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler) určují signatury obslužných rutin událostí pro události změny kolekce. Třídy s veřejným výčtem [Windows:: Foundation:: Collections:: CollectionChange](/uwp/api/windows.foundation.collections.collectionchange) a `Platform::Collection::Details::MapChangedEventArgs` a `Platform::Collections::Details::VectorChangedEventArgs` ref Classes, uložte argumenty události, abyste zjistili, co způsobilo událost. @No__t_0 typy jsou definovány v oboru názvů `Details`, protože nemusíte je vytvářet ani je nespotřebovávat explicitně při použití `Map` nebo `Vector`.

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
