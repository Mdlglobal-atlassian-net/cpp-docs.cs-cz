---
title: Hstringreference::hstringreference – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6123f87abb9922a9736ac56f64d28e78887a0fdd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403568"
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference – konstruktor

Inicializuje novou instanci třídy **HStringReference** třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>Parametry

*sizeDest*<br/>
Parametr šablony, které určuje velikost cílové **HStringReference** vyrovnávací paměti.

*str*<br/>
Odkaz na řetězec širokých znaků.

*Délka*<br/>
Maximální délka *str* parametr vyrovnávací paměti pro použití v této operaci. Pokud *len* parametr není zadán, celý *str* parametr se používá. Pokud *len* je větší než *sizeDest*, *len* je nastavena na *sizeDest*-1.

*Ostatní*<br/>
Jiné **HStringReference** objektu.

## <a name="remarks"></a>Poznámky

První konstruktor inicializuje novou **HStringReference** objekt, který stejné velikosti jako parametr *str*.

Druhý konstruktor inicializuje novou **HStringReference** objekt, který specifeid velikost parametrem *len*.

Třetí konstruktor inicializuje novou **HStringReference** objektu na hodnotu *jiných* parametr a potom zničí *jiných* parametru.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HStringReference – třída](../windows/hstringreference-class.md)