---
title: 'vektor&lt;bool&gt;:: reference – třída | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- vector/vector<bool>::reference
dev_langs:
- C++
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 798c65764ce49e795d3a6220803d51c72411ca79
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686405"
---
# <a name="vectorltboolgtreference-class"></a>vektor&lt;bool&gt;:: reference – třída

`vector<bool>::reference` Třídy je třída proxy poskytnutá [vektoru\<bool > třída](../standard-library/vector-bool-class.md) pro simulaci `bool&`.

## <a name="remarks"></a>Poznámky

Simulovaný odkaz je vyžadován, protože jazyk C++ nativně neumožňuje přímé odkazy na bity. `vector<bool>` používá pouze jeden bit na element, který můžete odkazovat pomocí této třídy proxy serveru. Simulace odkazu však není kompletní, protože určitá přiřazení nejsou platná. Například protože adresu `vector<bool>::reference` nelze přijmout, následující kód, který se pokusí použít `vector<bool>::operator&` není správná:

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Převrátit na ose](../standard-library/vector-bool-reference-flip.md)|Přemění logickou hodnotu prvku vektoru.|
|[bool – operátor](../standard-library/vector-bool-reference-operator-bool.md)|Poskytuje implicitní převod z `vector<bool>::reference` k **bool**.|
|[operátor =](../standard-library/vector-bool-reference-operator-assign.md)|Přiřadí k bitu logickou hodnotu nebo hodnotu obsaženou referenčním prvkem.|

## <a name="requirements"></a>Požadavky

**Hlavička**: \<vektoru >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[\<vektor >](../standard-library/vector.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
