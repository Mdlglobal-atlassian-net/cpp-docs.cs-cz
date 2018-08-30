---
title: Kolekce (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c174c904dfb43ff3fa3c032bae30da8c1e139c3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222897"
---
# <a name="collections-ccx"></a>Kolekce (C + +/ CX)
V jazyce C + +/ CX program, můžete provést bezplatné použití knihovny STL (Standard Template) kontejnerů nebo jakéhokoli jiného typu uživatelem definované kolekci. Ale při předání kolekce vpřed a zpět v prostředí Windows Runtime binárním rozhraním aplikace (ABI) – například do ovládacího prvku XAML nebo JavaScript klienta, je nutné použít typy Windows Runtime kolekcí.  
  
 Modul Windows Runtime definuje rozhraní pro kolekce a souvisejících typů a C + +/ CX poskytuje konkrétní implementace jazyka C++ v hlavičkovém souboru collection.h. Tento obrázek znázorňuje vztahy mezi typy kolekcí:  
  
 ![C&#43;&#43;&#47;CX strom dědičnosti pro typy kolekcí](../cppcx/media/cppcxcollectionsinheritancetree.png "CPPCXCollectionsInheritanceTree")  
  
-   [Platform::Collections:: Vector – třída](../cppcx/platform-collections-vector-class.md) vypadá podobně jako [std::vector třídy](../standard-library/vector-class.md).  
  
-   [Platform::Collections:: map – třída](../cppcx/platform-collections-map-class.md) třídy vypadá podobně jako [std::map třídy](../standard-library/map-class.md).  
  
-   [Platform::Collections:: vectorview – třída](../cppcx/platform-collections-vectorview-class.md) a[Platform::Collections:: mapview – třída](../cppcx/platform-collections-mapview-class.md) jsou jen pro čtení verze `Vector` a `Map`.  
  
-   Iterátory jsou definovány v [Platform::Collections – Namespace](../cppcx/platform-collections-namespace.md). Tyto iterátory splňovat požadavky na iterátory STL a umožňují použití [std::find](../standard-library/algorithm-functions.md#find), [std::count_if](../standard-library/algorithm-functions.md#count_if)a dalších algoritmů STL na žádném [Windows::Foundation:: Collections –](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.aspx) typ rozhraní nebo [Platform::Collections –](../cppcx/platform-collections-namespace.md) konkrétní typ. Například to znamená, že můžete iterovat kolekce v prostředí Windows Runtime komponenty, která je vytvořena v jazyce C# a aby u ní použil algoritmem STL.  
  
    > [!IMPORTANT]
    >  Iterátory proxy `VectorIterator` a `VectorViewIterator` využívají objekty proxy `VectoryProxy<T>` a `ArrowProxy<T>` umožňující použití s kontejnery STL. Další informace najdete v tématu "VectorProxy prvky" dále v tomto článku.  
  
-   C + +/ CX kolekci typů podporu stejné zabezpečení vlákna zaručuje, že podporuje kontejnery STL.  
  
-   [Windows::Foundation::Collections::IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) a [Windows::Foundation::Collections::IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) definovat události, které jsou aktivovány, pokud se změní kolekce různými způsoby. Implementací těchto rozhraní [Platform::Collections:: map –](../cppcx/platform-collections-map-class.md) a [Platform::Collections:: Vector –](../cppcx/platform-collections-vector-class.md) podporují vazby dat s kolekcí XAML. Například, pokud máte `Vector` , který je vázán na data `Grid`, při přidání položky do kolekce, změny se projeví v Uživatelském rozhraní mřížky.  
  
## <a name="vector-usage"></a>Vektor využití  
 Pokud vaše třída má předat pořadí kontejneru na jiné součásti prostředí Windows Runtime, použijte [Windows::Foundation:: Collections –:: IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx) jako parametr nebo návratový typ a [platformy:: Collections::Vector\<T >](../cppcx/platform-collections-vector-class.md) jako konkrétní implementaci. Pokud se pokusíte použít `Vector` zadejte veřejné návratová hodnota nebo parametr, C3986, bude vyvolána chyba kompilátoru. Chybu můžete vyřešit tak, že změníte `Vector` do `IVector`.  
  
> [!IMPORTANT]
>  Pokud předáváte sekvenci v rámci vlastní aplikace, použijte buď `Vector` nebo `std::vector` vzhledem k tomu, že jsou účinnější než `IVector`. Použití `IVector` pouze při předání kontejneru napříč ABI.  
>   
>  Systém typů prostředí Windows Runtime nepodporuje konceptu Vícenásobná pole a proto nelze předat IVector < Platform::Array\<T >> jako návratovou hodnotu nebo metoda parametr. Vícenásobné pole nebo sekvence sekvencí předejte ABI, použijte `IVector<IVector<T>^>`.  
  
 `Vector<T>` poskytuje metody, které jsou požadovány pro přidání, odebrání a přístup k položky v kolekci a je implicitně převést na `IVector<T>`. Algoritmy STL můžete použít také v instancích systému `Vector<T>`. Následující příklad ukazuje některé základní informace o využití. [Begin – funkce](../cppcx/begin-function.md) a [end – funkce](../cppcx/end-function.md) tady jsou z `Platform::Collections` obor názvů, ne `std` oboru názvů.  
  
 [!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]  
  
 Pokud máte existující kód, který používá `std::vector` a chcete ji znovu použít v součásti prostředí Windows Runtime, prostě použijte jednu z `Vector` konstruktory, které přijímá `std::vector` nebo pár iterátorů k vytvoření `Vector` v místě, kde můžete předat shromažďování napříč ABI. Následující příklad ukazuje způsob použití `Vector` pro efektivní inicializace z konstruktor přesunu `std::vector`. Po operaci přesunutí, původní `vec` proměnné již není platný.  
  
 [!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]  
  
 Pokud máte vektor řetězce, které musí projít přes ABI v určitém okamžiku budoucí, musíte se rozhodnout, zda k vytvoření řetězce zpočátku jako `std::wstring` typů nebo jako `Platform::String^` typy. Pokud musíte udělat spoustu zpracování na řetězce, použijte `wstring`. V opačném případě vytváření řetězců jako `Platform::String^` typy a vyhnout se náklady na jejich konverze později. Musíte se rovněž rozhodnout, jestli se má vložit do těchto řetězců `std:vector` nebo `Platform::Collections::Vector` interně. Obecně platí, použijte `std::vector` a pak vytvořte `Platform::Vector` z něj pouze v případě, že předáte napříč ABI kontejneru.  
  
## <a name="value-types-in-vector"></a>Typy hodnot ve vektoru  
 Libovolný element, který bude uložen do [Platform::Collections:: Vector –](../cppcx/platform-collections-vector-class.md) musí podporovat porovnání rovnosti, implicitně nebo pomocí vlastní [std::equal_to](../standard-library/equal-to-struct.md) Komparátor, který zadáte. Všechny typy odkazů a všech skalárních typů implicitně podporu porovnání rovnosti. Pro neskalární typů hodnot, jako [Windows::Foundation::DateTime](https://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx), nebo vlastní porovnávání – například `objA->UniqueID == objB->UniqueID`– je nutné zadat vlastní funkce objektu.  
   
  
## <a name="vectorproxy-elements"></a>VectorProxy elementy  
 [Platform::Collections:: vectoriterator –](../cppcx/platform-collections-vectoriterator-class.md) a [Platform::Collections:: vectorviewiterator –](../cppcx/platform-collections-vectorviewiterator-class.md) povolit použití `range for` smyčky a algoritmy, jako je [std::sort](../standard-library/algorithm-functions.md#sort) s [ IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx) kontejneru. Ale `IVector` elementy se nedá přistupovat prostřednictvím C++ přesměrování ukazatele; k nim může přistupovat pouze prostřednictvím [GetAt](https://msdn.microsoft.com/library/windows/apps/br206634.aspx) a [SetAt](https://msdn.microsoft.com/library/windows/apps/br206642.aspx) metody. Proto tyto iterátory použít třídy proxy `Platform::Details::VectorProxy<T>` a `Platform::Details::ArrowProxy<T>` pro poskytnutí přístupu k jednotlivým prvkům prostřednictvím `*`, `->`, a `[]` operátory znamének podle STL. Přesněji řečeno, vzhledem `IVector<Person^> vec`, typ `*begin(vec)` je `VectorProxy<Person^>`. Objekt proxy je však téměř vždy transparentního kódu. Tyto objekty proxy nejsou uvedené, protože jsou pouze pro interní použití rozhraním iterátory, ale je vhodné vědět, jak funguje mechanismus.  
  
 Při použití `range for` ve smyčce `IVector` kontejnery, používají `auto&&` umožňující proměnná iterátoru pro vazbu správně na `VectorProxy` elementy. Pokud používáte `auto` nebo `auto&`, je vyvolána C4239 upozornění kompilátoru a `VectoryProxy` je uvedený v textu upozornění.  
  
 Následující ilustrace ukazuje `range for` ve smyčce `IVector<Person^>`. Všimněte si, že na zarážku na řádku 64 zastavením spuštění. **QuickWatch** okno zobrazuje proměnná iterátoru `p` ve skutečnosti `VectorProxy<Person^>` , který má `m_v` a `m_i` členské proměnné. Ale při volání `GetType` na tuto proměnnou, vrátí stejné typ, který má `Person` instance `p2`. Je hlavní, co vyplývá, že ačkoli `VectorProxy` a `ArrowProxy` se může objevit **QuickWatch**, ladicí program některých chyb kompilátoru, nebo z jiných míst, obvykle není nutné je explicitně kód.  
  
 ![VectorProxy v rozsahu&#45;u smyčky založených na](../cppcx/media/vectorproxy-1.png "VectorProxy_1")  
  
 Jeden scénář, ve kterém budete muset kód kolem objektu proxy serveru je, když je nutné provést `dynamic_cast` na prvcích – například při hledání pro objekty určitého typu v XAML `UIElement` kolekci elementů. V takovém případě musíte nejdříve přetypována elementu, který chcete [Platform::Object](../cppcx/platform-object-class.md)^ a pak proveďte dynamické přetypování:  
  
```  
  
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
 Tento příklad ukazuje, jak vložit položky a nich vyhledávat [Platform::Collections:: map –](../cppcx/platform-collections-map-class.md)a pak se vraťte `Map` jako jen pro čtení [Windows::Foundation::Collections::IMapView] / UPW/api / Typ Windows.Foundation.Collections.IMapView_K_V_).  
  
 [!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]  
  
 Obecně platí, pro funkce interní mapy, raději `std::map` typ z důvodů výkonu. Pokud musíte předat kontejneru napříč ABI, sestavit [Platform::Collections:: map –](../cppcx/platform-collections-map-class.md) z [std::map](../standard-library/map-class.md) a vraťte se `Map` jako [Windows::Foundation –:: Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_). Pokud se pokusíte použít `Map` zadejte veřejné návratová hodnota nebo parametr, C3986, bude vyvolána chyba kompilátoru. Chybu můžete vyřešit tak, že změníte `Map` do `IMap`. V některých případech, například, pokud nejsou Příprava velký počet vyhledávání nebo vložení a kolekce jsou předávání přes ABI často – je možné, snižuje náklady na použití `Platform::Collections::Map` od začátku a vyhnout se náklady na převod `std::map`. V každém případě vyhnout vyhledávání a operací vložení na `IMap` vzhledem k tomu, že jedná se o nejméně výkonné ze tří typů. Převést na `IMap` pouze v případě, že předáte kontejneru napříč ABI.  
  
## <a name="value-types-in-map"></a>Typy hodnot v mapě  
 Prvky [Platform::Collections:: map –](../cppcx/platform-collections-map-class.md) jsou seřazeny. Libovolný element, který bude uložen do `Map` musí podporovat menší – než porovnání s přísné slabé seřazení, implicitně nebo pomocí vlastní [stl::less](../standard-library/less-struct.md) Komparátor, který zadáte. Skalární typy implicitně podporují porovnání. Pro neskalární typů hodnot, jako `Windows::Foundation::DateTime`, nebo vlastní porovnávání – například `objA->UniqueID < objB->UniqueID`– je nutné zadat vlastní porovnání.  
  
## <a name="collection-types"></a>Typy kolekcí  
 Kolekce se dělí do čtyř kategorií: upravitelná verze a verze jen pro čtení pořadí kolekcí a asociativní kolekce. Kromě toho, C + +/ CX vylepšuje kolekce tím, že poskytuje tři třídy iterátoru, které usnadňují přístup ke kolekcím. 
  
 Prvky lze měnit kolekci mohou být změněny, ale elementy z kolekce jen pro čtení, která se nazývá *zobrazení*, lze pouze číst. Prvky [Platform::Collections:: Vector –](../cppcx/platform-collections-vector-class.md) nebo[Platform::Collections:: vectorview –](../cppcx/platform-collections-vectorview-class.md) kolekce lze přistupovat pomocí iterátoru nebo kolekce [Vector::GetAt](../cppcx/platform-collections-vector-class.md#getat) a indexu. Prvky asociativní kolekce lze přistupovat pomocí kolekce [Map::Lookup](../cppcx/platform-collections-map-class.md#lookup) a klíč.  
  
 [Platform::Collections::Map – třída](../cppcx/platform-collections-map-class.md)  
 Upravitelné, asociativní kolekce. Elementy jsou páry klíč hodnota. Vyhledání klíče a získejte její přidružené hodnoty a provede iterace přes všechny páry klíč hodnota, jsou podporované.  
  
 `Map` a `MapView` jsou bez vizuálního vzhledu na `<K, V, C = std::less<K>>`; proto Komparátor, který můžete přizpůsobit.  Kromě toho `Vector` a `VectorView` jsou bez vizuálního vzhledu na `<T, E = std::equal_to<T>>` tak, aby si můžete přizpůsobit chování `IndexOf()`. To je důležité hlavně `Vector` a `VectorView` hodnotu struktur. Například pro vytvoření vektoru\<Windows::Foundation::DateTime >, je nutné zadat vlastní Komparátor, protože data a času nepřetěžuje == – operátor.  
  
 [Platform::Collections::MapView – třída](../cppcx/platform-collections-mapview-class.md)  
 Verze jen pro čtení `Map`.  
  
 [Platform::Collections::Vector – třída](../cppcx/platform-collections-vector-class.md)  
 Kolekce lze měnit pořadí. `Vector<T>` podporuje konstantním čase náhodný přístup a amortizovaných času konstanty [připojit](../cppcx/platform-collections-vector-class.md#append) operace...  
  
 [Platform::Collections::VectorView – třída](../cppcx/platform-collections-vectorview-class.md)  
 Verze jen pro čtení `Vector`.  
  
 [Platform::Collections::InputIterator – třída](../cppcx/platform-collections-inputiterator-class.md)  
 Iterátor STL, které splňuje požadavky na vstupní iterátor STL.  
  
 [Platform::Collections::VectorIterator – třída](../cppcx/platform-collections-vectoriterator-class.md)  
 Iterátor STL, který splňuje požadavky na iterátor STL proměnlivé náhodného přístupu.  
  
 [Platform::Collections::VectorViewIterator – třída](../cppcx/platform-collections-vectorviewiterator-class.md)  
 Iterátor STL, který splňuje požadavky STL `const` iterátor s náhodným přístupem.  
  
### <a name="begin-and-end-functions"></a>Funkce begin() a end()  
 Pro zjednodušení používá STL zpracovat `Vector`, `VectorView`, `Map`, `MapView`a libovolné `Windows::Foundation::Collections` objekty, C + +/ CX podporuje přetížení [begin – funkce](../cppcx/begin-function.md) a [end Funkce](../cppcx/end-function.md) nečlenské funkce.  
  
 V následující tabulce jsou uvedeny dostupné iterátory a funkce.  
  
|Iterátory|Funkce|  
|---------------|---------------|  
|[Platform::Collections:: vectoriterator –\<T >](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Interně ukládá [Windows::Foundation:: Collections –:: IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx) a int)|[Začněte](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md)([Windows::Foundation:: Collections –:: IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx))|  
|[Platform::Collections:: vectorviewiterator –\<T >](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Interně ukládá [IVectorView\<T >](https://msdn.microsoft.com/library/windows/apps/br226058.aspx)^ a int)|[Začněte](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IVectorView\<T >](https://msdn.microsoft.com/library/windows/apps/br226058.aspx)^)|  
|[Platform::Collections:: inputiterator –\<T >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [IIterator\<T >](https://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ a T.)|[Začněte](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IIterable\<T >](https://msdn.microsoft.com/library/windows/apps/br226024.aspx))|  
|[Platform::Collections:: inputiterator – < IKeyValuePair\<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [IIterator\<T >](https://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ a T.)|[Začněte](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IMap\<K, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).|  
|[Platform::Collections:: inputiterator – < IKeyValuePair\<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [IIterator\<T >](https://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ a T.)|[Začněte](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([Windows:: Foundation::Collections::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_))|  
  
### <a name="collection-change-events"></a>Události změny kolekce  
 `Vector` a `Map` podporují datové vazby v kolekcích XAML pomocí implementace události, ke kterým dochází, když se změní objekt kolekce nebo obnovení, nebo při vložení libovolný prvek v kolekci, odebrat nebo změnit. Můžete napsat vlastní typy databinding této podpory, i když nemůže dědit z `Map` nebo `Vector` vzhledem k tomu, že tyto typy jsou zapečetěné.  
  
 [Windows::Foundation::Collections::VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler) a [Windows::Foundation::Collections::MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler) delegáti určit podpisy pro obslužné rutiny událostí pro události změny kolekce. [Windows::Foundation::Collections::CollectionChange](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx) veřejný výčet tříd a `Platform::Collection::Details::MapChangedEventArgs` a `Platform::Collections::Details::VectorChangedEventArgs` referenční třídy uložit argumenty události, které mají určit, co způsobilo události. *`EventArgs` Typy jsou definovány `Details` obor názvů vzhledem k tomu není nutné vytvořit nebo je při použití explicitně využívat `Map` nebo `Vector`.  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Vestavěné typy](https://msdn.microsoft.com/acc196fd-09da-4882-b554-6c94685ec75f)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)