---
title: messages_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_byname
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
ms.openlocfilehash: b8fe1ab2db792819831f5c50aa99a02559f71cdd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451810"
---
# <a name="messagesbyname-class"></a>messages_byname – třída

Odvozená třída šablony popisuje objekt, který může sloužit jako omezující vlastnost zprávy daného národního prostředí a který umožňuje načtení lokalizovaných zpráv.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class messages_byname : public messages<CharType> {
public:
    explicit messages_byname(
    const char *_Locname,
    size_t _Refs = 0);

    explicit messages_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~messages_byname();

};
```

### <a name="parameters"></a>Parametry

*_Locname*\
Pojmenované národní prostředí.

*_Refs*\
Počáteční počet odkazů

## <a name="remarks"></a>Poznámky

Jeho chování je určeno názvem národního prostředí *_Locname*. Každý konstruktor inicializuje svůj základní objekt se [zprávami](../standard-library/messages-class.md#messages)\<CharType > `_Refs`().

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
