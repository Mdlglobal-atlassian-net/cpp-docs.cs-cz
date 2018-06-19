---
title: Implementace rozhraní Dual (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34cc55e4466dba094bf70e734340b40237207f3c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356729"
---
# <a name="implementing-a-dual-interface"></a>Implementace duální rozhraní
Můžete implementovat duální rozhraní pomocí [IDispatchImpl](../atl/reference/idispatchimpl-class.md) třídy, která poskytuje výchozí implementaci třídy `IDispatch` metody duální rozhraní. Další informace najdete v tématu [implementace rozhraní IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
 K použití této třídy:  
  
-   Duální rozhraní definujte v knihovny typů.  
  
-   Vlastní třídy odvozovat specializace z `IDispatchImpl` (předat informace o knihovně rozhraní a typ jako argumenty pro šablony).  
  
-   Přidejte položku (nebo položky) do mapy COM vystavení duální rozhraní prostřednictvím `QueryInterface`.  
  
-   Implementujte vtable součástí rozhraní v třídě.  
  
-   Zajistěte, aby byl typ knihovna, která obsahuje definice rozhraní k dispozici k objektům v době běhu.  
  
## <a name="atl-simple-object-wizard"></a>Průvodce jednoduchého objektu knihovny ATL  
 Pokud chcete vytvořit nové rozhraní a novou třídu pro implementaci, můžete použít [dialogové okno Přidat třídu ATL](../ide/add-class-dialog-box.md)a potom [ATL Simple Object Wizard](../atl/reference/atl-simple-object-wizard.md).  
  
## <a name="implement-interface-wizard"></a>Průvodce implementací rozhraní  
 Pokud máte existující rozhraní, můžete použít [Průvodce implementací rozhraní](../atl/reference/adding-a-new-interface-in-an-atl-project.md) přidání potřeby základní třídy, položek mapování COM a implementace kostru metoda do existující třídy.  
  
> [!NOTE]
>  Budete muset upravit vygenerované základní třídy tak, aby čísla hlavní verze a podverze knihovny typů jsou předat jako argumenty pro šablony pro vaše `IDispatchImpl` základní třídy. Průvodce implementací rozhraní není zkontrolujte číslo verze knihovny typu.  
  
## <a name="implementing-idispatch"></a>Implementace IDispatch  
 Můžete použít `IDispatchImpl` základní třída pro zadejte implementaci dispinterface právě zadáním na příslušnou položku v mapě COM (pomocí [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) nebo [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) makro), dokud máte knihovny typů popisující odpovídající duální rozhraní. Je celkem běžné implementovat `IDispatch` tímto způsobem, například rozhraní. Implementace rozhraní Průvodce obě předpokládá, že máte v úmyslu implementovat a ATL Simple Object Wizard `IDispatch` tímto způsobem, takže se přidá na příslušnou položku do mapy.  
  
> [!NOTE]
>  Nabízí ATL [IDispEventImpl](../atl/reference/idispeventimpl-class.md) a [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) třídy, která vám pomůže implementovat odesílající rozhraní bez nutnosti knihovny typů obsahující definice duální rozhraní, které je kompatibilní.  
  
## <a name="see-also"></a>Viz také  
 [Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)

