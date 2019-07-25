---
title: 'Vector&lt;bool&gt;:: Reference – třída'
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 65bfc91cf5dc79fb1e5151a6f62c394b4579883b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453215"
---
# <a name="vectorltboolgtreference-class"></a>Vector&lt;bool&gt;:: Reference – třída

Třída je proxy třída poskytovaná `bool&`vektorovou [\<bool > třídy](../standard-library/vector-bool-class.md) pro simulaci. `vector<bool>::reference`

## <a name="remarks"></a>Poznámky

Simulovaný odkaz je vyžadován, protože jazyk C++ nativně neumožňuje přímé odkazy na bity. `vector<bool>`používá pouze jeden bit na prvek, na který lze odkazovat pomocí této třídy proxy. Simulace odkazu však není kompletní, protože určitá přiřazení nejsou platná. Například vzhledem k tomu, že adresa `vector<bool>::reference` objektu nemůže být pořízena, následující kód, který se pokouší použít `vector<bool>::operator&` , není správný:

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[funkci](../standard-library/vector-bool-reference-flip.md)|Přemění logickou hodnotu prvku vektoru.|
|[operátor bool](../standard-library/vector-bool-reference-operator-bool.md)|Poskytuje implicitní převod z `vector<bool>::reference` na **bool**.|
|[operátor =](../standard-library/vector-bool-reference-operator-assign.md)|Přiřadí k bitu logickou hodnotu nebo hodnotu obsaženou referenčním prvkem.|

## <a name="requirements"></a>Požadavky

**Záhlaví**: \<vektorový >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<> vektoru](../standard-library/vector.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
