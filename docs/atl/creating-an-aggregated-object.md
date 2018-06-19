---
title: Vytvoření agregovaného objektu | Microsoft Docs
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
ms.openlocfilehash: 35ddbd6b8db853967a70de0427cc842689d55c82
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355017"
---
# <a name="creating-an-aggregated-object"></a>Vytvoření agregovaného objektu
Delegáti agregace **IUnknown** volání, poskytuje ukazatel na vnější objekt **IUnknown** vnitřní objekt.  
  
### <a name="to-create-an-aggregated-object"></a>Pro vytvoření agregovaného objektu  
  
1.  Přidat **IUnknown** ukazatel do vaší třídy objektu a inicializujte ho, aby **NULL** v konstruktoru.  
  
2.  Přepsání [FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct) vytvoření agregace.  
  
3.  Použití **IUnknown** ukazatele, definovaný v kroku 1, jako druhý parametr pro [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) makra.  
  
4.  Přepsání [FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease) k uvolnění **IUnknown** ukazatel.  
  
> [!NOTE]
>  Pokud používáte a verzi rozhraní z agregovaného objektu během `FinalConstruct`, měli byste přidat [DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) makro k definici třídy objektu.  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)

