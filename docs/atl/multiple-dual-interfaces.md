---
title: Více duálních rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- multiple dual interfaces
- COM_INTERFACE_ENTRY2 macro
- dual interfaces, exposing multiple
- multiple dual interfaces, exposing with ATL
- IDispatchImpl class, multiple dual interfaces
- COM_INTERFACE_ENTRY_IID macro
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80bc2d4cc112c87c5c7a4e7d30f680631c1a1506
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758284"
---
# <a name="multiple-dual-interfaces"></a>Více duálních rozhraní

Možná budete chtít kombinovat výhody duální rozhraní (to znamená, flexibilitu vtable a pozdní vazba, díky čemuž třídu, k dispozici skriptovací jazyky, jakož i jazyka C++) s technikami vícenásobnou dědičnost.

I když je možné ke zveřejnění více duálních rozhraní na jeden objekt modelu COM, se nedoporučuje. Pokud existuje více duálních rozhraní, musí obsahovat pouze jeden `IDispatch` rozhraní vystavené. Techniky, které jsou k dispozici pro zajištění, že se jedná o tento případ provádět sankce, jako je například výpadek funkce nebo kód zvýšení složitosti. Pro vývojáře, vzhledem k tomu tento přístup pečlivě zvážit, jaké výhody a nevýhody.

## <a name="exposing-a-single-idispatch-interface"></a>Vystavení jednotné rozhraní IDispatch

Je možné zveřejnit více duálních rozhraní na jeden objekt odvozené ze dvou nebo více specializace `IDispatchImpl`. Však-li povolit klientům dotazovat na `IDispatch` rozhraní, budete muset použít [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) – makro (nebo [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid))) k určení, které základní třídy pro provádění `IDispatch`.

[!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]

Protože pouze jeden `IDispatch` rozhraní je přístupný, klienti, kteří přístup pouze objekty prostřednictvím `IDispatch` rozhraní nebude mít přístup k metody nebo vlastnosti v jiných rozhraní.

## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>Spojování více duálních rozhraní do jedné implementace rozhraní IDispatch

ATL neposkytuje žádné podporu pro sloučení více duálních rozhraní do jediná implementace typu `IDispatch`. Existují však několik známých přístupů se ručně sloučením rozhraní, jako je například vytvoření třídy bez vizuálního vzhledu, který obsahuje spojení jako samostatná `IDispatch` rozhraní, vytváří se nový objekt pro provedení `QueryInterface` funkce nebo pomocí provádění TypeInfo vnořené objekty vytvořit `IDispatch` rozhraní.

Tyto přístupy máte problémy s potenciální kolize názvů, jakož i kód složitosti a udržovatelnosti. Nedoporučuje se, že vytvoříte více duálních rozhraní.

## <a name="see-also"></a>Viz také

[Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)

