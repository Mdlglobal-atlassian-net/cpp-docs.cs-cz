---
title: invoke_result – třída
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: a5f67935bde103cf10c1bd9948ac1388f5221322
ms.sourcegitcommit: f38f770bfda1c174d2b81fabda7c893b15bd83a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473888"
---
# <a name="invoke_result-class"></a>invoke_result – třída

Určuje návratový typ typu volat, který přebírá zadané typy argumentů v době kompilace. Přidáno v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<class Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Parametry

*Volat*\
Typ, který se má volat pro dotaz

\ *argumentů*
Typy seznamu argumentů pro dotaz na typ, který se má volat

## <a name="remarks"></a>Poznámky

Pomocí této šablony lze určit typ výsledku pro vyžádání k *vyžádání (* *args*...) v době kompilace, kde je možné *volat* a všechny typy v argumentech *argumentů* jsou kompletní typ, pole neznámého objektu Bound nebo pravděpodobně `void`s možnou odchylkou. `type` člen šablony třídy pojmenuje návratový typ *volat* při vyvolání *pomocí argumentů argumentů..* .. Člen `type` je definován pouze *v případě, že lze* volat volání při volání *pomocí argumentů argumentů..* . v nehodnoceném kontextu. V opačném případě šablona třídy nemá žádné členské `type`, což umožňuje SFINAE testy v konkrétní sadě typů argumentů v době kompilace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také

[< type_traits >](../standard-library/type-traits.md)\
[Zavolejte](functional-functions.md#invoke)
