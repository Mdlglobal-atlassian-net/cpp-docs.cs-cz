---
title: Vytvoření agregovaného objektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f6ff5a0fdcff62d62469f17388f633b83739a09
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850823"
---
# <a name="creating-an-aggregated-object"></a>Vytvoření agregovaného objektu
Delegáti agregace `IUnknown` volání, poskytuje ukazatel na objekt vnější `IUnknown` na vnitřní objekt.  
  
### <a name="to-create-an-aggregated-object"></a>Vytvoření agregovaného objektu  
  
1.  Přidat `IUnknown` ukazatel na třídu objektu a inicializovat na hodnotu NULL v konstruktoru.  
  
2.  Přepsat [FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct) vytvoření agregace.  
  
3.  Použití `IUnknown` ukazatel definovaný v kroku 1, jako druhý parametr [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) makra.  
  
4.  Přepsat [FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease) uvolnit `IUnknown` ukazatele.  
  
> [!NOTE]
>  Pokud používáte a uvolnění rozhraní z agregovaného objektu během `FinalConstruct`, měli byste přidat [DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) – makro na definici třídy objektu.  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)

