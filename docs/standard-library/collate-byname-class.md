---
title: collate_byname – třída
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 46eb139bafcf7368688f32cce37e38362c158c91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569598"
---
# <a name="collatebyname-class"></a>collate_byname – třída

Odvozená třída šablony popisující objekt, který může sloužit jako omezující vlastnost kolace daného národního prostředí a který umožňuje načtení informací specifických pro kulturní oblast v případě konvencí řazení řetězců.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```

### <a name="parameters"></a>Parametry

*_Locname*<br/>
S názvem národního prostředí.

*_Refs*<br/>
Počet počáteční odkazů.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který může sloužit jako [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class) typu [collate](../standard-library/collate-class.md#collate)\<CharType >. Je dáno jeho chování [s názvem](../standard-library/locale-class.md#name) národní prostředí *_Locname*. Každý konstruktor inicializuje jeho základní objekt s [collate](../standard-library/collate-class.md#collate)\<CharType > ( `_Refs`).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
