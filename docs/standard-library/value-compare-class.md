---
title: value_compare – třída
ms.date: 11/04/2016
f1_keywords:
- value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: 4b7fff1bef091a9d47e6ea4dc0e53e86ce39ad7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627432"
---
# <a name="valuecompare-class"></a>value_compare – třída

Poskytuje objekt funkce, který může porovnat elementy hash_map porovnáním hodnot jejich klíče pro určení jejich relativního pořadí v hash_map –.

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

Porovnání kritérií poskytované value_compare – mezi `value_types` celé elementů obsažených hash_map je vyvolaných z porovnání mezi službou klíče příslušných elementů pomocí vytváření pomocná třída. Objekt používá operátor členské funkce `comp` typu `key_compare` uloženou v objektu funkce poskytované value_compare – pro porovnání dvou prvků komponenty klíč řazení.

Pro hash_sets a hash_multisets, které jsou jednoduché kontejnery, ve kterém jsou shodné s hodnoty prvků hodnoty klíče, je ekvivalentní value_compare – `key_compare`; pro hash_maps a hash_multimaps nejsou, protože hodnota typu `pair` prvky není stejný jako hodnotu klíče prvku.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) příklad toho, jak deklarace a používání value_compare –.

## <a name="requirements"></a>Požadavky

**Header:** \<hash_map>

**Namespace:** stdext

## <a name="see-also"></a>Viz také:

[binary_function – struktura](../standard-library/binary-function-struct.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
