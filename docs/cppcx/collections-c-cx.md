---
title: Kolekce (C + +/ CX) | Microsoft Docs
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
caps.latest.revision: "35"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c97a264488e8b382091b24cdef8faae4c7bbfc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="collections-ccx"></a>Kolekce (C + +/ CX)
V jazyce C + +/ CX programu, můžete provést volné použijte standardní šablona knihovny (STL) kontejnery nebo jakýkoli jiný typ uživatelem definované kolekci. Ale pokud předáte kolekce a zpět přes rozhraní binární aplikace Windows Runtime (ABI) – například do ovládacího prvku XAML nebo klienta JavaScript – je nutné použít prostředí Windows Runtime typy kolekcí.  
  
 Prostředí Windows Runtime definuje rozhraní pro kolekce a souvisejících typů a C + +/ CX poskytuje konkrétní implementace C++ v záhlaví souboru collection.h. Tento obrázek znázorňuje vztahy mezi typy kolekcí:  
  
 ![C & č. 43; & č. 43; &#47; Stromu dědičnosti CX pro typy kolekcí](../cppcx/media/cppcxcollectionsinheritancetree.png "CPPCXCollectionsInheritanceTree")  
  
-   [Platform::Collections::Vector třída](../cppcx/platform-collections-vector-class.md) vypadá takto: [std::vector třída](../standard-library/vector-class.md).  
  
-   [Platform::Collections::Map třída](../cppcx/platform-collections-map-class.md) vypadá takto: Třída [std::map třída](../standard-library/map-class.md).  
  
-   [Třída Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) a[Platform::Collections::MapView třída](../cppcx/platform-collections-mapview-class.md) jsou jen pro čtení verzích `Vector` a `Map`.  
  
-   Iterátory jsou definovány v [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md). Tyto iterátory splňují požadavky pro STL iterátory a povolte použití [std::find](../standard-library/algorithm-functions.md#find), [std::count_if](../standard-library/algorithm-functions.md#count_if)a dalších algoritmů STL na žádném [Windows::Foundation::Collections](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.aspx) typ rozhraní nebo [Platform::Collections](../cppcx/platform-collections-namespace.md) konkrétní typ. Například to znamená, že můžete postup opakovat kolekci v prostředí Windows Runtime komponenty, která je vytvořena v jazyce C# a použije algoritmus STL na ni.  
  
    > [!IMPORTANT]
    >  Iterátory proxy `VectorIterator` a `VectorViewIterator` využívat objekty proxy `VectoryProxy<T>` a `ArrowProxy<T>` povolit využití s kontejnery STL. Další informace najdete v tématu "VectorProxy prvků" dále v tomto článku.  
  
-   C + +/ CX kolekce typy podporu stejné zabezpečení vlákna zaručuje, že kontejnery STL podporují.  
  
-   [Windows::Foundation::Collections::IObservableVector](http://msdn.microsoft.com/library/windows/apps/br226052.aspx) a [Windows::Foundation::Collections::IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) definovat události, které jsou aktivována, jestliže kolekci změní různými způsoby. Implementací těchto rozhraní [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) a [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) podporu vazby dat s kolekcí XAML. Pokud máte například `Vector` , je vázané na data k `Grid`, když přidat položku do kolekce, změny se projeví v uživatelském rozhraní mřížky.  
  
## <a name="vector-usage"></a>Vektor využití  
 Pokud vaše třída má předat kontejner pořadí jiné komponenty prostředí Windows Runtime, použijte [Windows::Foundation::Collections:: IVector\<T >](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) jako parametr nebo návratový typ a [platformy:: Collections::Vector\<T >](../cppcx/platform-collections-vector-class.md) jako konkrétní implementace. Pokud pokus o použití `Vector` zadejte veřejný návratovou hodnotu nebo parametr, Chyba kompilátoru C3986, bude vyvolána. Můžete je chyba vyřešit změnou `Vector` k `IVector`.  
  
> [!IMPORTANT]
>  Pokud předáte posloupnost v rámci vlastní program, použijte buď `Vector` nebo `std::vector` protože jsou efektivnější než `IVector`. Použití `IVector` pouze při předání kontejneru napříč ABI.  
>   
>  Systém typů prostředí Windows Runtime nepodporuje koncept Vícenásobná pole a proto nemůžete předat IVector < Platform::Array\<T >> jako návratový parametr hodnotu nebo metoda. Chcete-li předat Vícenásobná pole nebo posloupnost pořadí napříč ABI, použijte `IVector<IVector<T>^>`.  
  
 `Vector<T>`poskytuje metody, které jsou požadovány pro přidání, odebrání a přístup k položky v kolekci a je implicitně převést na `IVector<T>`. Můžete použít také STL algoritmy na instancích `Vector<T>`. Následující příklad ukazuje některé základní informace o využití. [Začít funkce](../cppcx/begin-function.md) a [ukončení funkce](../cppcx/end-function.md) tady jsou z `Platform::Collections` obor názvů, není `std` oboru názvů.  
  
 [!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]  
  
 Pokud máte existující kód, který používá `std::vector` a chcete ji znovu použít v prostředí Windows Runtime komponentě, použijte jednu z `Vector` konstruktorů, které přebírají `std::vector` nebo pár iterátory vytvořit `Vector` v místě, kde můžete předat kolekce napříč ABI. Následující příklad ukazuje, jak používat `Vector` přesunout konstruktor pro efektivní inicializace z `std::vector`. Po operaci přesunutí, původní `vec` proměnná již není platný.  
  
 [!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]  
  
 Pokud máte vektoru řetězců, které musí uplynout mezi ABI budoucí někde, musíte se rozhodnout, zda chcete-li vytvořit řetězce původně jako `std::wstring` typy nebo jako `Platform::String^` typy. Pokud je nutné provést spoustu zpracování na řetězce, použijte `wstring`. Vytvoření, jinak hodnota řetězce jako `Platform::String^` typy a vyhnout se náklady na jejich převodu později. Musíte také rozhodnout, zda se umístí do tyto řetězce `std:vector` nebo `Platform::Collections::Vector` interně. Z hlediska obecné použít `std::vector` a pak vytvořte `Platform::Vector` z něj jenom v případě, že předáváte kontejneru napříč ABI.  
  
## <a name="value-types-in-vector"></a>Typy hodnot u funkce Vector  
 Libovolný element, který má být uložen v [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) musí podporovat porovnání rovnosti implicitně nebo pomocí vlastní [std::equal_to](../standard-library/equal-to-struct.md) Komparátor, který zadáte. Všechny typy odkazů a všechny Skalární typy implicitně podporují porovnání rovnosti. Pro neskalární hodnoty typy [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx), nebo pro vlastní porovnání – například `objA->UniqueID == objB->UniqueID`– je třeba zadat objekt vlastní funkce.  
   
  
## <a name="vectorproxy-elements"></a>VectorProxy elementy  
 [Platform::Collections::VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) a [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) povolit používání `range for` smyčky a algoritmy jako [std::sort](../standard-library/algorithm-functions.md#sort) s [IVector\<T >](http://msdn.microsoft.com/en-us/library/windows/apps/br206631.aspx) kontejneru. Ale `IVector` elementy nelze získat přístup prostřednictvím C++ zrušení ukazatele; nim měly přístup jenom prostřednictvím [GetAt](http://msdn.microsoft.com/library/windows/apps/br206634.aspx) a [SetAt](http://msdn.microsoft.com/library/windows/apps/br206642.aspx) metody. Proto tyto iterátory použít třídy proxy `Platform::Details::VectorProxy<T>` a `Platform::Details::ArrowProxy<T>` k poskytování přístupu k jednotlivých prvků prostřednictvím `*`, `->`, a `[]` operátory podle požadavků STL. Přesněji řečeno, vzhledem `IVector<Person^> vec`, typ `*begin(vec)` je `VectorProxy<Person^>`. Objekt proxy serveru je však téměř vždy pro váš kód transparentní. Tyto objekty proxy serveru nejsou popsané, protože jsou pouze pro interní použití rozhraním iterátory, ale je dobré vědět, jak funguje mechanismus.  
  
 Při použití `range for` smyčku `IVector` kontejnery, použijte `auto&&` povolit proměnnou iterator pro vazbu správně na `VectorProxy` elementy. Pokud používáte `auto` nebo `auto&`, C4239 se vyvolá upozornění kompilátoru a `VectoryProxy` je uveden v textu upozornění.  
  
 Následující obrázek znázorňuje `range for` smyčku `IVector<Person^>`. Všimněte si, že je na zarážek na řádku 64 zastavená provádění. **QuickWatch** okno ukazuje, že proměnná iterator `p` je ve skutečnosti `VectorProxy<Person^>` s `m_v` a `m_i` proměnné členů. Ale při volání `GetType` na tuto proměnnou vrátí identické typ, který má `Person` instance `p2`. Takeaway je, že i když `VectorProxy` a `ArrowProxy` se může objevit **QuickWatch**, ladicího programu některých chyb kompilátoru, nebo z jiných míst, obvykle není nutné explicitně kód pro ně.  
  
 ![VectorProxy v rozsahu & č. 45; na základě smyčka for](../cppcx/media/vectorproxy-1.png "VectorProxy_1")  
  
 Jeden scénář, ve které je nutné kódu kolem objekt proxy serveru je, když je třeba provést `dynamic_cast` u elementů – například když hledáte XAML objektů, určitého typu v `UIElement` prvek kolekce. V takovém případě musíte nejprve přetypování elementu, který chcete [Platform::Object](../cppcx/platform-object-class.md)^ a poté proveďte dynamické přetypování:  
  
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
  
## <a name="map-usage"></a>Použití map  
 Tento příklad ukazuje, jak vložit položek a vyhledejte je [Platform::Collections::Map](../cppcx/platform-collections-map-class.md)a pak se vraťte `Map` jako jen pro čtení [Windows::Foundation::Collections::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) typu.  
  
 [!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]  
  
 Obecně platí, interní mapování funkce, dáváte přednost `std::map` typ z důvodů výkonu. Pokud máte předat kontejneru napříč ABI, vytvořit [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) z [std::map](../standard-library/map-class.md) a vrátíte se `Map` jako [Windows::Foundation –:: Collections::IMap](http://msdn.microsoft.com/library/windows/apps/br226042.aspx). Pokud pokus o použití `Map` zadejte veřejný návratovou hodnotu nebo parametr, Chyba kompilátoru C3986, bude vyvolána. Můžete je chyba vyřešit změnou `Map` k `IMap`. V některých případech – například, pokud nejsou Příprava velký počet hledání nebo vložení, a kolekce jsou předávání přes ABI často – může být levnější používat `Platform::Collections::Map` od začátku a vyhnout se náklady na převod `std::map`. V každém případě vyhnout vyhledávání a operace vložení na `IMap` protože se jedná minimálně původce všech tří typů. Převést na `IMap` pouze v bodě předáte napříč ABI kontejneru.  
  
## <a name="value-types-in-map"></a>Typy hodnot v mapě  
 Elementy v [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) seřazeni. Libovolný element, který má být uložen v `Map` musí podporovat menší – než porovnání s striktní weak řazení implicitně nebo pomocí vlastní [stl::less](../standard-library/less-struct.md) Komparátor, který zadáte. Skalární typy podporují porovnání implicitně. Pro neskalární hodnoty typy `Windows::Foundation::DateTime`, nebo pro vlastní porovnání – například `objA->UniqueID < objB->UniqueID`– je nutné zadat vlastní komparátoru.  
  
## <a name="collection-types"></a>Typy kolekcí  
 Kolekce rozdělit do čtyř skupin: upravitelnými verze jen pro čtení systému a pořadí kolekcí a asociativní kolekcí. Kromě toho, C + +/ CX vylepšuje kolekce tím, že poskytuje tři iterator třídy, které zjednodušují přístup k kolekcí. 
  
 Prvky upravitelnými kolekce lze změnit, ale prvků jen pro čtení kolekce, která se označuje jako *zobrazení*, mohli číst jenom. Elementy [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) nebo[Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) kolekce je přístupná pomocí iterovat nebo kolekce [Vector::GetAt](../cppcx/platform-collections-vector-class.md#getat) a indexu. Prvky asociativní kolekce můžete přistupovat pomocí kolekce [Map::Lookup](../cppcx/platform-collections-map-class.md#lookup) a klíč.  
  
 [Platform::Collections::Map – třída](../cppcx/platform-collections-map-class.md)  
 Upravitelnými, asociativní kolekce. Mapa prvky jsou páry klíč hodnota. Vyhledávání klíč pro načtení její přidružené hodnoty a iterace v rámci všechny páry klíč hodnota, jsou podporované.  
  
 `Map`a `MapView` jsou na základě šablony `<K, V, C = std::less<K>>`; proto Komparátor, který můžete přizpůsobit.  Kromě toho `Vector` a `VectorView` jsou na základě šablony `<T, E = std::equal_to<T>>` tak, aby si můžete přizpůsobit chování `IndexOf()`. To je důležité hlavně pro `Vector` a `VectorView` struktur hodnotu. Chcete-li například vytvořit vektor\<Windows::Foundation::DateTime >, je nutné zadat vlastní Komparátor, protože data a času není přetížení == – operátor.  
  
 [Platform::Collections::MapView – třída](../cppcx/platform-collections-mapview-class.md)  
 Jen pro čtení verzi `Map`.  
  
 [Platform::Collections::Vector – třída](../cppcx/platform-collections-vector-class.md)  
 Kolekce upravitelnými pořadí. `Vector<T>`podporuje konstanta čas náhodný přístup a amortizovaný čas konstanta [připojení](../cppcx/platform-collections-vector-class.md#append) operace...  
  
 [Platform::Collections::VectorView – třída](../cppcx/platform-collections-vectorview-class.md)  
 Jen pro čtení verzi `Vector`.  
  
 [Platform::Collections::InputIterator – třída](../cppcx/platform-collections-inputiterator-class.md)  
 Iterator STL, který splňuje požadavky vstupní iterovat STL.  
  
 [Platform::Collections::VectorIterator – třída](../cppcx/platform-collections-vectoriterator-class.md)  
 Iterator STL, který splňuje požadavky iterator STL měnitelný náhodný přístup.  
  
 [Platform::Collections::VectorViewIterator – třída](../cppcx/platform-collections-vectorviewiterator-class.md)  
 Iterátor STL, který splňuje požadavky STL `const` iterator náhodný přístup.  
  
### <a name="begin-and-end-functions"></a>Funkce begin() a end()  
 Ke zjednodušení použití STL zpracovat `Vector`, `VectorView`, `Map`, `MapView`a libovolný `Windows::Foundation::Collections` objekty, C + +/ CX podporuje přetížení [začít funkce](../cppcx/begin-function.md) a [end Funkce](../cppcx/end-function.md) třetí funkce.  
  
 Následující tabulka uvádí dostupné iterátory a funkce.  
  
|Iterátory|Funkce|  
|---------------|---------------|  
|[Platform::Collections::VectorIterator\<T >](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Interně ukládá [Windows::Foundation::Collections:: IVector\<T >](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) a int.)|[Začněte](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md)([Windows::Foundation::Collections:: IVector\<T >](http://msdn.microsoft.com/library/windows/apps/br206631.aspx))|  
|[Platform::Collections::VectorViewIterator\<T >](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Interně ukládá [IVectorView\<T >](http://msdn.microsoft.com/library/windows/apps/br226058.aspx)^ a int.)|[Začněte](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IVectorView\<T >](http://msdn.microsoft.com/library/windows/apps/br226058.aspx)^)|  
|[Platform::Collections::InputIterator\<T >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [IIterator\<T >](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ a T.)|[Začněte](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IIterable\<T >](http://msdn.microsoft.com/library/windows/apps/br226024.aspx))|  
|[Platform::Collections::InputIterator < IKeyValuePair\<tisíc, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [IIterator\<T >](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ a T.)|[Začněte](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IMap\<tisíc, V >](http://msdn.microsoft.com/library/windows/apps/br226042.aspx).|  
|[Platform::Collections::InputIterator < IKeyValuePair\<tisíc, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Interně ukládá [IIterator\<T >](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ a T.)|[Začněte](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([Windows::Foundation::Collections::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx))|  
  
### <a name="collection-change-events"></a>Kolekce událostí změny  
 `Vector`a `Map` podporu vazby dat v kolekcích XAML implementací události, které nastaly při změně objekt kolekce nebo obnovení, nebo když vložíte libovolného elementu kolekce, odebrat nebo změnit. Můžete napsat vlastní typy tuto podporu vazby dat, i když nemůže Zdědit z `Map` nebo `Vector` vzhledem k tomu, že tyto typy jsou zapečetěné.  
  
 [Windows::Foundation::Collections::VectorChangedEventHandler](http://msdn.microsoft.com/library/windows/apps/br206656.aspx) a [Windows::Foundation::Collections::MapChangedEventHandler](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) delegáti zadejte podpisy pro obslužné rutiny události pro kolekce událostí změny. [Windows::Foundation::Collections::CollectionChange](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx) veřejný výčet tříd a `Platform::Collection::Details::MapChangedEventArgs` a `Platform::Collections::Details::VectorChangedEventArgs` ref třídy ukládání argumenty událostí k určení, co způsobilo události. *`EventArgs` Typy jsou definované v `Details` obor názvů vzhledem k tomu, že nemáte k vytvoření nebo je můžou využívat explicitně při použití `Map` nebo `Vector`.  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Vestavěné typy](http://msdn.microsoft.com/en-us/acc196fd-09da-4882-b554-6c94685ec75f)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)