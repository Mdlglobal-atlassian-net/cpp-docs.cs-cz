---
title: enable_if – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::enable_if
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
ms.openlocfilehash: b6990dba20643b35dde36a492d40c3e3e76ae0b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413759"
---
# <a name="enableif-class"></a>enable_if – třída

Podmíněně provede instance typu pro sfinae u řešení přetížení. Vnořené typedef `enable_if<Condition,Type>::type` existuje – a je synonymum pro `Type`– pouze v případě `Condition` je **true**.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool B, class T = void>
struct enable_if;
```

### <a name="parameters"></a>Parametry

*B*<br/>
Hodnota, která určuje existenci výsledný typ.

*T*<br/>
Typ, který chcete vytvořit instanci v případě *B* má hodnotu true.

## <a name="remarks"></a>Poznámky

Pokud *B* má hodnotu true, `enable_if<B, T>` obsahuje vnořené typedef s názvem "typ", který je synonymum pro *T*.

Pokud *B* má hodnotu false, `enable_if<B, T>` nemá vnořené typedef s názvem "type".

Tato šablona aliasu je k dispozici:

```cpp
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```

V jazyce C++, selhání nahrazování parametrů šablony není chyba sám o sobě – to se označuje jako *SFINAE* (nahrazení selhání není chyba). Obvykle `enable_if` slouží k odebrání kandidáty rozlišení přetížení – to znamená, tím sady přetížení – tak, aby ve prospěch druhého může být odmítnutá jednu definici. To odpovídá sfinae u chování. Další informace o sfinae u najdete v tématu [nahrazení selhání není chyba](http://go.microsoft.com/fwlink/p/?linkid=394798) v encyklopedii Wikipedia.

Tady jsou čtyři ukázkové scénáře:

- Scénář 1: Obtékání návratový typ funkce:

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

- Scénář 3: Přidání parametru šablony, která má výchozí argument:

```cpp
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>
rest_of_function_declaration_goes_here
```

- Scénář 4: Pokud má vaše funkce bez použití šablon argument, můžete zabalit její typ:

```cpp
    template <typename T>
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>
s) {// ...
}
```

Scénář 1 nebude fungovat s konstruktory a operátory převodu, protože nemají návratové typy.

Scénář 2 opustí parametr nepojmenované. Řekněte `::type Dummy = BAR`, ale název `Dummy` je bezvýznamná, a zadání názvu je pravděpodobné, že aktivovat upozornění "neodkazovaný parametr". Budete muset zvolit `FOO` typ parametru funkce a `BAR` výchozí argument.  Řekněte **int** a `0`, ale pak uživatelé váš kód může nechtěně předat do funkce další celé číslo, které by se ignoruje. Namísto toho doporučujeme použít `void **` a buď `0` nebo **nullptr** protože téměř nic není převoditelná na `void **`:

```cpp
template <your_stuff>
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```

Scénář 2 také funguje pro běžné konstruktory.  Však to nebude fungovat pro operátory převodu protože nelze přijímají nadbytečné parametry.  Také nefunguje pro [variadické](../cpp/ellipses-and-variadic-templates.md) konstruktory protože přidání dalších parametrů vytvoří parametr funkce kontextu odvodit bez aktualizací Service pack a tím poráží účel `enable_if`.

Scénář 3 používá název `Dummy`, ale je volitelné. Právě " `typename = typename`" bude fungovat, ale pokud se domníváte, která vypadá divné, můžete použít "fiktivní" název – stačí nepoužívejte ho, které mohou být také použity v definici funkce. Pokud není typu `enable_if`, použije se výchozí typ void a, který je zcela přiměřené, protože vám nezáleží na co `Dummy` je. Tento postup funguje pro vše, včetně operátorů převodu a [variadické](../cpp/ellipses-and-variadic-templates.md) konstruktory.

Scénář 4 funguje v konstruktory, které nemají návratové typy a tím řeší omezení zabalení scénář 1.  Scénář 4 je ale omezený na argumenty bez použití šablon funkce, které nejsou vždycky k dispozici.  (Použití scénář 4 na argumentu šablony funkce zabrání odvození argumentu šablony z na tom pracujeme.)

`enable_if` je efektivní, ale také nebezpečné, pokud je chybná.  Protože jejím účelem je, aby kandidáty zmizí před řešení přetížení se potenciálně nebezpečného, může být velmi matoucí jeho účinky.  Zde je několik doporučení:

- Nepoužívejte `enable_if` k výběru mezi implementacemi v době kompilace. Nezapisujte někdy jedna `enable_if` pro `CONDITION` a druhý pro `!CONDITION`.  Místo toho použijte *označit odeslání* vzor – například algoritmus, který vybere implementace v závislosti na silné iterátory, že získá.

- Nepoužívejte `enable_if` k vynucení požadavků.  Pokud chcete ověřit parametry šablony a pokud se ověření nezdaří, způsobit chybu místo výběru jinou implementaci, použijte [static_assert](../cpp/static-assert.md).

- Použití `enable_if` případě, že máte skupinu přetížení, která provádí jinak dobré kódu nejednoznačný.  Nejčastěji používané k tomuto dochází u Implicitním převodem konstruktory.

## <a name="example"></a>Příklad

Tento příklad vysvětluje, jak C++ funkce standardní knihovny šablon [std::make_pair()](../standard-library/utility-functions.md#make_pair) využívá `enable_if`.

```cpp
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```

V tomto příkladu `make_pair("foo", "bar")` vrátí `pair<const char *, const char *>`. Řešení přetížení má k určení, které `func()` chcete. `pair<A, B>` má implicitně převodu konstruktoru z `pair<X, Y>`.  To není novinka, v C ++ 98. Nicméně v C ++ 98/03, podpis konstruktoru implicitně převodu vždy existuje, i v případě, že je `pair<int, int>(const pair<const char *, const char *>&)`.  Řešení přetížení není pro vás, že pokus o vytvoření instance tohoto konstruktoru rozbalí horribly protože `const char *` není implicitně převést na **int**; je jen prohlížení podpisy, před funkcí jsou definice vytvořit instanci.  Proto ukázkový kód je nejednoznačný, protože existují podpisy pro převod `pair<const char *, const char *>` zároveň `pair<int, int>` a `pair<string, string>`.

C ++ 11 tuto nejednoznačnost vyřešit pomocí `enable_if` zajistit `pair<A, B>(const pair<X, Y>&)` existuje **pouze** při `const X&` implicitně převést na `A` a `const Y&` implicitně převést na `B`.  To umožňuje rozlišení přetížení k určení, která `pair<const char *, const char *>` není převoditelná na `pair<int, int>` a že přetížení, která přijímá `pair<string, string>` je přijatelné.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
