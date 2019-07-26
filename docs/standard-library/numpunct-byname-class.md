---
title: numpunct_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct_byname
helpviewer_keywords:
- numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
ms.openlocfilehash: 0c9eb565c2dbf54da449411aa11a4c5661debf1d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452322"
---
# <a name="numpunctbyname-class"></a>numpunct_byname – třída

Odvozená třída šablony popisuje objekt, který může sloužit jako `numpunct` omezující vlastnost daného národního prostředí a který umožňuje formátování a interpunkci číselných a logických výrazů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class numpunct_byname : public numpunct<Elem> {
public:
    explicit numpunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit numpunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~numpunct_byname();

};
```

## <a name="remarks"></a>Poznámky

Jeho chování je určeno pojmenovaným národním prostředím. [](../standard-library/locale-class.md#name) `_Locname` Konstruktor inicializuje svůj základní objekt pomocí [numpunct](../standard-library/numpunct-class.md#numpunct)\<CharType > ( `_Refs`).

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
