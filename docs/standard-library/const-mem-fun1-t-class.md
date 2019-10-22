---
title: const_mem_fun1_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 1af44635400037c6359b13c4f2925c3ac7f2d9d5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689753"
---
# <a name="const_mem_fun1_t-class"></a>const_mem_fun1_t – třída

Třída adaptéru umožňující volat **konstantní** členskou funkci, která přijímá jeden argument jako objekt binární funkce při inicializaci s argumentem ukazatele. Zastaralé v C++ 11, odebrané v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* member_ptr)(Arg) const);
    Result operator()(const Type* left, Arg right) const;
};
```

### <a name="parameters"></a>Parametry

*member_ptr* \
Ukazatel na členskou funkci třídy `Type`, která má být převedena na objekt funkce.

*levý* \
Objekt **const** , na kterém je volána členská funkce *member_ptr* .

*pravé* \
Argument, který je uveden pro *member_ptr*.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelná binární funkce.

## <a name="remarks"></a>Poznámky

Šablona třídy uchovává kopii *member_ptr*, která musí být ukazatel na členskou funkci třídy `Type` v objektu Private member. Definuje jeho členskou funkci `operator()` jako vrácení `(left->member_ptr)(right) const`.

## <a name="example"></a>Příklad

Konstruktor `const_mem_fun1_t` se zřídka používá přímo. `mem_fn` slouží k přizpůsobení členských funkcí. Příklad použití adaptérů členské funkce naleznete v tématu [mem_fn](../standard-library/functional-functions.md#mem_fn) .
