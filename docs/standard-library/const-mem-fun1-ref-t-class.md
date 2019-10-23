---
title: const_mem_fun1_ref_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: 76fae1ce29cb4c47870e45e8f946f6ff1fea1885
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688180"
---
# <a name="const_mem_fun1_ref_t-class"></a>const_mem_fun1_ref_t – třída

Třída adaptéru umožňující volat **konstantní** členskou funkci, která přijímá jeden argument jako objekt binární funkce při inicializaci s argumentem odkazu. Zastaralé v C++ 11, odebrané v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type, class Arg>
    class const_mem_fun1_ref_t
        : public binary_function<Type, Arg, Result>
{
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
};
```

### <a name="parameters"></a>Parametry

@No__t_1 *ODP* .
Ukazatel na členskou funkci třídy `Type`, která má být převedena na objekt funkce.

*levý* \
Objekt **const** , na kterém je volána členská funkce *PM* .

*pravé* \
Argument, který je přidělen *ODP*.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelná binární funkce.

## <a name="remarks"></a>Poznámky

Šablona třídy uchovává kopii *PM*, která musí být ukazatel na členskou funkci třídy `Type` v objektu Private member. Definuje jeho členskou funkci `operator()` jako vrácení (`left`. \* *ODP*) (`right`) **const**.

## <a name="example"></a>Příklad

Konstruktor `const_mem_fun1_ref_t` se obvykle nepoužívá přímo; pomocná funkce `mem_fun_ref` slouží k přizpůsobení členských funkcí. Příklady použití adaptérů členské funkce naleznete v tématu [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) .
