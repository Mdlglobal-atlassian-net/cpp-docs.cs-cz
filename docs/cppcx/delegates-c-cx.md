---
title: Delegáti (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
ms.openlocfilehash: e570acafb8cce8b9496b79a062c3035015ba9811
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032470"
---
# <a name="delegates-ccx"></a>Delegáti (C++/CX)

Klíčové `delegate` slovo se používá k deklarování typu odkazu, který je ekvivalentem prostředí Windows Runtime objektu funkce ve standardním jazyce C++. Deklarace delegáta podobná podpisu funkce; určuje návratový typ a typy parametrů, které musí mít jeho zabalená funkce. Toto je uživatelem definované prohlášení delegáta:

```cpp
public delegate void PrimeFoundHandler(int result);
```

Delegáti se nejčastěji používají ve spojení s událostmi. Událost má typ delegáta, v podstatě stejným způsobem, že třída může mít typ rozhraní. Delegát představuje smlouvu, kterou obslužné rutiny událostí plní. Zde je člen třídy události, jehož typ je dříve definovaný delegát:

```cpp
event PrimeFoundHandler^ primeFoundEvent;
```

Při deklarování delegátů, kteří budou vystaveni klientům v binárním rozhraní aplikace Prostředí Windows Runtime, použijte [windows::Foundation::TypedEventHandler\<TSender, TResult>](/uwp/api/windows.foundation.typedeventhandler-2). Tento delegát má předdefinované binární soubory proxy a se zakázaným inzerováním, které umožňují jeho spotřebování klienty Javascriptu.

## <a name="consuming-delegates"></a>Náročné delegáty

Při vytváření aplikace univerzální platformy Windows často pracujete s delegátem jako typ události, kterou zpřístupňuje třída Prostředí Windows Runtime. Chcete-li se přihlásit k odběru události, vytvořte instanci jejího typu delegáta zadáním funkce nebo lambda, která odpovídá podpisu delegáta. Potom pomocí `+=` operátoru předaj objekt delegáta členu události ve třídě. Tento název se označuje jako přihlášení k odběru události. Když instance třídy "spustí" událost, je volána vaše funkce spolu s dalšími obslužnými rutinami, které byly přidány objektem nebo jinými objekty.

> [!TIP]
> Visual Studio dělá hodně práce za vás při vytváření obslužné rutiny události. Pokud například zadáte obslužnou rutinu události ve značkách XAML, zobrazí se tip nástroje. Pokud zvolíte tip nástroje, Visual Studio automaticky vytvoří metodu obslužné rutiny události a přidruží ji k události ve třídě publikování.

Následující příklad ukazuje základní vzor. `Windows::Foundation::TypedEventHandler`je typ delegáta. Funkce obslužné rutiny je vytvořena pomocí pojmenované funkce.

V aplikaci app.h:

[!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]

V aplikaci app.cpp:

[!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]

> [!WARNING]
> Obecně platí pro obslužnou rutinu události je lepší použít pojmenovanou funkci namísto lambda, pokud nechcete věnovat velkou pozornost, abyste se vyhnuli cyklické odkazy. Pojmenovaná funkce zachytí ukazatel "this" slabým odkazem, ale lambda ji zachytí silným odkazem a vytvoří cyklický odkaz. Další informace naleznete v tématu [Slabé odkazy a cykly přerušení](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

Podle konvence mají názvy delegátů obslužné rutiny událostí, které jsou definovány prostředím Windows Runtime, formulář *EventHandler – například RoutedEventHandler, SizeChangedEventHandler nebo SuspendingEventHandler. Také podle konvence delegáti obslužné rutiny události mají dva parametry a vrátit void. V delegátovi, který nemá parametry typu, je první parametr typu [Platform::Object^](../cppcx/platform-object-class.md); obsahuje odkaz na odesílatele, což je objekt, který vypálil událost. Před použitím argumentu v metodě obslužné rutiny události je třeba přetypovat zpět na původní typ. V delegáta obslužné rutiny události, který má parametry typu, určuje parametr prvního typu typ odesílatele a druhý parametr je popisovač třídy ref, která obsahuje informace o události. Podle konvence, tato \*třída se nazývá EventArgs. Například delegát RoutedEventHandler má druhý parametr typu RoutedEventArgs^, a DragEventHander má druhý parametr typu DragEventArgs^.

Podle konvence delegáti, které obtékat kód, který se spustí po dokončení asynchronní operace s názvem *CompletedHandler. Tyto delegáti jsou definovány jako vlastnosti třídy, nikoli jako události. Proto nepoužíváte `+=` operátor k jejich odběru; pouze přiřadit objekt delegáta k vlastnosti.

> [!TIP]
> C++ IntelliSense nezobrazuje úplný podpis delegáta; proto nepomůže určit konkrétní typ EventArgs parametr. Chcete-li najít typ, můžete přejít do `Invoke` prohlížeče **objektů** a podívat se na metodu delegáta.

## <a name="creating-custom-delegates"></a>Vytváření vlastních delegátů

Můžete definovat vlastní delegáty, definovat obslužné rutiny událostí nebo povolit spotřebitelům předat vlastní funkce součásti prostředí Windows Runtime. Stejně jako jakýkoli jiný typ prostředí Windows Runtime nelze veřejný delegát deklarovat jako obecný.

### <a name="declaration"></a>Deklarace

Deklarace delegáta se podobá deklaraci funkce s tím rozdílem, že delegát je typ. Obvykle deklarujete delegáta v oboru oboru názvů, i když můžete také vnořit deklaraci delegáta do deklarace třídy. Následující delegát zapouzdřuje všechny `ContactInfo^` funkce, která `Platform::String^`trvá jako vstup a vrátí .

[!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]

Po deklarování typu delegáta můžete deklarovat členy třídy tohoto typu nebo metody, které berou objekty tohoto typu jako parametry. Metoda nebo funkce může také vrátit typ delegáta. V následujícím příkladu `ToCustomString` metoda přebírá delegáta jako vstupní parametr. Metoda umožňuje klientský kód poskytnout vlastní funkci, která vytvoří řetězec z některých nebo všech veřejných vlastností objektu. `ContactInfo`

[!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]

> [!NOTE]
> Symbol ^se používá při odkazování na typ delegáta, stejně jako u libovolného typu odkazu prostředí Windows Runtime.

Deklarace události má vždy typ delegáta. Tento příklad ukazuje typický podpis typu delegáta v prostředí Windows Runtime:

[!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]

Událost `Click` ve `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` třídě je `RoutedEventHandler`typu . Další informace naleznete v tématu [Události](../cppcx/events-c-cx.md).

Klientský kód nejprve vytvoří `ref new` instanci delegáta pomocí a poskytnutím lambda, který je kompatibilní s podpisem delegáta a definuje vlastní chování.

[!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]

Potom zavolá členská funkce a předá delegáta. `ci` Předpokládejme, `ContactInfo^` že `textBlock` je instance a `TextBlock^`je XAML .

[!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]

V dalším příkladu klientská aplikace předá vlastní delegáta veřejné metodě v součásti prostředí `Vector`Windows Runtime, která provede delegáta proti každé položce v :

[!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]

[!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]

### <a name="construction"></a>Stavebnictví

Delegáta můžete sestavit z některého z těchto objektů:

- lambda

- statická funkce

- ukazatel na člen

- std::funkce

Následující příklad ukazuje, jak vytvořit delegáta z každého z těchto objektů. Delegáta spotřebováváte přesně stejným způsobem bez ohledu na typ objektu, který se používá k jeho vytvoření.

[!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]

> [!WARNING]
> Pokud používáte lambda, který zachycuje ukazatel "this", `-=` nezapomeňte použít operátor explicitně zrušit registraci z události před ukončením lambda. Další informace naleznete v tématu [Události](../cppcx/events-c-cx.md).

### <a name="generic-delegates"></a>Obecné delegáty

Obecné delegáty v jazyce C++/CX mají omezení podobná deklaracím obecných tříd. Nelze je prohlásit za veřejné. Můžete deklarovat soukromé nebo interní obecný delegát a využívat jej z Jazyka C++, ale klienti .NET nebo JavaScript jej nemohou využívat, protože nejsou vyzařovány do metadat .winmd. Tento příklad deklaruje obecný delegát, který může být spotřebován pouze c++:

[!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]

Další příklad deklaruje specializovanou instanci delegáta uvnitř definice třídy:

[!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]

## <a name="delegates-and-threads"></a>Delegáti a vlákna

Delegát, stejně jako objekt funkce, obsahuje kód, který bude spuštěn někdy v budoucnu. Pokud kód, který vytvoří a předá delegáta a funkce, která přijímá a provádí delegáta, jsou spuštěny ve stejném vlákně, pak věci jsou poměrně jednoduché. Pokud toto vlákno je vlákno uživatelského rozhraní, pak delegát může přímo manipulovat s objekty uživatelského rozhraní, jako jsou ovládací prvky XAML.

Pokud klientská aplikace načte součást prostředí Windows Runtime, která běží v zřetězené masce a poskytuje delegáta této součásti, pak je ve výchozím nastavení delegát vyvolán přímo ve vlákně STA. Většina součástí prostředí Windows Runtime lze spustit v STA nebo MTA.

Pokud kód, který provede delegáta běží v jiném vlákně – například v rámci souběžnosti::task objektu – pak jste zodpovědní za synchronizaci přístupu ke sdíleným datům. Například pokud váš delegát obsahuje odkaz na Vector a ovládací prvek XAML má odkaz na stejný vector, je nutné provést kroky, aby se zabránilo zablokování nebo sporné podmínky, které mohou nastat, když delegát a XAML ovládací prvek pokusí o přístup k Vector ve stejnou dobu. Musíte také dbát na to, aby se delegát nepokusil zachytit odkazem na místní proměnné, které mohou přejít mimo rozsah před vyvoláním delegáta.

Pokud chcete, aby byl vytvořený delegát volán zpět do stejného vlákna, ve kterém byl vytvořen – například pokud jej předáte součásti, která běží v bytě MTA – `CallbackContext` a chcete, aby byl vyvolán ve stejném vlákně jako tvůrce, použijte přetížení konstruktoru delegáta, které přebírá druhý parametr. Toto přetížení používejte pouze u delegátů, kteří mají registrovaný proxy/stub. nejsou registrováni všichni delegáti, kteří jsou definováni v souboru Windows.winmd.

Pokud jste obeznámeni s obslužnými rutinami událostí v rozhraní .NET, víte, že doporučeným postupem je vytvořit místní kopii události před jeho spálením. Tím se zabrání časovky, ve kterém obslužná rutina události může být odebrána těsně před vyvolání události. Není nutné to provést v jazyce C++/CX, protože při přidání nebo odebrání obslužné rutiny je vytvořen nový seznam obslužné rutiny. Vzhledem k tomu, že objekt jazyka C++ zvýší počet odkazů v seznamu obslužné rutiny před vyvoláním události, je zaručeno, že všechny obslužné rutiny budou platné. To však také znamená, že pokud odeberete obslužnou rutinu události ve náročném vlákně, může být tato obslužná rutina stále vyvolána, pokud objekt publikování stále pracuje na své kopii seznamu, který je nyní zastaralý. Objekt publikování nezíská aktualizovaný seznam až při příštím spuštění události.

## <a name="see-also"></a>Viz také

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
