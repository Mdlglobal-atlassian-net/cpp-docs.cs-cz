---
title: hash_compare – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- hash_set/stdext::hash_compare
dev_langs:
- C++
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92dce97754eccc8cd4f618db3ac3e23574fb54ae
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956573"
---
# <a name="hashcompare-class"></a>hash_compare – třída

Třída šablony popisuje objekt, který můžete použít některou z hodnot hash asociativní kontejnery – hash_map – hash_multimap, hash_set, nebo hash_multiset – jako výchozí **osobnostní rysy** parametr objektu pořadí a hodnoty hash, který obsahují elementy .

## <a name="syntax"></a>Syntaxe

hash_compare – třída {osobnostní rysy comp; veřejného: const bucket_size – size_t = 4; const size_t min_buckets = 8; hash_compare() hash_compare – (před vlastností); size_t operator() (const Key & klíč) const; bool operator() (const Key & klíč1, const Key & key2) const;};

## <a name="remarks"></a>Poznámky

Každá hodnota hash asociativní kontejner ukládá objekt hash vlastností typu `Traits` (parametr šablony). Třídu lze odvodit z specializací hash_compare – pro selektivní přepsání některých funkce a objekty, nebo můžete zadat vlastní verzi této třídy, pokud jsou splněné určité minimální požadavky na. Konkrétně pro hash_comp objektu typu `hash_compare<Key, Traits>`, podle výše uvedených kontejnerů se vyžaduje následující chování:

- Pro všechny hodnoty `key` typu `Key`, volání **hash_comp**(`key`) slouží jako funkce hash, která získá distribuci hodnot typu `size_t`. Funkce poskytnuté hash_compare – vrátí `key`.

- Jakoukoli hodnotu `key1` typu `Key` , která předchází `key2` v pořadí a má stejnou hodnotu (hodnoty vrácené funkce hash), hodnoty hash **hash_comp**(`key2`, `key1`) má hodnotu false. Funkce musí uložit celkem řazení u hodnot typu `Key`. Funkce poskytnuté hash_compare – vrátí *kompozice*(`key2`, `key1`) `,` kde *kompozice* je uložený objekt typu `Traits` , můžete určit, kdy jste Vytvořte objekt hash_comp. Pro výchozí `Traits` typ parametru `less<Key>`, klíče řazení nikdy snížení hodnoty.

- Celočíselná konstanta `bucket_size` určuje střední počet prvků na "kbelík" (zatřiďovací tabulku položka), který se kontejner by měl která nepřekročí. Musí být větší než nula. Hodnota zadaná pomocí hash_compare – je 4.

- Celočíselná konstanta `min_buckets` Určuje minimální počet kbelíků udržovat v zatřiďovací tabulce. Musí být mocninou čísla 2 a větší než nula. Hodnota zadaná pomocí hash_compare – je 8.

## <a name="example"></a>Příklad

Viz příklady pro [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map), [hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap), [hash_set::hash_set](../standard-library/hash-set-class.md#hash_set), a [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset), příklady toho, jak deklarace a používání hash_compare –.

## <a name="requirements"></a>Požadavky

**Header:** \<hash_map>

**Namespace:** stdext

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
