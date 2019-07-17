---
title: const_mem_fun1_ref_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: 59790b5791dc50d217053dc7a13856d436101020
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244543"
---
# <a name="constmemfun1reft-class"></a>const_mem_fun1_ref_t – třída

Třída adaptéru umožňující **const** členskou funkci, která přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem reference. Zastaralé v C ++ 11, v C ++ 17 odebrané.

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

*Odp.* \
Ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

*doleva*\
**Const** objekt, který *Pm* členská funkce je volána v.

*doprava*\
Argument, který je právě přiřazen k *Pm*.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelnou binární funkci.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá kopie *Pm*, která musí být ukazatel na členskou funkci třídy `Type`, v objektu privátní člen. Definuje jeho členskou funkci `operator()` jako vracející (`left`.\* *PM*) (`right`) **const**.

## <a name="example"></a>Příklad

Konstruktor třídy `const_mem_fun1_ref_t` se obvykle nepoužívá přímo; pomocnou funkci `mem_fun_ref` slouží k přizpůsobení členské funkce. Zobrazit [mem_fun_ref –](../standard-library/functional-functions.md#mem_fun_ref) příklady, jak používat adaptéry členské funkce.
