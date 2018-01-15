---
title: "hash_compare – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: hash_set/stdext::hash_compare
dev_langs: C++
helpviewer_keywords: hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 85450d9c41e4a0eedbf82a4b5113e3b8890998a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="hashcompare-class"></a>hash_compare – třída
Šablony třídy popisuje objekt, který můžete použít žádné kontejnery asociativní hash – hash_map, hash_multimap, hash_set, nebo hash_multiset – ve výchozím nastavení **vlastnosti** parametr objekt pořadí a hodnoty hash elementy obsahují .  
  
## <a name="syntax"></a>Syntaxe  
  
hash_compare – třída {vlastnosti comp; veřejný: const bucket_size – size_t – = 4; const min_buckets size_t – = 8, hash_compare(), hash_compare (vlastnosti před), size_t – Operator() – (const klíč & klíč) const; Operator() – bool (const klíč & key1, const klíč & key2) const;};  
  
## <a name="remarks"></a>Poznámky  
 Každý kontejner asociativní hash ukládá vlastnosti objektu hash typu **vlastnosti** (parametr šablony). Můžete odvození třídy z specializace hash_compare potřeby přepsat určité funkce a objekty, nebo můžete zadat vlastní verze této třídy, pokud splňovat určité požadavky na minimální. Konkrétně pro hash_comp k objektu typu **hash_compare\<klíče a vlastnosti >**, toto chování je požadované pro výše uvedené kontejnerů:  
  
-   Pro všechny hodnoty `key` typu **klíč**, volání **hash_comp**( `key`) slouží jako funkce hash, která vypočítá distribuci hodnot typu **size_t –**. Vrátí funkci poskytl hash_compare `key`.  
  
-   Pro jakoukoli hodnotu `key1` typu **klíč** který předchází `key2` v pořadí a má stejné hodnoty hash hodnotu (hodnoty vrácené funkce hash), **hash_comp**( `key2`, `key1`) je hodnota false. Funkce se musí použít celkem řazení hodnoty typu **klíč**. Vrátí funkce poskytl hash_compare *comp*( `key2`, `key1`) `,` kde *comp* je objekt uložené typu **vlastnosti** , můžete zadat při vytváření objektu hash_comp. Pro výchozí **vlastnosti** typ parametru **menší\<klíč >**, klíči řazení nikdy snížit v poli hodnota.  
  
-   Celočíselná konstanta **bucket_size –** určuje střední počet elementů za "sady" (hash-položka), kontejner se pokuste není překročit. Musí být větší než nula. Hodnota poskytnutá hash_compare je 4.  
  
-   Celočíselná konstanta **min_buckets** Určuje minimální počet kbelíků udržovat v zatřiďovací tabulce. Musí to být power dva a větší než nula. Hodnota poskytnutá hash_compare je 8.  
  
## <a name="example"></a>Příklad  
 Obsahuje příklady [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map), [hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap), [hash_set::hash_set](../standard-library/hash-set-class.md#hash_set), a [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset), příklady, jak deklarace a používání hash_compare.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<hash_map >  
  
 **Namespace:** stdext –  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



