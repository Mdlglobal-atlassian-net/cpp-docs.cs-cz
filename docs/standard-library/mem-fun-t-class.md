---
title: mem_fun_t – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_t
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
ms.openlocfilehash: cf1080f5f832bd79a347ee7fd847ff56a7567fdf
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006510"
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

*_Pm*<br/>
Ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

*_Pleft*<br/>
Objekt, který *_Pm* členská funkce je volána v.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelnou jednočlennou funkci.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá kopie *_Pm*, která musí být ukazatel na členskou funkci třídy `Type`, v objektu privátní člen. Definuje jeho členskou funkci `operator()` jako vracející ( `_Pleft` ->*  `_Pm`) ().

## <a name="example"></a>Příklad

Konstruktor třídy `mem_fun_t` se obvykle nepoužívá přímo; pomocnou funkci `mem_fun` slouží k přizpůsobení členské funkce. Zobrazit [mem_fun –](../standard-library/functional-functions.md#mem_fun) příklad, jak používat adaptéry členské funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[\<funkční >](../standard-library/functional.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
