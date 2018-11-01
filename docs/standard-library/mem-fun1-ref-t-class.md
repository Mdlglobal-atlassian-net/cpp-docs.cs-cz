---
title: mem_fun1_ref_t – třída
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::mem_fun1_ref_t
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
ms.openlocfilehash: 4169ac00cfeeb2bd9f38ef0e7eb30da819fbff5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488059"
---
# <a name="memfun1reft-class"></a>mem_fun1_ref_t – třída

Třída adaptéru umožňující `non_const` členskou funkci, která přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem reference.

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

*_Pm*<br/>
Ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

*doleva*<br/>
Objekt, který *_Pm* členská funkce je volána v.

*doprava*<br/>
Argument, který je právě přiřazen k *_Pm*.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelnou binární funkci.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá kopie *_Pm*, která musí být ukazatel na členskou funkci třídy `Type`, v objektu privátní člen. Definuje jeho členskou funkci `operator()` jako vracející ( **levé**.\* `_Pm`) ( **správné**).

## <a name="example"></a>Příklad

Konstruktor třídy `mem_fun1_ref_t` se obvykle nepoužívá přímo; pomocnou funkci `mem_fun_ref` slouží k přizpůsobení členské funkce. Zobrazit [mem_fun_ref –](../standard-library/functional-functions.md#mem_fun_ref) příklad, jak používat adaptéry členské funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
