---
title: invoke_result třídy
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: 7c03240d3ee666fcda30562279a8dbda2ca8dc7b
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006848"
---
# <a name="invokeresult-class"></a>invoke_result třídy

Určuje návratový typ volatelného typu, který přijímá zadanými typy argumentu v době kompilace. Přidáno v C ++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Parametry

*Volatelný*<br/>
Volatelný typ dotazu.

*Args*<br/>
Typy seznamu argumentů na volatelný typ dotazu.

## <a name="remarks"></a>Poznámky

Pomocí této šablony můžete určit typ výsledku *Callable*(*Args*...) v době kompilace, ve kterém *Callable* a všechny typy v *Args* jsou všechny úplný typ, pole neznámým rozsahem nebo pravděpodobně cv kvalifikovaný `void`. `type` Názvy členů třídy šablony návratový typ *Callable* při vyvolání pomocí argumentů *Args*... `type` Člen je definováno pouze, pokud *Callable* lze volat při vyvolání pomocí argumentů *Args*... v nevyhodnoceném kontextu. V opačném případě šablony třídy nemá žádný člen `type`, který umožňuje sfinae u testů na určitou sadu typy argumentů v době kompilace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke](functional-functions.md#invoke)
