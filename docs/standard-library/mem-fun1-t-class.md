---
title: mem_fun1_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: 00d9322a8f0530da2e48b3f16fb52c00f9d1b075
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687738"
---
# <a name="mem_fun1_t-class"></a>mem_fun1_t – třída

Třída adaptéru, která `non_const` umožňuje, aby byla při inicializaci s argumentem ukazatele volána členská funkce, která přijímá jeden argument jako objekt binární funkce. Zastaralé v C++ 11, odebrané v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;
};
```

### <a name="parameters"></a>Parametry

*_Pm* \
Ukazatel na členskou funkci třídy `Type`, která má být převedena na objekt funkce.

*_Pleft* \
Objekt, na kterém je volána členská funkce *_Pm*

*pravé* \
Argument, který je uveden pro *_Pm*.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelná binární funkce.

## <a name="remarks"></a>Poznámky

Šablona třídy uchovává kopii *_Pm*, která musí být ukazatel na členskou funkci třídy `Type` v objektu Private member. Definuje jeho členskou funkci `operator()` jako vrácení ( **_Pleft** -> \* `_Pm`) (**vpravo**).

## <a name="example"></a>Příklad

Konstruktor `mem_fun1_t` se obvykle nepoužívá přímo; pomocná funkce `mem_fun` slouží k přizpůsobení členských funkcí. Příklad použití adaptérů členské funkce naleznete v tématu [mem_fun](../standard-library/functional-functions.md#mem_fun) .
