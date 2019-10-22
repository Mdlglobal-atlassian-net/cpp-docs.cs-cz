---
title: time_get_byname – třída
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get_byname
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
ms.openlocfilehash: 9df3831e085f1dea1df45ff9368479fa516b944e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685760"
---
# <a name="time_get_byname-class"></a>time_get_byname – třída

Šablona odvozené třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí typu `time_get` \<CharType InputIterator >.

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

*_Locname* \
Pojmenované národní prostředí.

*_Refs* \
Počáteční počet odkazů

## <a name="requirements"></a>Požadavky

Jeho chování je určeno názvem národního prostředí *_Locname*. Každý konstruktor inicializuje svůj základní objekt pomocí \<CharType [time_get](../standard-library/time-get-class.md#time_get) , InputIterator > (`_Refs`).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
