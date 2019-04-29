---
title: messages_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_byname
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
ms.openlocfilehash: 7b341f3e1dbf76021911c70560b83932b5302191
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404790"
---
# <a name="messagesbyname-class"></a>messages_byname – třída

Odvozená třída šablony popisuje objekt, který může sloužit jako omezující vlastnost zprávy daného národního prostředí, který umožňuje načtení lokalizovaných zpráv.

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

*_Locname*<br/>
S názvem národního prostředí.

*_Refs*<br/>
Počet počáteční odkazů.

## <a name="remarks"></a>Poznámky

Její chování je určeno s názvem národního prostředí *_Locname*. Každý konstruktor inicializuje jeho základní objekt s [zprávy](../standard-library/messages-class.md#messages)\<CharType > ( `_Refs`).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
