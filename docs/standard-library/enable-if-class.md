---
title: enable_if – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::enable_if
dev_langs:
- C++
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dfed0f7aab48cf933e69e7d1e6044cfda98c7dff
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="enableif-class"></a>enable_if – třída

Podmíněná vytváří instanci typu pro sfinae u výrazů řešení přetížení. Vnořené typedef `enable_if<Condition,Type>::type` existuje, a je synonymum pro `Type`– jenom v případě `Condition` je `true`.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool B, class T = void>
struct enable_if;
```

### <a name="parameters"></a>Parametry

`B` Hodnota, která určuje existenci výsledný typ.

`T` Typ k vytvoření instance Pokud `B` hodnotu true.

## <a name="remarks"></a>Poznámky

Pokud `B` má hodnotu true, `enable_if<B, T>` má vnořené typedef s názvem "typ", který se jedná o synonymum `T`.

Pokud `B` je nastavena hodnota false, `enable_if<B, T>` nemá vnořené typedef s názvem "typ".

Tato šablona alias je k dispozici:

```cpp
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```

V jazyce C++ selhání nahrazování parametrů šablony není chybu sám o sobě – tento proces se označuje jako *sfinae u výrazů* (selhání nahrazování není chybu). Obvykle `enable_if` slouží k odebrání kandidáty rozlišení přetížení – to znamená, že ho culls sadu přetížení – tak, aby jednu definici, může být odmítnutá považuje jiné. To odpovídá chování sfinae u výrazů. Další informace o sfinae u výrazů najdete v tématu [selhání nahrazování není chybu](http://go.microsoft.com/fwlink/p/?linkid=394798) na webu Wikipedia.

Zde jsou čtyři ukázkové scénáře:

- Scénář 1: Zabalení návratový typ funkce:

```cpp
    template <your_stuff>
typename enable_if<your_condition, your_return_type>::type
    yourfunction(args) {// ...
 }
// The alias template makes it more concise:
    template <your_stuff>
enable_if_t<your_condition, your_return_type>
yourfunction(args) {// ...
 }
```

- Scénář 2: Přidání funkce parametr, který má výchozí argument:

```cpp
    template <your_stuff>
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
 }
```

- Scénář 3: Přidání parametr šablony, která má výchozí argument:

```cpp
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>
rest_of_function_declaration_goes_here
```

- Scénář 4: Pokud má vaše funkce bez použití šablon argument, může obtékat typ:

```cpp
    template <typename T>
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>
s) {// ...
 }
```

Scénář 1 nefunguje s konstruktory a operátory převodu, protože nemají návratové typy.

Scénář 2 zanechává nepojmenovaný parametr. Řekněte `::type Dummy = BAR`, ale název `Dummy` je důležité, a pod názvem mohou aktivovat upozornění "neregistrované parametr". Budete muset zvolit `FOO` typ parametru funkce a `BAR` výchozí argument.  Řekněte `int` a `0`, ale pak uživatelé kódu může nechtěně předávat funkce celé navíc, který bude ignorován. Místo toho doporučujeme používat `void **` a buď `0` nebo `nullptr` protože převést na téměř nic `void **`:

```cpp
template <your_stuff>
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```

Scénář 2 funguje i pro běžné konstruktory.  Však nefunguje pro operátory převodu vzhledem k tomu, že nelze zpracovat další parametry.  Také nefunguje pro [variadická](../cpp/ellipses-and-variadic-templates.md) konstruktory protože přidání další parametry usnadňuje parametr funkce pack-odvodit kontextu a tím účinně chrání před účel `enable_if`.

Scénář 3 používá název `Dummy`, ale je volitelné. Právě " `typename = typename`" by pracovat, ale pokud si myslíte, která vypadá divné, můžete použít "fiktivní" název – stačí nepoužívejte ten, který lze také použít v definici funkce. Pokud nemáte dává typu k `enable_if`, nastaví se jako výchozí void, na kterém jsou perfektně rozumné řešení, protože není důležité co `Dummy` je. Tento postup funguje pro vše, včetně operátorů převodu a [variadická](../cpp/ellipses-and-variadic-templates.md) konstruktory.

Scénář 4 pracuje v konstruktory, které nemají návratové typy a tím řeší omezení zabalení scénář 1.  Scénář 4 je ale omezený na argumenty bez použití šablon funkce, které nejsou vždy k dispozici.  (Pomocí scénář 4 na argument podle šablony funkce zabraňuje odvození argumentu šablony z na něm pracovat.)

`enable_if` je výkonný, ale také nebezpečné, pokud je došlo ke zneužití.  Protože jeho účel je aby kandidáty zmizí před rozlišení přetížení je nebezpečného, může být velmi matoucí jeho účinky.  Tady jsou některá doporučení:

- Nepoužívejte `enable_if` můžete vybrat, jestli implementace při kompilaci. Nemáte někdy zápisu jeden `enable_if` pro `CONDITION` a druhý pro `!CONDITION`.  Místo toho použijte *značky odesílání* vzor – například algoritmu, který vybere implementace v závislosti na silné stránky iterátory se získá.

- Nepoužívejte `enable_if` vynutit požadavky.  Pokud chcete ověřit parametry šablony, a pokud se ověření nezdaří, způsobit chybu místo výběru jinou implementaci, použijte [static_assert](../cpp/static-assert.md).

- Použití `enable_if` Pokud máte sadu přetížení, který jinak dobrý code nejednoznačný.  Nejčastěji používá k tomu dochází v implicitní převod konstruktory.

## <a name="example"></a>Příklad

Tento příklad vysvětluje, jak funkce standardní knihovny C++ šablony [std::make_pair()](../standard-library/utility-functions.md#make_pair) využívá `enable_if`.

```cpp
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```

V tomto příkladu `make_pair("foo", "bar")` vrátí `pair<const char *, const char *>`. Řešení přetížení má zjistíte, které `func()` chcete. `pair<A, B>` má implicitně převodu konstruktor z `pair<X, Y>`.  Tato akce není nový – byl C ++ 98. Ale v C ++ 98/03, implicitně převodu konstruktor podpis vždy existuje, i když je `pair<int, int>(const pair<const char *, const char *>&)`.  Rozlišení přetížení nebude vědět, že pokus o vytvoření instance tento konstruktor rozbalí horribly protože `const char *` není implicitně převést na `int`; je pouze prohlížení podpisy, než funkce definice instance.  Proto je ukázkový kód nejednoznačný, protože podpisy převést `pair<const char *, const char *>` do obou `pair<int, int>` a `pair<string, string>`.

C ++ 11 vyřeší tato nejednoznačnost pomocí `enable_if` zajistit `pair<A, B>(const pair<X, Y>&)` existuje **pouze** při `const X&` implicitně převést na `A` a `const Y&` implicitně převést na `B`.  To umožňuje rozlišení přetížení k určení, který `pair<const char *, const char *>` není převoditelná na `pair<int, int>` a že přetížení, které nepřijímá `pair<string, string>` je přijatelná.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
