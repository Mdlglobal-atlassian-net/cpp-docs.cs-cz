---
title: ctype_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype_byname
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
ms.openlocfilehash: 0b0f33781cc9f1f54661a44a5434c94316432a45
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457896"
---
# <a name="ctypebyname-class"></a>ctype_byname – třída

Odvozená třída šablony popisuje objekt, který může sloužit jako omezující vlastnost CType daného národního prostředí, což umožňuje klasifikaci znaků a převod znaků mezi velikostmi písmen a nativním a národním prostředím zadanými znakové sady.

## <a name="syntax"></a>Syntaxe

```cpp
template <class _Elem>
class ctype_byname : public ctype<_Elem>
{
public:
    explicit ctype_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit ctype_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual __CLR_OR_THIS_CALL ~ctype_byname();

};
```

## <a name="remarks"></a>Poznámky

Jeho chování je určeno pojmenovaným národním `_Locname`prostředím. Každý konstruktor inicializuje svůj základní objekt pomocí [CType](../standard-library/ctype-class.md)\<CharType > ( `_Refs`) nebo ekvivalentu pro základní třídu `ctype<char>`.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
