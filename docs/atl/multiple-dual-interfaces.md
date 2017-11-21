---
title: "Duální rozhraní více | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multiple dual interfaces
- COM_INTERFACE_ENTRY2 macro
- dual interfaces, exposing multiple
- multiple dual interfaces, exposing with ATL
- IDispatchImpl class, multiple dual interfaces
- COM_INTERFACE_ENTRY_IID macro
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 426109958cf9b34829c23ac0bfd59743f1681e72
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="multiple-dual-interfaces"></a>Více duální rozhraní
Možná budete chtít kombinovat výhod duální rozhraní (to znamená, flexibilitu vtable a pozdní vazba, díky čemuž třídy, k dispozici skriptovací jazyky, jakož i C++) pomocí technik vícenásobná dědičnost.  
  
 Přestože je možné ke zveřejnění více duální rozhraní u jednoho objektu COM, se nedoporučuje. Pokud existuje více duální rozhraní, musí existovat jenom jeden `IDispatch` rozhraní vystavené. K dispozici zajistit, že se jedná o tento případ techniky provádění postihy například ztráty funkce nebo složitost vyšší kódu. Vývojář vzhledem k tomu tento přístup má pečlivě naváží výhody a nevýhody.  
  
## <a name="exposing-a-single-idispatch-interface"></a>Vystavení jednoho rozhraní IDispatch  
 Je možné ke zveřejnění více duální rozhraní na jediný objekt Odvozením ze dvou nebo více specializací `IDispatchImpl`. Ale pokud povolit klientům dotazovat na `IDispatch` rozhraní, budete muset použít [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) – makro (nebo [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid))) k určení, které základní třídu pro implementace `IDispatch`.  
  
 [!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]  
  
 Protože pouze jeden `IDispatch` rozhraní je vystavený, klienti, kteří přístup jenom k vašich objektů prostřednictvím `IDispatch` rozhraní nebudou mít přístup k metody nebo vlastnosti v jiných rozhraní.  
  
## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>Kombinace více duální rozhraní do jediná implementace typu IDispatch  
 ATL neposkytuje žádné podporu pro kombinace více duální rozhraní do jediná implementace typu `IDispatch`. Existuje však několik známé přístupy k ručně kombinování rozhraní, jako je například vytváření šablonované třídu, která obsahuje spojení samostatné `IDispatch` rozhraní, vytvoření nového objektu provést `QueryInterface` funkce nebo pomocí na základě TypeInfo – implementace vnořených objektů vytvořit `IDispatch` rozhraní.  
  
 Tyto přístupy máte problémy s potenciální kolize názvů, jakož i kód složitosti a udržovatelnosti. Není doporučeno, abyste vytvořili více duální rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Duální rozhraní a knihovny ATL](../atl/dual-interfaces-and-atl.md)

