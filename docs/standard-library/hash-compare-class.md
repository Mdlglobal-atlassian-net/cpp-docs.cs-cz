---
title: hash_compare – třída
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_compare
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
ms.openlocfilehash: 399b412c41128f513cf01d1e034bad2bbc5ef79f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448810"
---
# <a name="hashcompare-class"></a>hash_compare – třída

Třída šablony popisuje objekt, který může být použit jakýmkoli z asociativních kontejnerů hash – hash_map, hash_multimap, hash_set nebo hash_multiset – **jako výchozí objekt** parametru pro řazení a hash prvků, které obsahují.

## <a name="syntax"></a>Syntaxe

hash_compare třídy {resize_ts; Public: const bucket_size = 4; const size_t min_buckets = 8; hash_compare (); hash_compare (vlastnosti před); size_t operátor () (const Key & Key) const; bool operator () (const Key & klíč1, const Key & key2) const;};

## <a name="remarks"></a>Poznámky

Každý asociativní kontejner hash ukládá objekt zatřiďovacích vlastností typu `Traits` (parametr šablony). Třídu můžete odvodit od specializace hash_compare pro selektivní přepsání určitých funkcí a objektů, nebo můžete předat vlastní verzi této třídy, pokud splňujete určité minimální požadavky. Konkrétně pro objekt hash_comp typu `hash_compare<Key, Traits>`je vyžadováno následující chování výše uvedenými kontejnery:

- Pro všechny hodnoty `key` typu `Key`volání **hash_comp**(`key`) slouží jako funkce hash, která poskytuje distribuci hodnot typu `size_t`. Funkce poskytnutá funkcí hash_compare vrací `key`.

- Pro libovolnou hodnotu `key1` typu `Key` , která předchází `key2` v sekvenci a má stejnou hodnotu hash (hodnota vrácená funkcí hash), **hash_comp**(`key2`, `key1`) je false. Funkce musí stanovit celkové řazení hodnot typu `Key`. Funkce poskytnutá funkcí hash_compare vrací *comp*(`key2`, `key1`) `,` , kde *comp* je uložený objekt typu `Traits` , který můžete zadat při vytváření objektu hash_comp. Pro výchozí `Traits` typ `less<Key>`parametru se klíče řazení nikdy nesnižují.

- Celočíselná konstanta `bucket_size` určuje průměrný počet prvků na hodnotu "interval" (hodnota hash-Table Entry), které by měl kontejner zkusit přesáhnout. Musí být větší než nula. Hodnota zadaná v hash_compare je 4.

- Celočíselná konstanta `min_buckets` určuje minimální počet intervalů, které se mají zachovat v zatřiďovací tabulce. Musí to být Mocnina dvou a větší než nula. Hodnota zadaná v hash_compare je 8.

## <a name="example"></a>Příklad

Příklady, jak deklarovat a používat hash_set, naleznete v tématu Příklady pro [hash_map:: hash_map](../standard-library/hash-map-class.md#hash_map), [hash_multimap:: hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap), [hash_set:: hash_multiset](../standard-library/hash-set-class.md#hash_set)a [hash_multiset:: hash_compare](../standard-library/hash-multiset-class.md#hash_multiset).

## <a name="requirements"></a>Požadavky

**Header:** \<hash_map>

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
