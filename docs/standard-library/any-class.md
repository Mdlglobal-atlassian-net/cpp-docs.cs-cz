---
title: všechny třídy
ms.date: 04/04/2019
f1_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
helpviewer_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
ms.openlocfilehash: 050276da665ab6ed3eb53d9e65bfea06b88bcbea
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267979"
---
# <a name="any-class"></a>všechny třídy

Úložiště instance typu, který splňuje požadavky na konstruktor nebo ho nemá žádnou hodnotu, která je volána stav třídy libovolného objektu.

Uložené instance se nazývá hodnotě obsažené. Dva stavy jsou stejné, pokud oba nemají žádnou hodnotu, nebo mít hodnotu a omezením hodnoty jsou stejné.

## <a name="syntax"></a>Syntaxe

```cpp
class any
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[Všechny](#any)|Vytvoří objekt typu `any`.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[emplace –](#emplace)|Nastaví hodnotu žádné.|
|[has_value](#has_value)|Vrátí **true** Pokud má hodnotu.|
|[reset](#reset)|Resetuje žádný.|
|[swap](#swap)|Prohodí dva objekty.|
|[type](#type)|Vrátí hodnotu libovolného typu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_eq)|Nahradí všechny s kopií jiného any.|

## <a name="any"></a> Všechny

Vytvoří objekt typu `any`. Také obsahuje destruktor.

```cpp
constexpr any() noexcept;
any(const any& other);
any(any&& other) noexcept;
template <class T>
    any(T&& value);
template <class T, class... Args>
    explicit any(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    explicit any(in_place_type_t<T>, initializer_list<U>, Args&&...);

~any();
```

## <a name="emplace"></a> emplace –

Nastaví hodnotu žádné.

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a> has_value –

Vrátí **true** Pokud má hodnotu.

```cpp
bool has_value() const noexcept;
```

## <a name="op_eq"></a> operátor =

Nahradí všechny s kopií jiného any.

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>Parametry

*doprava*\
Všechny kopírovaná do všechny.

## <a name="reset"></a> Resetovat

Resetuje žádný.

```cpp
void reset() noexcept;
```

## <a name="swap"></a> Prohození

Prohodí dva objekty.

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a> Typ

Vrátí hodnotu libovolného typu.

```cpp
const type_info& type() const noexcept;
```
