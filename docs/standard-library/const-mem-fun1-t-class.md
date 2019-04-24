---
title: const_mem_fun1_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: df984d90f8b632f8e3e3b183943343952d45b8be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62211972"
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

*member_ptr*<br/>
Ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

*doleva*<br/>
**Const** objekt, který *member_ptr* členská funkce je volána v.

*doprava*<br/>
Argument, který je právě přiřazen k *member_ptr*.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelnou binární funkci.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá kopie *member_ptr*, která musí být ukazatel na členskou funkci třídy `Type`, v objektu privátní člen. Definuje jeho členskou funkci `operator()` jako vracející `(left->member_ptr)(right) const`.

## <a name="example"></a>Příklad

Konstruktor třídy `const_mem_fun1_t` je zřídka se používá přímo. `mem_fn` slouží k přizpůsobení členské funkce. Zobrazit [mem_fn –](../standard-library/functional-functions.md#mem_fn) příklad, jak používat adaptéry členské funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
