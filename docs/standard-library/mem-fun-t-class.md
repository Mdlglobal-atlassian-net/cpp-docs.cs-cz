---
title: mem_fun_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_t
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
ms.openlocfilehash: 19ccd4835c4257a7f409bcf0f7bda1a898567458
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245088"
---
# <a name="memfunt-class"></a>mem_fun_t – třída

Třída adaptéru umožňující `non_const` členskou funkci, která nepřijímá žádné argumenty, která se má volat jako objekt jednočlenné funkce při inicializaci s argumentem ukazatele. Zastaralé v C ++ 11, v C ++ 17 odebrané.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;
};
```

### <a name="parameters"></a>Parametry

*_Pm*\
Ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

*_Pleft*\
Objekt, který *_Pm* členská funkce je volána v.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelnou jednočlennou funkci.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá kopie *_Pm*, která musí být ukazatel na členskou funkci třídy `Type`, v objektu privátní člen. Definuje jeho členskou funkci `operator()` jako vracející (`_Pleft`->* `_Pm`) ().

## <a name="example"></a>Příklad

Konstruktor třídy `mem_fun_t` se obvykle nepoužívá přímo; pomocnou funkci `mem_fun` slouží k přizpůsobení členské funkce. Zobrazit [mem_fun –](../standard-library/functional-functions.md#mem_fun) příklad, jak používat adaptéry členské funkce.
