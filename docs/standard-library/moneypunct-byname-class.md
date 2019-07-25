---
title: moneypunct_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct_byname
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
ms.openlocfilehash: 47c9d2281973cb57288bfdcf865926fb6dd9ed0e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460210"
---
# <a name="moneypunctbyname-class"></a>moneypunct_byname – třída

Odvozená třída šablony popisující objekt, který může sloužit jako `moneypunct` omezující vlastnost daného národního prostředí a který povoluje formátování peněžních vstupních polí nebo peněžních výstupních polí.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, bool Intl = false>
class moneypunct_byname : public moneypunct<CharType, Intl>
{
public:
    explicit moneypunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit moneypunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~moneypunct_byname();

};
```

## <a name="remarks"></a>Poznámky

Jeho chování je určeno pojmenovaným národním `_Locname`prostředím. Každý konstruktor inicializuje svůj základní objekt pomocí [moneypunct](../standard-library/moneypunct-class.md#moneypunct)\<CharType, Intl > ( `_Refs`).

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
