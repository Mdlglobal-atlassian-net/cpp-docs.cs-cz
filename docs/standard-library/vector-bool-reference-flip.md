---
title: 'vektor&lt;bool&gt;:: Reference::Flip – | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vector/std::vector<bool>::reference::flip
dev_langs:
- C++
helpviewer_keywords:
- reference::flip method
ms.assetid: ef940365-cbe4-4a87-a3e2-1f3cfa357e29
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f100117cf67f049d31d226a4a42c37bd6812773e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="vectorltboolgtreferenceflip"></a>vektor&lt;bool&gt;:: Reference::Flip –

Invertuje výběr logická hodnota odkazovaný [vektoru\<bool >](../standard-library/vector-bool-class.md) element.

## <a name="syntax"></a>Syntaxe

```cpp
void flip();
```

## <a name="example"></a>Příklad

```cpp
// vector_bool_ref_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    cout << "The vector is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vector<bool>::reference vbref = vb.front();
    vbref.flip();

    cout << "The vector with first element flipped is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}

```

## <a name="output"></a>Výstup

```Output
The vector is:
    true false false true true
The vector with first element flipped is:
    false false false true true
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vektoru >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[vektor\<bool >:: odkazovat – třída](../standard-library/vector-bool-reference-class.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
