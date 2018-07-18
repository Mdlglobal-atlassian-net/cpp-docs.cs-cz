---
title: value_compare – třída (&lt;mapy&gt;) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46f8d00877aa4147e4b3e4ec2a6a23b70d8154c8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965845"
---
# <a name="valuecompare-class-ltmapgt"></a>value_compare – třída (&lt;mapy&gt;)

Poskytuje objekt funkce, který může porovnat prvky objektu map porovnáním hodnot jejich klíče pro určení jejich relativního pořadí v objektu map.

## <a name="syntax"></a>Syntaxe

```cpp
class value_compare : public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(const value_type& left, const value_type& right) const;
    value_compare(key_compare pred) : comp(pred);
protected:
    key_compare comp;
};
```

## <a name="remarks"></a>Poznámky

Kritérium porovnání poskytované `value_compare` mezi `value_types` celé elementů obsažených mapy je vyvolaných z porovnání mezi službou klíče příslušných elementů pomocí vytváření pomocná třída. Objekt používá operátor členské funkce `comp` typu `key_compare` uloženou v objektu funkce poskytované `value_compare` k porovnání dvou prvků komponenty klíč řazení.

Pro sady a multisets, které jsou jednoduché kontejnery, ve kterém jsou shodné s hodnoty prvků hodnoty klíče, `value_compare` je ekvivalentní `key_compare`; pro mapy a multimaps nejsou, jako hodnotu typu `pair` prvky není stejný jako hodnotu klíče prvku.

## <a name="example"></a>Příklad

Viz příklad pro [value_comp –](../standard-library/map-class.md#value_comp) příklad toho, jak deklarace a používání `value_compare`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<mapy >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[binary_function – struktura](../standard-library/binary-function-struct.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
