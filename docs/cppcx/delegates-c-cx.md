---
title: "Delegáti (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aca49513c52c5eff9c10461281bb4235fa39349f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="delegates-ccx"></a>Delegáti (C + +/ CX)
`delegate` – Klíčové slovo se používá k deklaraci typu odkaz, který je ekvivalentní prostředí Windows Runtime objektu funkce v standardní C++. Deklarace delegáta podobné funkce podpisu; Určí návratový typ a typy parametrů, které musí mít jeho zabalené funkce. Toto je uživatelem definované delegáta deklarace:  
  
```cpp  
     public delegate void PrimeFoundHandler(int result);  
```  
  
 Delegáti se běžně používají ve spojení s událostmi. Událost má typem delegáta prakticky stejným způsobem, že třída může mít typ rozhraní. Delegát představuje kontrakt, který obslužné rutiny událostí mnohem splnit. Tady je jejichž typ je delegáta předtím definovaný člen třídy události:  
  
```cpp  
event PrimeFoundHandler^ primeFoundEvent;  
```  
  
 Pokud deklarace delegáti, které se zveřejní klientům v prostředí Windows Runtime binární rozhraní aplikace, použijte [Windows::Foundation::TypedEventHandler\<TSender, TResult >](http://msdn.microsoft.com/library/windows/apps/br225997.aspx). Tento delegát má předdefinovaná nastavení proxy serveru a se zakázaným inzerováním binární soubory, které umožní, aby se spotřebovávají klientů Javascript.  
  
## <a name="consuming-delegates"></a>Použití delegátů  
 Když vytvoříte aplikaci pro univerzální platformu Windows, často pracujete s delegáta jako typ událost, která zveřejňuje třídu prostředí Windows Runtime. K odběru události, vytvořte instanci daného typu delegáta zadáním funkce – nebo lambda, která odpovídá delegáta. Potom pomocí `+=` operátor a předat objekt delegáta člena události na třídu. To se označuje jako k události odběru. Pokud instance třídy "aktivuje" události, je volána funkce, společně s všech ostatních obslužných rutin, které byly přidány do objektu nebo jiné objekty.  
  
> [!TIP]
>  Visual Studio provede hodně práce při vytvoření obslužné rutiny události. Například pokud zadáte obslužné rutiny událostí v kódu XAML, zobrazí se popis tlačítka. Pokud si zvolíte popis tlačítka, Visual Studio automaticky vytvoří obslužná rutina události a přidruží ji k události k třídě publikování.  
  
 Následující příklad ukazuje základní vzor. `Windows::Foundation::TypedEventHandler` je typ delegáta. Obslužné rutiny je vytvořená pomocí pojmenovaného funkce.  
  
 V app.h:  
  
 [!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]  
  
 V app.cpp:  
  
 [!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]  
  
> [!WARNING]
>  Obecně platí obslužné rutiny události, je lepší pro používání s názvem funkce místo lambda, pokud dávejte pozor, aby se zabránilo. cyklické odkazy. Pojmenované funkce zaznamená ukazatel "this" slabé odkazem, ale lambda zaznamená silné odkazem a vytvoří cyklický odkaz. Další informace najdete v tématu [slabé odkazy a ukončování cykly](../cppcx/weak-references-and-breaking-cycles-c-cx.md).  
  
 Podle konvence názvy delegáta obslužné rutiny události, které jsou definovány pomocí prostředí Windows Runtime mít formát * obslužná rutina události – například RoutedEventHandler, SizeChangedEventHandler nebo SuspendingEventHandler. Podle konvence také delegátů obslužných rutin událostí mít dva parametry a vracet typ void. Delegát, který nemá parametry typu, je první parametr typu [Platform::Object ^](../cppcx/platform-object-class.md); že obsahuje odkaz na odesílatele, který je objekt, který je aktivována událost. Je nutné převést zpět na původní typ dříve, než použijete argument v obslužná rutina události. V delegáta obslužná rutina události, který má parametry typu, určuje první parametr typu typ odesílatele a druhý parametr je popisovač pro ref třídu, která obsahuje informace o události. Podle konvence je s názvem třídy \*EventArgs. Například delegáta RoutedEventHandler má druhý parametr typu RoutedEventArgs ^, a DragEventHander má druhý parametr typu DragEventArgs ^.  
  
 Podle konvence, jsou pojmenované delegáti, které balí kód, který se spustí po dokončení asynchronní operace * CompletedHandler. Tyto Delegáti jsou definovány jako vlastnosti třídy, ne jako události. Proto, že nepoužíváte `+=` operátor a přihlásit se k odběru; je právě přiřadit objekt delegáta pro vlastnost.  
  
> [!TIP]
>  C++ IntelliSense nezobrazí úplné delegáta; proto jej není vám pomohou určit konkrétní typ parametru EventArgs. Se najít typ, můžete přejít na **Prohlížeč objektů** a podívejte se na `Invoke` metodu delegáta.  
  
## <a name="creating-custom-delegates"></a>Vytváření vlastních delegáti  
 Můžete definovat vlastní delegáty k definování obslužné rutiny událostí nebo k povolení příjemcům předat příslušné součásti prostředí Windows Runtime v vlastní funkce. Jako jiný typ prostředí Windows Runtime veřejný delegát nelze deklarovat jako obecný.  
  
### <a name="declaration"></a>Deklarace  
 Kromě toho, že delegát je typu se podobá deklaraci delegáta deklaraci funkce. Obvykle je deklarovat delegáta v oboru názvů, i když lze také vnořit deklaraci delegáta v deklaraci třídy. Následující delegát zapouzdřuje všechny funkce, která přebírá `ContactInfo^` jako vstup a vrátí `Platform::String^`.  
  
 [!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]  
  
 Jakmile je deklarovat typem delegáta, můžou deklarovat členy třídy tohoto typu nebo metod, které berou objekty daného typu jako parametry. Metody nebo funkce mohou vracet typem delegáta. V následujícím příkladu `ToCustomString` metoda přebírá delegáta jako vstupní parametr. Metoda umožňuje kód klienta zajistit vlastní funkci, která vytvoří řetězec z některé nebo všechny veřejné vlastnosti `ContactInfo` objektu.  
  
 [!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]  
  
> [!NOTE]
>  Můžete použít "^" symbolů při odkazu na typ delegáta, stejně jako s žádné prostředí Windows Runtime odkazujete typu.  
  
 Vždy deklaraci události má typem delegáta. Tento příklad ukazuje typické delegáta typu podpis v prostředí Windows Runtime:  
  
 [!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]  
  
 `Click` Událost v `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` třída je typu `RoutedEventHandler`. Další informace najdete v tématu [události](../cppcx/events-c-cx.md).  
  
 Kód klienta nejprve vytvoří instanci delegáta pomocí `ref new` a poskytování lambda, který je kompatibilní s podpisem delegáta a definuje vlastní chování.  
  
 [!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]  
  
 Potom volá funkci člen a předá delegát. Předpokládáme, že `ci` je `ContactInfo^` instance a `textBlock` je XAML `TextBlock^`.  
  
 [!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]  
  
 V následujícím příkladu, klient aplikace předává vlastní delegáta veřejná metoda v prostředí Windows Runtime součásti, které provádí delegáta pro každou položku v `Vector`:  
  
 [!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]  
  
 [!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]  
  
### <a name="construction"></a>Konstrukce  
 Můžete vytvořit delegáta z některého z těchto objektů:  
  
-   lambda  
  
-   statické funkce  
  
-   ukazatele na člena  
  
-   std::Function  
  
 Následující příklad ukazuje, jak vytvořit delegáta z každé z těchto objektů. Delegát spotřebujete přesně stejně bez ohledu na typ objektu, který se používá pro konstrukci ho.  
  
 [!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]  
  
> [!WARNING]
>  Pokud používáte lambda, který zachycuje ukazatel "this", je nutné používat `-=` operátor explicitně zrušte registraci z události před ukončete argument lambda. Další informace najdete v tématu [události](../cppcx/events-c-cx.md).  
  
### <a name="generic-delegates"></a>Obecní delegáti  
 Obecní delegáti v jazyce C + +/ CX mají omezení podobná deklarace obecné třídy. Jejich nelze deklarovat jako veřejné. Můžou deklarovat privátního nebo interní obecného delegovat a využívat z C++, ale .NET nebo klientů JavaScript nelze ho zpracovat vzhledem k tomu, že není vygenerované do .winmd metadata. Tento příklad deklaruje obecný delegát, který může zpracovat pouze C++:  
  
 [!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]  
  
 Další příklad deklaruje specializovanou instanci třídy delegáta uvnitř definice třídy:  
  
 [!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]  
  
## <a name="delegates-and-threads"></a>Delegáti a vlákna  
 S delegátem, stejně jako objekt funkce, obsahuje kód, který provede někdy v budoucnu. Pokud kód, který vytvoří a předá delegát a funkce, která přijme a zpracuje delegáta, běží ve stejném vlákně, jsou věci poměrně jednoduché. Pokud tento přístup z více vláken je vlákna uživatelského rozhraní, delegát můžete pracovat přímo s objekty uživatelského rozhraní, jako je například ovládací prvky jazyka XAML.  
  
 Pokud klientské aplikace načte komponenty prostředí Windows Runtime, která běží ve model typu apartment a poskytuje delegáta pro tuto součást, pak ve výchozím nastavení je vyvolán delegát přímo na STA vlákno. Většina komponent prostředí Windows Runtime můžete spustit v režimu STA nebo modelu MTA.  
  
 Pokud je kód, který provede delegát běží v jiném podprocesu – například v kontextu objektu concurrency::task – pak je zodpovědná za synchronizaci přístup ke sdíleným datům. Například pokud vaše delegáta obsahuje odkaz na vektor a XAML ovládací prvek obsahuje odkaz na tento stejný vektoru, musíte provést kroky předejdete zablokování nebo časování, které mohou nastat při delegáta i XAML řízení pokusí o přístup k vektoru v správce zabezpečení účtů čas e. Můžete také pečlivě, delegát není pokusí zaznamenat pomocí odkazu místní proměnné, které může před vyvoláním delegát dostala mimo rozsah.  
  
 Pokud chcete, aby vaše vytvořený delegáta být ve stejném vlákně, která byla vytvořena na zpětné volání – například, pokud je předat do komponenty, která běží v typu apartment MTA – a má být volána ve stejném vlákně, jako Tvůrce , pak použít přetížení konstruktor delegáta, které přijímá druhý `CallbackContext` parametr. Toto přetížení použijte pouze na delegáti, které mají registrované proxy/stub; Ne všechny delegáty, které jsou definovány v Windows.winmd jsou registrované.  
  
 Pokud jste obeznámeni s obslužné rutiny událostí v rozhraní .NET, víte, že doporučený postup je vytvořit místní kopii událost dříve, než ji můžete aktivovat. Tím je zabráněno časování, ve kterých může být obslužné rutiny události odebrán těsně před událost se vyvolá. Není to nutné k tomu v jazyce C + +/ CX vzhledem k tomu, že při přidávání nebo odebírání obslužné rutiny událostí je vytvořen nový seznam obslužné rutiny. Vzhledem k tomu, že objekt C++ zvýší počet odkazů na obslužné rutiny seznamu před vyvoláním událost, tak, aby zajistil platí všechny obslužné rutiny. Ale také to znamená, že pokud odeberete obslužné rutiny události pro spotřebitelské vlákno, této obslužné rutiny může stále získat volá se, pokud objekt publikování je pořád v provozu na jeho kopii v seznamu je nyní zastaralý. Objekt publikování nezískáte aktualizovaný seznam až po příštím vyvolá událost.  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)