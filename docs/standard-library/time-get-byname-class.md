---
title: time_get_byname – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xloctime/std::time_get_byname
dev_langs:
- C++
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1c1e7c0992822f8f0a47011a873f99a17b2095d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854451"
---
# <a name="timegetbyname-class"></a>time_get_byname – třída

Třída odvozená šablony popisuje objekt, který může sloužit jako národní prostředí omezující vlastnost typu `time_get` \<CharType, InputIterator >.

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

`_Locname` S názvem národní prostředí.

`_Refs` Počet počáteční odkazů.

## <a name="requirements"></a>Požadavky

Její chování je dáno s názvem národní prostředí `_Locname`. Každý konstruktor inicializuje jeho základní objekt s [time_get](../standard-library/time-get-class.md#time_get)\<CharType, InputIterator > ( `_Refs`).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
