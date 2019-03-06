---
title: Delegáti (C + +/ CX)
ms.date: 01/22/2017
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
ms.openlocfilehash: cb23c5d1ae35a56a827bc2436dbdd81b53dd1224
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415276"
---
# <a name="delegates-ccx"></a>Delegáti (C + +/ CX)

`delegate` – Klíčové slovo se používá k deklaraci typu odkaz, který je ekvivalentní prostředí Windows Runtime a objektu funkce ve standardním jazyce C++. Deklarace delegáta, která je podobná signatuře funkce; Určuje návratový typ a typy parametrů musí mít jeho zabalené funkce. Toto je uživatelský delegát deklarace:

```cpp
public delegate void PrimeFoundHandler(int result);
```

Delegáty se běžně používají ve spojení s událostmi. Událost má typ delegáta, téměř stejným způsobem, že třída může mít typ rozhraní. Delegát reprezentuje kontrakt, který mnohem splnění obslužných rutin událostí. Tady je člen třídy události jehož typ je dříve definovaného delegáta:

```cpp
event PrimeFoundHandler^ primeFoundEvent;
```

Při deklarování delegáty, kteří budou přístupné pro klienty napříč binárním rozhraním aplikace Windows Runtime, použijte [Windows::Foundation:: typedeventhandler\<TSender, TResult >](/uwp/api/windows.foundation.typedeventhandler). Tento delegát má předdefinovaná proxy a zástupných procedur binární soubory, které umožňují využívat klientů Javascript.

## <a name="consuming-delegates"></a>Použití delegátů

Když vytvoříte aplikaci pro univerzální platformu Windows, můžete často pracují s delegátem jako typu události, která zveřejňuje třídy Windows Runtime. Chcete-li přihlásit odběr události, vytvořit instanci typ delegáta tak, že určíte funkci – nebo lambda –, který odpovídá signatuře delegátu. Potom použijte `+=` operátor pro předání objektu delegáta pro člen události ve třídě. To se označuje jako přihlášení k odběru události. Při instanci třídy"" události je volána funkce, spolu s všechny rutiny, které byly přidány do objektu nebo jiné objekty.

> [!TIP]
> Visual Studio spoustu práce udělá za vás při vytváření obslužné rutiny události. Například pokud chcete zadat obslužné rutiny události v kódu XAML, zobrazí se popisku tlačítka. Pokud se rozhodnete popis tlačítka, Visual Studio automaticky vytvoří metodu obslužné rutiny události a přidruží ji k události publikování třídy.

Následující příklad zobrazuje základní vzor. `Windows::Foundation::TypedEventHandler` je typ delegátu. Funkce obslužné rutiny se vytvoří s použitím pojmenované funkce.

V app.h:

[!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]

V app.cpp:

[!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]

> [!WARNING]
> Obecně pro obslužnou rutinu události, je vhodnější použít pojmenované funkce namísto výrazu lambda, pokud trvat velmi pečlivě, aby se zabránilo cyklické odkazy. Pojmenované funkce zachycuje ukazatel "Tento" podle nestálý odkaz, ale výraz lambda zachytí silné odkazem a vytváří cyklický odkaz. Další informace najdete v tématu [slabé odkazy a cykly zásadní](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

Podle úmluvy názvy delegáta obslužné rutiny události, které jsou definovány pomocí prostředí Windows Runtime mít formát _služba ._protokol * EventHandler – například RoutedEventHandler SizeChangedEventHandler či SuspendingEventHandler. Podle konvence také delegátů obslužných rutin události mají dva parametry a vracet typ void. Delegát, který nemá parametry typu, je první parametr typu [Platform::Object ^](../cppcx/platform-object-class.md); obsahuje odkaz na odesílatele, což je objekt, která vyvolala událost. Je třeba přetypovat zpět na původní typ, než použití argumentu v metodě obslužné rutiny události. V obslužné rutiny delegáta události, které má parametry typu, určuje první parametr typu typ odesílatele a druhý parametr je popisovač na referenční třídu, která uchovává informace o události. Podle konvence, tato třída má název \*EventArgs. Například delegát RoutedEventHandler má druhý operátor typu RoutedEventArgs ^, a druhý operátor typu DragEventArgs DragEventHander ^.

Podle konvence jsou delegáty, kteří se zabalit kód, který se spustí po dokončení asynchronní operace s názvem * CompletedHandler. Tyto delegáty jsou definovány jako vlastnosti třídy, nikoli jako události. Proto nepoužívejte `+=` operátor přihlásit se k odběru; právě přiřadit objektu delegáta k vlastnosti.

> [!TIP]
> Technologie IntelliSense jazyka C++ nezobrazí úplný delegáta; Proto se nijak nepomáhá můžete zjistit, konkrétní typ parametr EventArgs. Najít typ, můžete přejít na **prohlížeče objektů** a podívejte se na `Invoke` metodu pro delegáta.

## <a name="creating-custom-delegates"></a>Vytváří se vlastní delegáty

Můžete definovat vlastní delegáty, k definování obslužných rutin událostí nebo k povolení příjemcům a zajistěte tak předání vlastní funkce pro vaše komponenta Windows Runtime. Stejně jako jakýkoli jiný typ Windows Runtime nelze použít deklaraci veřejný delegát jako obecný.

### <a name="declaration"></a>Deklarace

Deklarace delegáta vypadá podobně jako deklarace funkce s tím rozdílem, že je typ delegátu. Obvykle je deklarovat delegáta v oboru názvů, i když lze také vnořit deklaraci delegáta v deklaraci třídy. Následující delegát zapouzdřuje všechny funkce, které přijímá `ContactInfo^` jako vstup a vrátí `Platform::String^`.

[!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]

Po deklaraci typu delegáta, je možné deklarovat členy třídy tohoto typu nebo metody, které přebírají objekty tohoto typu jako parametry. Metoda nebo funkce může také vracet typ delegáta. V následujícím příkladu `ToCustomString` metoda přijímá jako vstupní parametr delegátu. Tato metoda umožňuje klientským kódem, aby poskytují vlastní funkce, která vytvoří řetězec z některé nebo všechny veřejné vlastnosti `ContactInfo` objektu.

[!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]

> [!NOTE]
> Můžete použít "^" stejně jako jakékoli Windows runtime na typ symbolu při odkazu na typ delegáta.

Vždy deklaraci události má typ delegáta. Tento příklad ukazuje typické delegáta podpisu typ v modulu Windows Runtime:

[!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]

`Click` Událost v `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` třída je typu `RoutedEventHandler`. Další informace najdete v tématu [události](../cppcx/events-c-cx.md).

Klientský kód nejprve vytvoří instanci delegáta pomocí `ref new` a výraz lambda, který je kompatibilní s podpisem delegáta a definuje vlastní chování.

[!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]

Potom volá členskou funkci a předává delegáta. Předpokládejme, že `ci` je `ContactInfo^` instance a `textBlock` je XAML `TextBlock^`.

[!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]

V následujícím příkladu, klientská aplikace předává do veřejné metody v součásti prostředí Windows Runtime, který spouští delegáta pro každou položku v vlastního delegáta `Vector`:

[!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]

[!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]

### <a name="construction"></a>Konstrukce

Můžete vytvořit delegáta z kteréhokoli z těchto objektů:

- lambda

- statické funkce

- pointer-to-member

- std::Function

Následující příklad ukazuje, jak vytvořit delegáta z každého z těchto objektů. Využité delegáta přesně stejným způsobem bez ohledu na typ objektu, který slouží k jeho vytvoření.

[!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]

> [!WARNING]
> Pokud výraz lambda, který zachycuje ukazatel "Tento" použijete, nezapomeňte použít `-=` operátor explicitně zrušit registraci z událostí před ukončením výrazu lambda. Další informace najdete v tématu [události](../cppcx/events-c-cx.md).

### <a name="generic-delegates"></a>Obecní delegáti

Obecní delegáti v jazyce C + +/ CX mají omezení, podobně jako deklarace obecných tříd. Nemohou být deklarovány jako veřejná. Můžete deklarovat soukromé nebo interní obecného delegáta a používat ji v C++, ale rozhraní .NET nebo klientů JavaScript nelze ho zpracovat vzhledem k tomu, že se emitovat do metadat .winmd. V tomto příkladu deklaruje obecného delegáta, který může používat pouze C++:

[!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]

Následující příklad deklaruje specializovanou instanci třídy delegáta uvnitř definice třídy:

[!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]

## <a name="delegates-and-threads"></a>Delegáty a vlákna

Delegát, stejně jako objekt funkce, obsahuje kód, který se spustí někdy v budoucnu. Pokud kód, který vytváří a předává delegáta a funkci, která přijme a zpracuje delegáta, běží ve stejném vlákně, co jsou poměrně jednoduché. Pokud toto vlákno je vlákno uživatelského rozhraní, delegáta můžete přímo pracovat s objekty uživatelského rozhraní, jako je například ovládací prvky XAML.

Pokud se klientská aplikace načte komponenty prostředí Windows Runtime, která běží na jednovláknový objekt apartment a poskytuje delegáta pro tuto součást, pak ve výchozím nastavení je delegát vyvolán přímo u vlákna STA. Většina komponent prostředí Windows Runtime můžete spustit v režimu STA nebo MTA.

Pokud kód, který spouští delegáta je spuštěna v jiném vlákně – například v rámci objektu concurrency::task – pak zodpovědná za synchronizaci přístup ke sdíleným datům. Například Pokud delegát obsahuje odkaz na vektoru a ovládací prvek XAML obsahuje odkaz na tento stejný vektoru, je nutné provést kroky předcházet zablokování nebo časování, které mohou nastat při delegáta i ovládací prvek XAML pokus o přístup k vektoru na sam čas e. Můžete také pečlivě, že delegát nebude se pokoušet zachycení podle reference lokálních proměnných, které může být předtím, než je delegát vyvolán dostanou mimo rozsah.

Pokud chcete vytvořený delegát být ve stejném vlákně, který byl vytvořen na zpětné volání – například pokud předáte do komponenty, která běží v prostředí MTA komplexu – a má být vyvolána ve stejném vlákně jako Tvůrce , pak pomocí přetížení konstruktoru delegáta, který přebírá sekundy `CallbackContext` parametru. Toto přetížení použijte pouze na delegáty, kteří mají registrované proxy/zástupné procedury; Ne všechny delegáty, které jsou definovány v Windows.winmd jsou registrované.

Pokud jste se seznámili s obslužné rutiny události v rozhraní .NET, víte, že doporučeným postupem je vytvořit místní kopii předtím, než se aktivuje událost. Tím se vyhnete časování, ve kterých může být obslužné rutiny události odebrán těsně před plánovaným začátkem události je vyvolána. Není to nutné k tomu v jazyce C + +/ CX vzhledem k tomu, že při přidávání nebo odebírání obslužných rutin událostí se vytvoří nový seznam obslužné rutiny. Protože objekt jazyka C++ zvýší počet odkazů na seznam obslužných rutin před vyvoláním události, není zaručeno, že všechny obslužné rutiny bude platit. To ale také znamená, že pokud odeberete obslužné rutiny události v konzumním vlákně, tato obslužná rutina může stále získat vyvolána, pokud publikování objektu stále pracuje na jeho kopii v seznamu je nyní zastaralá. Publikování objekt nebude aktualizovaný seznam získáte až do příštího vyvolá událost.

## <a name="see-also"></a>Viz také

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)