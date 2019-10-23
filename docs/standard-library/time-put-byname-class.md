---
title: time_put_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put_byname
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
ms.openlocfilehash: 4471c0df352a4d40d863ac36f0245cf8194f588c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685456"
---
# <a name="time_put_byname-class"></a>time_put_byname – třída

Šablona odvozené třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí typu `time_put` \< CharType, OutputIterator >.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```

### <a name="parameters"></a>Parametry

*_Locname* \
Název národního prostředí.

*_Refs* \
Počáteční počet odkazů

## <a name="remarks"></a>Poznámky

Jeho chování je určeno [názvem](../standard-library/locale-class.md#name) národního prostředí *_Locname*. Každý konstruktor inicializuje svůj základní objekt pomocí \<CharType [time_put](../standard-library/time-put-class.md#time_put) , OutputIterator > (`_Refs`).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
