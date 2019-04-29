---
title: ctype_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype_byname
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
ms.openlocfilehash: d998747045ece765269ddb013b525b8c06fcdf8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394166"
---
# <a name="ctypebyname-class"></a>ctype_byname – třída

Odvozená třída šablony popisuje objekt, který může sloužit jako omezující vlastnost ctype daného národního prostředí, který umožňuje klasifikaci znaků a převod znaků mezi případ a nativní a znakovými sadami určenými pro národní prostředí.

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

Její chování je určeno s názvem národního prostředí `_Locname`. Každý konstruktor inicializuje jeho základní objekt s [ctype](../standard-library/ctype-class.md)\<CharType > ( `_Refs`) nebo jeho ekvivalent pro základní třídu `ctype<char>`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
