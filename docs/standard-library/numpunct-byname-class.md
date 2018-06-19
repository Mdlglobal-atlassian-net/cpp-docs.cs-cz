---
title: numpunct_byname – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocnum/std::numpunct_byname
dev_langs:
- C++
helpviewer_keywords:
- numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 511547b8a02a956a2ed7eff2da384f3adcfbd5ed
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912794"
---
# <a name="numpunctbyname-class"></a>numpunct_byname – třída

Objekt, který může sloužit jako popisuje třídy odvozené šablony `numpunct` omezující vlastnosti daného národního prostředí povolení formátování a interpunkce číselná nebo logická výrazů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class numpunct_byname : public numpunct<Elem> {
public:
    explicit numpunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit numpunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~numpunct_byname();

};
```

## <a name="remarks"></a>Poznámky

Je dáno jeho chování [s názvem](../standard-library/locale-class.md#name) národního prostředí `_Locname`. Konstruktor inicializuje jeho základní objekt s [numpunct](../standard-library/numpunct-class.md#numpunct)\<CharType > ( `_Refs`).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
