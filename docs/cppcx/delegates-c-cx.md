---
title: DelegátiC++(/CX)
ms.date: 01/22/2017
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
ms.openlocfilehash: 3ab455044b98cdd8c7b13a650f729efc2132797e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740285"
---
# <a name="delegates-ccx"></a>DelegátiC++(/CX)

Klíčové slovo slouží k deklaraci typu odkazu, který je prostředí Windows Runtime ekvivalentem objektu funkce ve standardu C++ `delegate` Deklarace delegáta podobná podpisu funkce; Určuje návratový typ a typy parametrů, které musí mít zabalená funkce. Toto je uživatelsky definovaná deklarace delegáta:

```cpp
public delegate void PrimeFoundHandler(int result);
```

Delegáti se nejčastěji používají ve spojení s událostmi. Událost má typ delegáta, podobně jako třída může mít typ rozhraní. Delegát představuje kontrakt, který obslužné rutiny událostí hodně splní. Zde je člen třídy události, jehož typ je dříve definovaný delegát:

```cpp
event PrimeFoundHandler^ primeFoundEvent;
```

Při deklaraci delegátů, kteří budou vystaveni klientům v rámci binárního rozhraní prostředí Windows Runtime aplikace, použijte [Windows:: Foundation\<:: TypedEventHandler TSender, TResult >](/uwp/api/windows.foundation.typedeventhandler). Tento delegát má předdefinované binární soubory proxy a zástupné procedury, které umožňují, aby je mohli používat klienti JavaScriptu.

## <a name="consuming-delegates"></a>Používání delegátů

Při vytváření Univerzální platforma Windows aplikace často pracujete s delegátem jako typ události, kterou třída prostředí Windows Runtime zpřístupňuje. Chcete-li se přihlásit k odběru události, vytvořte instanci svého typu delegáta zadáním funkce (neboli výrazu lambda), která odpovídá podpisu delegáta. Pak použijte `+=` operátor k předání objektu delegáta členovi události třídy. Tento postup se označuje jako odběr události. Když je instance třídy "aktivována" událost, je volána funkce společně s dalšími obslužnými rutinami, které byly přidány do objektu nebo jiných objektů.

> [!TIP]
> Když vytvoříte obslužnou rutinu události, Visual Studio provede spoustu práce. Například pokud zadáte obslužnou rutinu události v kódu jazyka XAML, zobrazí se popis tlačítka. Pokud zvolíte popis tlačítka, Visual Studio automaticky vytvoří metodu obslužné rutiny události a přidruží ji k události třídy publikování.

Následující příklad ukazuje základní vzor. `Windows::Foundation::TypedEventHandler`je typ delegáta. Funkce obslužné rutiny je vytvořena pomocí pojmenované funkce.

V App. h:

[!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]

V App. cpp:

[!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]

> [!WARNING]
> Obecně platí, že pro obslužnou rutinu události je vhodnější použít pojmenovanou funkci namísto lambda, pokud nebudete mít skvělou péči vyhnout se cyklickým odkazům. Pojmenovaná funkce zachycuje "This" ukazatel na základě slabého odkazu, ale lambda ho zachytí silným odkazem a vytvoří cyklický odkaz. Další informace najdete v tématu [slabé odkazy a průlomové cykly](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

Podle konvencí názvy delegátů obslužných rutin události, které jsou definovány prostředí Windows Runtime, mají formu * EventHandler, například RoutedEventHandler, SizeChangedEventHandler nebo SuspendingEventHandler. I podle konvence mají Delegáti obslužné rutiny události dva parametry a vracet typ void. V delegátu, který nemá parametry typu, je první parametr typu [Platform:: Object ^](../cppcx/platform-object-class.md);. obsahuje odkaz na odesílatele, což je objekt, který událost vyvolal. Před použitím argumentu v metodě obslužné rutiny události je třeba přetypovat zpět na původní typ. V delegátu obslužné rutiny události, který má parametry typu, určuje první parametr typu odesílatele a druhý parametr popisovač referenční třídy, která obsahuje informace o události. Podle konvence je tato třída pojmenována \*EventArgs. Například delegát RoutedEventHandler má druhý parametr typu RoutedEventArgs ^ a DragEventHander má druhý parametr typu DragEventArgs ^.

Podle konvence delegáti, kteří zabalí kód, který se spustí po dokončení asynchronní operace, mají název * CompletedHandler. Tito Delegáti jsou definováni jako vlastnosti třídy, nikoli jako události. Proto `+=` operátor nepoužíváte k přihlášení k odběru. pouze k této vlastnosti přiřadíte objekt delegáta.

> [!TIP]
> C++IntelliSense nezobrazuje úplný podpis delegáta; Proto vám nepomůže určit konkrétní typ parametru EventArgs. Chcete-li najít typ, můžete přejít na **Prohlížeč objektů** a podívat se `Invoke` na metodu delegáta.

## <a name="creating-custom-delegates"></a>Vytváření vlastních delegátů

Můžete definovat vlastní delegáty, definovat obslužné rutiny událostí nebo umožnit příjemcům předat vlastní funkce prostředí Windows Runtime komponentě. Stejně jako u jakéhokoli jiného typu prostředí Windows Runtime nemůže být veřejný delegát deklarovaný jako obecný.

### <a name="declaration"></a>Deklarace

Deklarace delegáta se podobá deklaraci funkce s tím rozdílem, že delegát je typu. Obvykle deklarujete delegáta v oboru názvů, i když můžete také vnořit deklaraci delegáta v deklaraci třídy. Následující delegát zapouzdřuje jakoukoliv funkci, která přijímá `ContactInfo^` jako vstup, a `Platform::String^`vrátí.

[!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]

Po deklaraci typu delegáta můžete deklarovat členy třídy tohoto typu nebo metody, které přijímají objekty daného typu jako parametry. Metoda nebo funkce může také vracet typ delegáta. V následujícím příkladu `ToCustomString` metoda přebírá delegáta jako vstupní parametr. Metoda umožňuje klientskému kódu poskytnout vlastní funkci, která vytvoří řetězec z některých nebo všech veřejných vlastností `ContactInfo` objektu.

[!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]

> [!NOTE]
> Symbol "^" použijete při odkazování na typ delegáta, stejně jako u jakéhokoli typu odkazu prostředí Windows Runtime.

Deklarace události má vždycky typ delegáta. Tento příklad ukazuje typický podpis typu delegáta v prostředí Windows Runtime:

[!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]

Událost ve třídě je typu `RoutedEventHandler`. `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` `Click` Další informace najdete v tématu [události](../cppcx/events-c-cx.md).

Kód klienta nejprve vytvoří instanci delegátu pomocí `ref new` a poskytne lambda, která je kompatibilní s podpisem delegáta, a definuje vlastní chování.

[!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]

Pak zavolá členskou funkci a předá delegáta. Předpokládejme, `ci` že `ContactInfo^` je instancí a `textBlock` je XAML `TextBlock^`.

[!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]

V dalším příkladu klientská aplikace projde vlastní delegát na veřejnou metodu ve prostředí Windows Runtime komponentě, která spustí delegáta pro každou položku v `Vector`:

[!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]

[!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]

### <a name="construction"></a>Stavbě

Můžete vytvořit delegáta z libovolného z těchto objektů:

- lambda

- static – funkce

- ukazatel na člena

- std:: Function

Následující příklad ukazuje, jak vytvořit delegáta z každého z těchto objektů. Můžete využít delegáta přesně stejným způsobem bez ohledu na typ objektu, který je použit k jeho sestavení.

[!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]

> [!WARNING]
> Použijete-li lambda, který zachycuje ukazatel "This", nezapomeňte použít `-=` operátor k explicitnímu zrušení registrace z události před ukončením výrazu lambda. Další informace najdete v tématu [události](../cppcx/events-c-cx.md).

### <a name="generic-delegates"></a>Obecné delegáty

Obecní delegáti C++v/CX mají omezení podobná deklaracím obecných tříd. Nemohou být deklarovány jako veřejné. Můžete deklarovat privátní nebo interní delegáta a spotřebovat ho z C++, ale klienti .NET nebo JavaScript ho nemůžou spotřebovat, protože se neemitují do metadat. winmd. Tento příklad deklaruje obecný delegát, který může používat pouze C++:

[!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]

Následující příklad deklaruje specializované instance delegáta uvnitř definice třídy:

[!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]

## <a name="delegates-and-threads"></a>Delegáti a vlákna

Delegát, stejně jako objekt funkce, obsahuje kód, který bude v budoucnu spuštěn v určitou dobu. Pokud kód, který vytvoří a předává delegáta, a funkci, která přijímá a spustí delegáta, jsou spuštěny ve stejném vlákně, jsou objekty relativně jednoduché. Pokud je toto vlákno vláknem uživatelského rozhraní, delegát může přímo manipulovat s objekty uživatelského rozhraní, jako jsou například ovládací prvky XAML.

Pokud klientská aplikace načte prostředí Windows Runtime komponentu, která běží v vlákně s vláknem, a poskytuje delegáta této součásti, pak ve výchozím nastavení je delegát vyvolán přímo ve vlákně STA. Většina prostředí Windows Runtime komponent může běžet v prostředí STA nebo MTA.

Pokud kód, který spouští delegáta, je spuštěn v jiném vlákně, například v kontextu objektu concurrency:: Task, potom zodpovídáte za synchronizaci přístupu ke sdíleným datům. Například pokud váš delegát obsahuje odkaz na vektor a ovládací prvek XAML má odkaz na stejný vektor, je nutné provést kroky, abyste zabránili zablokování nebo konfliktům časování, ke kterým může dojít, když se delegát i ovládací prvek XAML pokusí o přístup ke vektoru v Sam. čas e. Je také nutné dbát na to, aby se delegát nepokoušel zachytit pomocí referenčních místních proměnných, které mohou být před vyvoláním delegáta přecházet mimo rozsah.

Pokud chcete, aby byl vytvořený delegát volán zpátky ve stejném vlákně, ve kterém byl vytvořen, například pokud ho předáte do komponenty, která běží v izolovaném prostoru MTA, a chcete ji vyvolat ve stejném vlákně jako tvůrce a pak použijte přetížení konstruktoru delegáta, které přijímá druhý `CallbackContext` parametr. Toto přetížení používejte jenom u delegátů, kteří mají registrovaný proxy/zástupnou proceduru; nejsou registrováni Všichni delegáti, kteří jsou definováni ve Windows. winmd.

Pokud jste obeznámeni s obslužnými rutinami událostí v rozhraní .NET, víte, že doporučeným postupem je vytvořit místní kopii události před tím, než se ji spustí. Tím se zabrání konfliktům časování, ve kterém může být obslužná rutina události odebrána těsně před vyvoláním události. Tuto akci není nutné provádět v C++/CX, protože když jsou obslužné rutiny událostí přidány nebo odebrány, vytvoří se nový seznam obslužných rutin. Vzhledem k C++ tomu, že objekt zvyšuje počet odkazů v seznamu obslužných rutin před vyvoláním události, je zaručeno, že všechny obslužné rutiny budou platné. Nicméně to znamená, že pokud odeberete obslužnou rutinu události ve fungujícím vlákně, tato obslužná rutina může být vyvolána i v případě, že objekt publikování stále pracuje na kopii seznamu, která je nyní zastaralá. Publikovaný objekt nebude získávat aktualizovaný seznam do okamžiku, kdy událost příště vyvolá.

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
