---
title: codecvt_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_byname
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
ms.openlocfilehash: b48f01126eba7082230fc5e19150d42d1dfad2f3
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688296"
---
# <a name="codecvt_byname-class"></a>codecvt_byname – třída

Šablona odvozené třídy popisující objekt, který může sloužit jako omezující vlastnost COLLATE daného národního prostředí a který umožňuje načtení informací specifických pro kulturní oblast týkající se převodů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Byte, class StateType>
class codecvt_byname: public codecvt<CharType, Byte, StateType> {
public:
    explicit codecvt_byname(
    const char* _Locname,
    size_t _Refs = 0);
```

```cpp
explicit codecvt_byname(
    const string& _Locname,
    size_t _Refs = 0);
```

```cpp
protected:
    virtual ~codecvt_byname();

};
```

### <a name="parameters"></a>Parametry

*_Locname* \
Pojmenované národní prostředí.

*_Refs* \
Počáteční počet odkazů

## <a name="remarks"></a>Poznámky

Charakteristiky byname se automaticky vytvoří při vytváření pojmenovaného národního prostředí.

Jeho chování je určeno názvem národního prostředí *_Locname*. Každý konstruktor inicializuje svůj základní objekt pomocí [codecvt](../standard-library/codecvt-class.md) \<CharType, Byte, StateType > (`_Refs`).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
