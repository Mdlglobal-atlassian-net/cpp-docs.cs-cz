---
title: const_mem_fun1_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 8ccd9d7e58b9cadec83b64df5553564db20a5745
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244518"
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t – třída

Třída adaptéru umožňující **const** členskou funkci, která přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem ukazatele. Zastaralé v C ++ 11, v C ++ 17 odebrané.

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

*member_ptr*\
Ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

*doleva*\
**Const** objekt, který *member_ptr* členská funkce je volána v.

*doprava*\
Argument, který je právě přiřazen k *member_ptr*.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelnou binární funkci.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá kopie *member_ptr*, která musí být ukazatel na členskou funkci třídy `Type`, v objektu privátní člen. Definuje jeho členskou funkci `operator()` jako vracející `(left->member_ptr)(right) const`.

## <a name="example"></a>Příklad

Konstruktor třídy `const_mem_fun1_t` je zřídka se používá přímo. `mem_fn` slouží k přizpůsobení členské funkce. Zobrazit [mem_fn –](../standard-library/functional-functions.md#mem_fn) příklad, jak používat adaptéry členské funkce.
