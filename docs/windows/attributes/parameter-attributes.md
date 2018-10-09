---
title: Atributy parametru (C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], parameter attributes
- parameter attributes
ms.assetid: 024c2dd5-49d7-4ced-a17a-c56c1bc485b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 160e71111a9080367390302a59c41a53580ffe0b
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789341"
---
# <a name="parameter-attributes"></a>Atributy parametru

Následující atributy se vztahují na parametry metody ve třídě nebo rozhraní.

|Atribut|Popis|
|---------------|-----------------|
|[Vlastní](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[defaultvalue](defaultvalue.md)|Umožňuje specifikace výchozí hodnotu pro zadaný nepovinný parametr.|
|[first_is](first-is.md)|Určuje index první prvek pole předávají.|
|[iid_is](iid-is.md)|Určuje index první prvek pole předávají.|
|[immediatebind](immediatebind.md)|Označuje, že databázi budou okamžitě oznamovat všechny změny vlastnosti objektu vázané na data.|
|[in](in-cpp.md)|Označuje, že je parametr předat z volající procedury do volané procedury.|
|[last_is](last-is.md)|Určuje index posledního prvku pole předávají.|
|[lcid](lcid.md)|Umožňuje předat funkci identifikátor národního prostředí.|
|[length_is](length-is.md)|Určuje počet elementů pole předávají.|
|[max_is](max-is.md)|Určuje maximální hodnotu pro pole platný index.|
|[Volitelné](optional-cpp.md)|Určuje volitelný parametr pro členské funkce.|
|[out](out-cpp.md)|Identifikuje parametry ukazatele, které se vracejí z volané procedury do volající procedury (ze serveru do klienta).|
|[rozsah](range-cpp.md)|Určuje rozsah povolených hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastavené v době běhu.|
|[ref](ref-cpp.md)|Určuje referenční ukazatel.|
|[retval](retval.md)|Označí parametr, který přijímá návratovou hodnotu člena.|
|[satype](satype.md)|Určuje datový typ `SAFEARRAY` struktury.|
|[size_is](size-is.md)|Určuje velikost paměti přidělené pro velikosti ukazatele, velikosti ukazatele na velikosti ukazatele a single - nebo vícedimenzionální pole.|
|[Jedinečný](unique-cpp.md)|Určuje jedinečný ukazatel.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](attributes-by-usage.md)