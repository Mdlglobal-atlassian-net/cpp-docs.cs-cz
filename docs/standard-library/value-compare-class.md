---
title: value_compare – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9019b39ff9df7137a1de6723a6fbb64e595ce678
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="valuecompare-class"></a>value_compare – třída

Poskytuje objekt funkce, který můžete porovnat elementy hash_map srovnáním jejich klíčů určit jejich relativní pořadí v hash_map.

## <a name="syntax"></a>Syntaxe

```cpp
class value_compare
 : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
    const value_type& left,
    const value_type& right) const
 {
    return (comp(left.first, right.first));

}
protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```

## <a name="remarks"></a>Poznámky

Porovnání kritéria poskytované value_compare – mezi **value_types** celou elementů obsažených hash_map je vyvolané z porovnání mezi klíče příslušných elementů ve vytváření pomocná třída. Operátor členské funkce používá objekt **comp** typu `key_compare` uložené v objektu funkce poskytované value_compare – k porovnání klíč řazení součástí dva elementy.

Pro hash_sets a hash_multisets, které jsou jednoduché kontejnery, kde jsou identické s hodnotami element hodnoty klíče, je ekvivalentní value_compare – `key_compare`, hash_maps a hash_multimaps nejsou, protože hodnota typu `pair` elementy není identické s hodnotou klíče elementu.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) příklad toho, jak deklarace a používání value_compare –.

## <a name="requirements"></a>Požadavky

**Header:** \<hash_map>

**Namespace:** stdext –

## <a name="see-also"></a>Viz také

[binary_function – struktura](../standard-library/binary-function-struct.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
