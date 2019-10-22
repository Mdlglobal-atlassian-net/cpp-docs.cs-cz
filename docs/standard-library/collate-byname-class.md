---
title: collate_byname – třída
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 3e9a256ac7bdb5f6d077746fe2a08990ed41e931
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688272"
---
# <a name="collate_byname-class"></a>collate_byname – třída

Šablona odvozené třídy popisující objekt, který může sloužit jako omezující vlastnost COLLATE daného národního prostředí a který umožňuje načtení informací specifických pro kulturní oblast týkající se konvencí řazení řetězců.

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

*_Locname* \
Pojmenované národní prostředí.

*_Refs* \
Počáteční počet odkazů

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který může sloužit jako [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class) typu [COLLATE](../standard-library/collate-class.md#collate) \<CharType >. Jeho chování je určeno [názvem](../standard-library/locale-class.md#name) národního prostředí *_Locname*. Každý konstruktor inicializuje svůj základní objekt s [kompletem collate](../standard-library/collate-class.md#collate) \<CharType > (`_Refs`).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
