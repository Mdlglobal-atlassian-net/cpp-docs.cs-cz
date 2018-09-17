---
title: const_mem_fun1_t – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun1_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d42bc03e9fcb16ba8c0832a10ee96b361c525523
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699970"
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t – třída

Třída adaptéru umožňující **const** členskou funkci, která přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem ukazatele.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* _Pm)(Arg) const);
    Result operator()(const Type* _Pleft, Arg right) const;
};
```

### <a name="parameters"></a>Parametry

*_Pm*<br/>
Ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

*_Pleft*<br/>
**Const** objekt, který *_Pm* členská funkce je volána v.

*doprava*<br/>
Argument, který je právě přiřazen k *_Pm*.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelnou binární funkci.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá kopie *_Pm*, která musí být ukazatel na členskou funkci třídy `Type`, v objektu privátní člen. Definuje jeho členskou funkci `operator()` jako vracející ( *_Pleft*->\*<em>Pm</em>) ( *správné* ) **const**.

## <a name="example"></a>Příklad

Konstruktor třídy `const_mem_fun1_t` se obvykle nepoužívá přímo; pomocnou funkci `mem_fun` slouží k přizpůsobení členské funkce. Zobrazit [mem_fun –](../standard-library/functional-functions.md#mem_fun) příklad, jak používat adaptéry členské funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
