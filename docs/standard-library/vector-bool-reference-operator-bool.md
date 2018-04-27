---
title: 'vektor&lt;bool&gt;:: reference::operator bool | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89a027f9c31b9779991ebaee80b4e9d1a97d8ff7
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vektor&lt;bool&gt;:: reference::operator bool

Poskytuje implicitní převod z `vector<bool>::reference` k `bool`.

## <a name="syntax"></a>Syntaxe

```cpp
operator bool() const;
```

## <a name="return-value"></a>Návratová hodnota

Logická hodnota elementu [vektoru\<bool >](../standard-library/vector-bool-class.md) objektu.

## <a name="remarks"></a>Poznámky

`vector<bool>` Objektu nelze změnit pomocí tento operátor.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vektoru >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[vektor\<bool >:: odkazovat – třída](../standard-library/vector-bool-reference-class.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
