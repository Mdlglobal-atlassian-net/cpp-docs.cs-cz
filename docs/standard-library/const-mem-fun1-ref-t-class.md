---
title: const_mem_fun1_ref_t – třída
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: e90ac09543c0704cf900e0fc5448e295034dcb66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516439"
---
# <a name="constmemfun1reft-class"></a>const_mem_fun1_ref_t – třída

Třída adaptéru umožňující **const** členskou funkci, která přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem reference.

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

*Odp.*<br/>
Ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

*doleva*<br/>
**Const** objekt, který *Pm* členská funkce je volána v.

*doprava*<br/>
Argument, který je právě přiřazen k *Pm*.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelnou binární funkci.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá kopie *Pm*, která musí být ukazatel na členskou funkci třídy `Type`, v objektu privátní člen. Definuje jeho členskou funkci `operator()` jako vracející ( `left`.\* *PM*) ( `right`) **const**.

## <a name="example"></a>Příklad

Konstruktor třídy `const_mem_fun1_ref_t` se obvykle nepoužívá přímo; pomocnou funkci `mem_fun_ref` slouží k přizpůsobení členské funkce. Zobrazit [mem_fun_ref –](../standard-library/functional-functions.md#mem_fun_ref) příklady, jak používat adaptéry členské funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
