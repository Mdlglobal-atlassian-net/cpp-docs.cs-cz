---
title: moneypunct_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct_byname
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
ms.openlocfilehash: c687bc870e4d78cfe9174eb04ea09c34d6a9c955
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687660"
---
# <a name="moneypunct_byname-class"></a>moneypunct_byname – třída

Odvozená šablona třídy, která popisuje objekt, který může sloužit jako omezující vlastnost `moneypunct` daného národního prostředí, umožňující formátování peněžních vstupních polí nebo peněžních výstupních polí.

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

Jeho chování je určeno názvem národního `_Locname`. Každý konstruktor inicializuje svůj základní objekt pomocí [moneypunct](../standard-library/moneypunct-class.md#moneypunct) \<CharType, mezinárodní > (`_Refs`).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
