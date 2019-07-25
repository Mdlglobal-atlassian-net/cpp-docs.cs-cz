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
ms.openlocfilehash: 2b2051b0c854151cff9b439f5ec0a951c25a6387
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447631"
---
# <a name="invokeresult-class"></a>invoke_result – třída

Určuje návratový typ typu volat, který přebírá zadané typy argumentů v době kompilace. Přidáno v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Parametry

*Kompatibilní*\
Typ, který se má volat pro dotaz

*Argumentů*\
Typy seznamu argumentů pro dotaz na typ, který se má volat

## <a name="remarks"></a>Poznámky

Pomocí této šablony lze určit typ výsledku pro vyžádání *k vyžádání (* *args*...) v době kompilace, kde je možné *volat* a všechny typy v argumentech *argumentů* jsou kompletní typ, pole neznámého objektu Bound nebo případně `void`hodnota typu CV-Qualified. Člen třídy šablony pojmenovává návratový typ, který se má *volat* při vyvolání pomocí argumentů argumentů *..* .. `type` Člen je definován pouze *v případě,* že lze volat při volání pomocí argumentů argumentů *..* . `type` v nehodnoceném kontextu. V opačném případě třída šablony nemá žádného člena `type`, což umožňuje SFINAE testy na konkrétní sadě typů argumentů v době kompilace.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
