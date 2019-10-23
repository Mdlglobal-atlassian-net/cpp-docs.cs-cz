---
title: const_mem_fun_ref_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_ref_t
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
ms.openlocfilehash: 8ce29eb0d2122dbd95fea34fa59f3fa11b9b388e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689764"
---
# <a name="const_mem_fun_ref_t-class"></a>const_mem_fun_ref_t – třída

Třída adaptéru umožňující volat **konstantní** členskou funkci, která nepřijímá žádné argumenty jako unární objekt funkce při inicializaci s argumentem odkazu. Zastaralé v C++ 11, odebrané v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type>
    class const_mem_fun_ref_t
: public unary_function<Type, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type& left) const;
};
```

### <a name="parameters"></a>Parametry

@No__t_1 *ODP* .
Ukazatel na členskou funkci třídy `Type`, která má být převedena na objekt funkce.

*levý* \
Objekt, na kterém je volána členská funkce *PM* .

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelná unární funkce.

## <a name="remarks"></a>Poznámky

Šablona třídy uchovává kopii *PM*, která musí být ukazatel na členskou funkci třídy `Type` v objektu Private member. Definuje jeho členskou funkci `operator()` jako vrácení (**Left**. \* `Pm`) () **const**.

## <a name="example"></a>Příklad

Konstruktor `const_mem_fun_ref_t` se obvykle nepoužívá přímo; pomocná funkce `mem_fun_ref` slouží k přizpůsobení členských funkcí. Příklad použití adaptérů členské funkce naleznete v tématu [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) .
