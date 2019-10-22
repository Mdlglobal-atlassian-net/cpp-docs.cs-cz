---
title: mem_fun_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_t
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
ms.openlocfilehash: 3c6606fe4d2df3b6068c3bb8194dc380344f7d97
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689370"
---
# <a name="mem_fun_t-class"></a>mem_fun_t – třída

Třída adaptéru, která `non_const` umožňuje, aby při inicializaci s argumentem ukazatele převolala žádné argumenty jako unární objekt funkce. Zastaralé v C++ 11, odebrané v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;
};
```

### <a name="parameters"></a>Parametry

*_Pm* \
Ukazatel na členskou funkci třídy `Type`, která má být převedena na objekt funkce.

*_Pleft* \
Objekt, na kterém je volána členská funkce *_Pm*

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelná unární funkce.

## <a name="remarks"></a>Poznámky

Šablona třídy uchovává kopii *_Pm*, která musí být ukazatel na členskou funkci třídy `Type` v objektu Private member. Definuje jeho členskou funkci `operator()` jako vrácení (`_Pleft` ->*  `_Pm`) ().

## <a name="example"></a>Příklad

Konstruktor `mem_fun_t` se obvykle nepoužívá přímo; pomocná funkce `mem_fun` slouží k přizpůsobení členských funkcí. Příklad použití adaptérů členské funkce naleznete v tématu [mem_fun](../standard-library/functional-functions.md#mem_fun) .
