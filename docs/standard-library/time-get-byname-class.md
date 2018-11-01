---
title: time_get_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get_byname
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
ms.openlocfilehash: e18f210dba03d66fa3a4ea111a6dfc61f0d0c12a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596466"
---
# <a name="timegetbyname-class"></a>time_get_byname – třída

Odvozená třída šablony popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí typu `time_get` \<CharType, InputIterator >.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class InputIterator =
    istreambuf_iterator<CharType, char_traits<CharType>>>
class time_get_byname : public time_get<CharType, InputIterator>
{
public:
    explicit time_get_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_get_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_get_byname()
};
```

### <a name="parameters"></a>Parametry

*_Locname*<br/>
S názvem národního prostředí.

*_Refs*<br/>
Počet počáteční odkazů.

## <a name="requirements"></a>Požadavky

Její chování je určeno s názvem národního prostředí *_Locname*. Každý konstruktor inicializuje jeho základní objekt s [time_get](../standard-library/time-get-class.md#time_get)\<CharType, InputIterator > ( `_Refs`).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
