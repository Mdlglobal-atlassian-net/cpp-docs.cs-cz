---
title: mem_fun1_ref_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_ref_t
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
ms.openlocfilehash: 238d6147b2afa5ca3e143bc57aa4892e17d2c869
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687746"
---
# <a name="mem_fun1_ref_t-class"></a>mem_fun1_ref_t – třída

Třída adaptéru, která `non_const` umožňuje, aby byla při inicializaci s argumentem odkazu volána členská funkce, která přijímá jeden argument jako objekt binární funkce. Zastaralé v C++ 11, odebrané v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_ref_t : public binary_function<Type, Arg, Result> {
    explicit mem_fun1_ref_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type& left,
    Arg right) const;
};
```

### <a name="parameters"></a>Parametry

*_Pm* \
Ukazatel na členskou funkci třídy `Type`, která má být převedena na objekt funkce.

*levý* \
Objekt, na kterém je volána členská funkce *_Pm*

*pravé* \
Argument, který je uveden pro *_Pm*.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelná binární funkce.

## <a name="remarks"></a>Poznámky

Šablona třídy uchovává kopii *_Pm*, která musí být ukazatel na členskou funkci třídy `Type` v objektu Private member. Definuje jeho členskou funkci `operator()` jako vrácení (**Left**. \* `_Pm`) (**vpravo**).

## <a name="example"></a>Příklad

Konstruktor `mem_fun1_ref_t` se obvykle nepoužívá přímo; pomocná funkce `mem_fun_ref` slouží k přizpůsobení členských funkcí. Příklad použití adaptérů členské funkce naleznete v tématu [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) .
