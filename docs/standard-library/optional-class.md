---
title: Volitelná třída
ms.date: 11/04/2016
f1_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
helpviewer_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
ms.openlocfilehash: d9c4bf5356e6ff163ecdf7e1a80bc55453d59003
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689149"
---
# <a name="optional-class"></a>Volitelná třída

Šablona třídy `optional<T>` popisuje objekt, který může nebo nemusí obsahovat hodnotu typu `T`, která se označuje jako *obsažená hodnota*.

Pokud instance `optional<T>` obsahuje hodnotu, obsažená hodnota je přidělena v rámci úložiště objektu `optional` v oblasti vhodně zarovnané pro typ `T`. Pokud je `optional<T>` převedena na `bool`, výsledek je `true`, pokud objekt obsahuje hodnotu; v opačném případě je `false`.

Objekt typu intypeed Object `T` nesmí být [in_place_t](in-place-t-struct.md) ani [nullopt_t](nullopt-t-structure.md). `T` musí být *zničitelné*, to znamená, že jeho destruktor musí znovu získat všechny vlastněné prostředky a nemůže vyvolat žádné výjimky.

Třída `optional` je v C++ 17 novinkou.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class optional
{
    using value_type = T;
};

template<class T> optional(T) -> optional<T>;
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
| **Konstruktory a destruktor** | |
|[optional](#optional) | Vytvoří objekt typu `optional`. |
|[~ volitelné](#optional-destructor) | Zničí objekt typu `optional`. |
| **Přiřazení** | |
| [operátor =](#op_eq) | Nahradí `optional` kopií jiného `optional`. |
| [emplace](#op_eq) | Inicializuje obsaženou hodnotu se zadanými argumenty. |
| **Adresu** | |
| [adresu](#swap) | Zamění obsaženou hodnotu nebo prázdný stav s jiným `optional`. |
| **Pozorovatelů** | |
| [has_value](#has_value) | Vrátí, zda objekt `optional` obsahuje hodnotu. |
| [value](#value) | Vrátí obsaženou hodnotu. |
| [value_or](#value_or) | Vrátí obsaženou hodnotu nebo alternativu, pokud není zadána žádná hodnota. |
| [operátor->](#op_as) | Odkazuje na obsaženou hodnotu objektu `optional`. |
| [podnikatel](#op_mem) | Odkazuje na obsaženou hodnotu objektu `optional`. |
| [operátor bool](#op_bool) | Vrátí, zda objekt `optional` obsahuje hodnotu. |
| **Modifikátory** | |
| [nové](#reset) | Obnoví `optional` zničením obsažené hodnoty. |

## <a name="has_value"></a>has_value

```cpp
constexpr bool has_value() const noexcept;
```

## <a name="optional"></a>Volitelný konstruktor

Vytvoří objekt typu `optional`.

```cpp
constexpr optional() noexcept;
constexpr optional(nullopt_t nullopt) noexcept;
constexpr optional(const optional& rhs);
constexpr optional(optional&& rhs) noexcept;

template <class... Args>
constexpr explicit optional(in_place_t, Args&&... args);

template <class U, class... Args>
constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);

template <class U = T>
explicit constexpr optional(U&& rhs);

template <class U>
explicit optional(const optional<U>& rhs);

template <class U>
explicit optional(optional<U>&& rhs);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce rhs* \
@No__t_0 ke zkopírování nebo přesunutí konstrukce obsažené hodnoty z.

*i_list* \
Seznam inicializátorů, z něhož se má vytvořit obsažená hodnota

\ *argumentů*
Seznam argumentů, z něhož se má vytvořit obsažená hodnota

### <a name="remarks"></a>Poznámky

`constexpr optional() noexcept;` 
 `constexpr optional(nullopt_t nullopt) noexcept;` tyto konstruktory vytvoří `optional`, který neobsahuje hodnotu.

`constexpr optional(const optional& rhs);` konstruktor Copy inicializuje z obsažené hodnoty argumentu obsaženou hodnotu. Je definována jako **Odstraněná** , pokud `is_copy_constructible_v<T>` není true a je triviální, pokud `is_trivially_copy_constructible_v<T>` true.

`constexpr optional(optional&& rhs) noexcept;` konstruktor Move inicializuje obsaženou hodnotu přesunutím z obsažené hodnoty argumentu. Neúčastní řešení přetížení, pokud `is_move_constructible_v<T>` není pravda a je triviální, pokud `is_trivially_move_constructible_v<T>` true.

`template <class... Args> constexpr explicit optional(in_place_t, Args&&... args);` Direct inicializuje obsaženou hodnotu jako při použití argumentů `std::forward<Args>(args)`. Tento konstruktor je `constexpr`, je-li použit konstruktor `T` `constexpr`. Neúčastní řešení přetížení, pokud `is_constructible_v<T, Args...>` není pravda.

`template <class U, class... Args> constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);` Direct inicializuje obsaženou hodnotu jako při použití argumentů `i_list, std::forward<Args>(args)`. Tento konstruktor je `constexpr`, je-li použit konstruktor `T` `constexpr`. Neúčastní řešení přetížení, pokud `is_constructible_v<T, initializer_list<U>&, Args&&...>` není pravda.

`template <class U = T> explicit constexpr optional(U&& rhs);` Direct inicializuje obsaženou hodnotu jako při použití `std::forward<U>(v)`. Tento konstruktor je `constexpr`, je-li použit konstruktor `T` `constexpr`. Nepodílí se na řešení přetížení, pokud `is_constructible_v<T, U&&>` není true a `is_same_v<remove_cvref_t<U>, in_place_t>` a `is_same_v<remove_cvref_t<U>, optional>` mají hodnotu false.

`template <class U> explicit optional(const optional<U>& rhs);` Pokud *Zarovnání indirekce RHS* obsahuje hodnotu, přímo inicializuje obsaženou hodnotu z obsažené hodnoty argumentu. Nepodílí se na rozlišení přetěžování, pokud `is_constructible_v<T, const U&>` hodnotu true a `is_constructible_v<T, optional<U>&>`, `is_constructible_v<T, optional<U>&&>`, `is_constructible_v<T, const optional<U>&>`, `is_constructible_v<T, const optional<U>&&>`, `is_convertible_v<optional<U>&, T>`, `is_convertible_v<optional<U>&&, T>`, `is_convertible_v<const optional<U>&, T>` a `is_convertible_v<const optional<U>&&, T>` jsou všechny nepravdivé.

`template <class U> explicit optional(optional<U>&& rhs);` Pokud *Zarovnání indirekce RHS* obsahuje hodnotu, přímo inicializuje obsaženou hodnotu jako při použití `std::move(*rhs)`. Nepodílí se na rozlišení přetěžování, pokud `is_constructible_v<T, U&&>` hodnotu true a `is_constructible_v<T, optional<U>&>`, `is_constructible_v<T, optional<U>&&>`, `is_constructible_v<T, const optional<U>&>`, `is_constructible_v<T, const optional<U>&&>`, `is_convertible_v<optional<U>&, T>`, `is_convertible_v<optional<U>&&, T>`, `is_convertible_v<const optional<U>&, T>` a `is_convertible_v<const optional<U>&&, T>` jsou všechny nepravdivé.

## <a name="optional-destructor"></a>~ Volitelný destruktor

Zničí všechny netriviální zničitelné obsažené hodnoty, pokud je k dispozici, vyvoláním svého destruktoru.

```cpp
~optional();
```

### <a name="remarks"></a>Poznámky

Pokud je `T` triviální zničitelné, `optional<T>` je také triviální zničitelné.

## <a name="op_eq"></a>operátor =

Nahradí obsaženou hodnotu `optional` kopírováním nebo přesunutím z jiné hodnoty, která byla obsaženy `optional`.

```cpp
optional& operator=(nullopt_t) noexcept;
optional& operator=(const optional& rhs);
optional& operator=(optional&&) noexcept( /* see below */ );

template <class U = T>
    optional& operator=(U&&);

template <class U>
optional& operator=(const optional<U>&);

template <class U>
    optional& operator=(optional<U>&&);

template <class... Args>
T& emplace(Args&&...);

template <class U, class... Args>
T& emplace(initializer_list<U>, Args&&...);
```

## <a name="op_as"></a>operátor->

Odkazuje na obsaženou hodnotu objektu `optional`.

```cpp
constexpr const T* operator->() const;
constexpr T* operator->();
```

## <a name="op_mem"></a>podnikatel

Odkazuje na obsaženou hodnotu objektu `optional`.

```cpp
constexpr const T& operator*() const&;
constexpr T& operator*() &;
constexpr T&& operator*() &&;
constexpr const T&& operator*() const&&;
```

## <a name="op_bool"></a>operátor bool

Oznamuje, zda objekt `optional` má obsaženou hodnotu.

```cpp
constexpr explicit operator bool() const noexcept;
```

## <a name="reset"></a>nové

Efektivně volá destruktor obsaženého objektu, pokud existuje, a nastaví jej na Neinicializovaný stav.

```cpp
void reset() noexcept;
```

## <a name="swap"></a>adresu

```cpp
template<class T>
void swap(optional<T>&, optional<T>&) noexcept;
```

## <a name="value"></a>osa

```cpp
constexpr const T& value() const&;
constexpr T& value() &;
constexpr T&& value() &&;
constexpr const T&& value() const&&;
```

## <a name="value_or"></a>value_or

```cpp
template <class U>
    constexpr T value_or(U&&) const&;
template <class U>
    constexpr T value_or(U&&) &&;
```

## <a name="see-also"></a>Viz také:

[\<optional >](optional.md)
