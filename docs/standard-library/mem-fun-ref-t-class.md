---
title: mem_fun_ref_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_ref_t
helpviewer_keywords:
- mem_fun_ref_t class
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
ms.openlocfilehash: d8f5ef05d1bdeec694cdf22d7e7a163478127dfc
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687762"
---
# <a name="mem_fun_ref_t-class"></a>mem_fun_ref_t – třída

Třída adaptéru umožňující `non_const` členskou funkci, která nepřijímá žádné argumenty, které se mají volat jako unární objekt funkce při inicializaci s argumentem odkazu. Zastaralé v C++ 11, odebrané v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type>
class mem_fun_ref_t : public unary_function<Type, Result> {
    explicit mem_fun_ref_t(
    Result (Type::* _Pm)());

    Result operator()(Type& left) const;
};
```

### <a name="parameters"></a>Parametry

*_Pm* \
Ukazatel na členskou funkci třídy `Type`, která má být převedena na objekt funkce.

*levý* \
Objekt, na kterém je volána členská funkce *_Pm*

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelná unární funkce.

## <a name="remarks"></a>Poznámky

Šablona třídy uchovává kopii *_Pm*, která musí být ukazatel na členskou funkci třídy `Type` v objektu Private member. Definuje jeho členskou funkci `operator()` jako vrácení (**Left**. * `_Pm`) ().

## <a name="example"></a>Příklad

Konstruktor `mem_fun_ref_t` se obvykle nepoužívá přímo; pomocná funkce `mem_fun_ref` slouží k přizpůsobení členských funkcí. Příklad použití adaptérů členské funkce naleznete v tématu [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) .
