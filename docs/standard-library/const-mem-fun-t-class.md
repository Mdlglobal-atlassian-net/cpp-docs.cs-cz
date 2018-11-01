---
title: const_mem_fun_t – třída
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::const_mem_fun_t
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
ms.openlocfilehash: 16169c094e74178f5a2dd67f70bf75c1f3ee8d87
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563589"
---
# <a name="constmemfunt-class"></a>const_mem_fun_t – třída

Třída adaptéru umožňující volat konstantní členskou funkci, která nepřijímá žádné argumenty, jako objekt jednočlenné funkce při inicializaci s argumentem reference.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type>
class const_mem_fun_t : public unary_function <Type *, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type* Pleft) const;
};
```

### <a name="parameters"></a>Parametry

*Odp.*<br/>
Ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

*Pleft*<br/>
Objekt, který *Pm* členská funkce je volána v.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelnou jednočlennou funkci.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá kopie *Pm*, která musí být ukazatel na členskou funkci třídy `Type`, v objektu privátní člen. Definuje jeho členskou funkci `operator()` jako vracející ( `Pleft` -> \* `Pm`) () **const**.

## <a name="example"></a>Příklad

Konstruktor třídy `const_mem_fun_t` se obvykle nepoužívá přímo; pomocnou funkci `mem_fun` slouží k přizpůsobení členské funkce. Zobrazit [mem_fun –](../standard-library/functional-functions.md#mem_fun) příklad, jak používat adaptéry členské funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
