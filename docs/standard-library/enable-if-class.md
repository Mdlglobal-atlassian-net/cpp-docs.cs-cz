---
title: enable_if – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::enable_if
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
ms.openlocfilehash: 6e6b8a286dca8c451e6920e7f25f07829d3b453f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454217"
---
# <a name="enableif-class"></a>enable_if – třída

Podmíněně vytvoří instanci typu pro řešení přetížení SFINAE. Vnořená definice `enable_if<Condition,Type>::type` typu existuje – a je synonymum `Type`pro, pokud a pouze `Condition` Pokud má **hodnotu true**.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool B, class T = void>
struct enable_if;
```

### <a name="parameters"></a>Parametry

*B*\
Hodnota, která určuje existenci výsledného typu.

*Š*\
Typ, který má být vytvořen při hodnotě *B* .

## <a name="remarks"></a>Poznámky

Pokud je *B* true, `enable_if<B, T>` má vnořenou definici TypeDef s názvem "Type", která je synonymem pro *T*.

Pokud je *B* false, `enable_if<B, T>` nemá vnořenou definici TypeDef s názvem "Type".

Tato šablona aliasu je k dispozici:

```cpp
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```

V C++systému není při nahrazování parametrů šablony chyba sama o sobě, což se označuje jako *SFINAE* (Chyba při nahrazování není chyba). `enable_if` Obvykle se používá k odebrání kandidátů z Rozlišení přetěžování – to znamená, že je vráceno nastavení přetížení, aby jedna definice mohla být odmítnuta ve prospěch jiné. To odpovídá chování SFINAE. Další informace o SFINAE najdete v tématu [selhání při nahrazování není](https://go.microsoft.com/fwlink/p/?linkid=394798) v Wikipedii chyba.

Tady jsou čtyři příklady scénářů:

- Scénář 1: Zabalení návratového typu funkce:

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

- Scénář 2: Přidání parametru funkce s výchozím argumentem:

```cpp
    template <your_stuff>
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
}
```

- Scénář 3: Přidání parametru šablony s výchozím argumentem:

```cpp
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>
rest_of_function_declaration_goes_here
```

- Scénář 4: Pokud má funkce argument bez šablony, můžete zalomit jeho typ:

```cpp
    template <typename T>
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>
s) {// ...
}
```

Scénář 1 nefunguje s konstruktory a operátory převodu, protože nemají návratové typy.

Scénář 2 ponechá parametr nepojmenovaný. Je možné `::type Dummy = BAR`, že název `Dummy` je nepodstatný a že jeho název pravděpodobně může aktivovat upozornění "neodkazovaná" parametr ". Musíte zvolit `FOO` typ parametru funkce a `BAR` výchozí argument.  Mohli byste vyslovit **int** a `0`, ale uživatelé vašeho kódu by mohli omylem předat funkci dodatečné celé číslo, které by bylo ignorováno. Místo toho doporučujeme, abyste používali `void **` a buď `0` nebo **nullptr** , protože téměř nic není převoditelné na `void **`:

```cpp
template <your_stuff>
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```

Scénář 2 funguje také pro běžné konstruktory.  Nefunguje ale u operátorů převodu, protože nemůže mít další parametry.  Nefunguje ani pro konstruktory [variadické](../cpp/ellipses-and-variadic-templates.md) , protože přidání dodatečných parametrů způsobí, že balíček parametrů funkce je neodvozený kontext a tím se přestává účel `enable_if`.

Scénář 3 používá název `Dummy`, ale je nepovinný. Pouze " `typename = typename`" by fungovalo, ale pokud si myslíte, že je to divné, můžete použít "fiktivní" název, ale nepoužívat ho, který by se mohl použít i v definici funkce. Pokud neudělíte typu `enable_if`, nastaví se jako výchozí hodnota void a je naprosto rozumný, protože nezáleží na tom, `Dummy` co je. To funguje pro všechno, včetně operátorů převodu a konstruktorů [variadické](../cpp/ellipses-and-variadic-templates.md) .

Scénář 4 funguje v konstruktorech, které nemají návratové typy, a tímto způsobem řeší omezení zabalení scénáře 1.  Scénář 4 je však omezen na argumenty funkce bez šablony, které nejsou vždy k dispozici.  (Použití scénáře 4 u argumentu funkce s šablonou zabraňuje odvození argumentu šablony při práci.)

`enable_if`je výkonná, ale také nebezpečná, pokud se nepoužívá.  Vzhledem k tomu, že jeho účelem je udělat kandidáty v době, kdy je to v nepoužitém případě zneužito, může jeho účinky být velice matoucí.  Tady je několik doporučení:

- Nepoužívejte `enable_if` k výběru mezi implementacemi v době kompilace. Ještě nic nepište `enable_if` pro `CONDITION` a druhý pro `!CONDITION`.  Místo toho použijte model *odeslání značky* , například algoritmus, který vybírá implementace v závislosti na síle iterátorů, které jsou uvedeny.

- Nepoužívejte `enable_if` k vymáhání požadavků.  Pokud chcete ověřit parametry šablony a v případě, že se ověření nepovede, vyzpůsobíte chybu namísto výběru jiné implementace, použijte [static_assert](../cpp/static-assert.md).

- Použijte `enable_if` v případě, že máte nastavenou přetíženou metodu, která způsobuje jinak dobrý kód jako nejednoznačný.  Nejčastěji k tomu dochází v implicitním převádění konstruktorů.

## <a name="example"></a>Příklad

Tento příklad vysvětluje, jak C++ standardní funkce šablony knihovny [std:: make_pair ()](../standard-library/utility-functions.md#make_pair) `enable_if`využívá.

```cpp
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```

V tomto příkladu `make_pair("foo", "bar")` vrátí `pair<const char *, const char *>`. Rozlišení přetěžování musí určovat, `func()` které chcete. `pair<A, B>`má implicitní převod konstruktoru z `pair<X, Y>`.  To není nové – bylo v C++ 98. V jazyce C++ 98/03 však signatura implicitního převodu vždy existuje, i `pair<int, int>(const pair<const char *, const char *>&)`když je to.  Rozlišení přetížení nezáleží na tom, že pokus o vytvoření instance tohoto konstruktoru rozbalí `const char *` horribly, protože není implicitně převoditelné na **int**; hledá se pouze signatury, než se vytvoří instance funkce.  Proto je kód příkladu dvojznačný, protože signatury existují pro převod `pair<const char *, const char *>` na obojí `pair<int, int>` i `pair<string, string>`.

C++ 11 vyřešila tuto nejednoznačnost `enable_if` pomocí, aby se zajistilo `const X&` , že existuje **pouze** v `A` případě `const Y&` , že `pair<A, B>(const pair<X, Y>&)` je implicitně `B`převoditelná na a je implicitně převoditelná na.  To umožňuje rozlišení přetížení, aby bylo `pair<const char *, const char *>` možné určit, že `pair<int, int>` se nedá převést na a že `pair<string, string>` přetížení, které trvá, je životaschopné.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
