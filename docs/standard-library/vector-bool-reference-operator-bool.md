---
title: 'vektor&lt;bool&gt;:: reference::operator bool | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
dev_langs:
- C++
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00ccd9e9ffbab78534c5b6417b7567ba03d007ab
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963677"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vektor&lt;bool&gt;:: reference::operator bool

Poskytuje implicitní převod z `vector<bool>::reference` k **bool**.

## <a name="syntax"></a>Syntaxe

```cpp
operator bool() const;
```

## <a name="return-value"></a>Návratová hodnota

Logická hodnota elementu [vektoru\<bool >](../standard-library/vector-bool-class.md) objektu.

## <a name="remarks"></a>Poznámky

`vector<bool>` Objektu nelze změnit tímto operátorem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vektoru >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[vektor\<bool >:: reference – třída](../standard-library/vector-bool-reference-class.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
