---
title: Hstring::makereference – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs:
- C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 061b3be0e642bb8e7406f54a469723c70559d85a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610158"
---
# <a name="hstringmakereference-method"></a>HString::MakeReference – metoda

Vytvoří `HStringReference` objekt ze zadaného parametru řetězce.

## <a name="syntax"></a>Syntaxe

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>Parametry

*sizeDest*  
Parametr šablony, které určuje velikost cílové `HStringReference` vyrovnávací paměti.

*str*  
Odkaz na řetězec širokých znaků.

*Délka*  
Maximální délka *str* parametr vyrovnávací paměti pro použití v této operaci. Pokud *len* parametr není zadán, celý *str* parametr se používá.

## <a name="return-value"></a>Návratová hodnota

`HStringReference` Objekt, jehož hodnota je stejný jako zadaný *str* parametru.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HString – třída](../windows/hstring-class.md)