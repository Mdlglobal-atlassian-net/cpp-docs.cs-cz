---
title: ctype_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype_byname
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
ms.openlocfilehash: dcaaff45fb33155710f788af4ceb657eff97464e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689736"
---
# <a name="ctype_byname-class"></a>ctype_byname – třída

Šablona odvozené třídy popisuje objekt, který může sloužit jako omezující vlastnost CType daného národního prostředí, což umožňuje klasifikaci znaků a převod znaků mezi písmeny a nativními a národními zadanými znakovými sadami.

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

Jeho chování je určeno názvem národního `_Locname`. Každý konstruktor inicializuje svůj základní objekt pomocí [ctype](../standard-library/ctype-class.md) \<CharType > (`_Refs`) nebo ekvivalentu `ctype<char>` základní třídy.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
