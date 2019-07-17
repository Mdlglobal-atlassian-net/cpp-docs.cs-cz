---
title: mem_fun1_ref_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_ref_t
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
ms.openlocfilehash: 88ab2c436b3dd3b5a289124e73b6f1b5d21f96a5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243856"
---
# <a name="memfun1reft-class"></a>mem_fun1_ref_t – třída

Třída adaptéru umožňující `non_const` členskou funkci, která přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem reference. Zastaralé v C ++ 11, v C ++ 17 odebrané.

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

*_Pm*\
Ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

*doleva*\
Objekt, který *_Pm* členská funkce je volána v.

*doprava*\
Argument, který je právě přiřazen k *_Pm*.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelnou binární funkci.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá kopie *_Pm*, která musí být ukazatel na členskou funkci třídy `Type`, v objektu privátní člen. Definuje jeho členskou funkci `operator()` jako vracející (**levé**.\* `_Pm`) (**správné**).

## <a name="example"></a>Příklad

Konstruktor třídy `mem_fun1_ref_t` se obvykle nepoužívá přímo; pomocnou funkci `mem_fun_ref` slouží k přizpůsobení členské funkce. Zobrazit [mem_fun_ref –](../standard-library/functional-functions.md#mem_fun_ref) příklad, jak používat adaptéry členské funkce.
