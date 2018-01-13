---
title: Implementace CComObjectRootEx | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CComObjectRootEx
dev_langs: C++
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ae8b8266aca2c9d6099455ddcb7618206dbe8c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-ccomobjectrootex"></a>Implementace CComObjectRootEx
[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) je nezbytné; všechny objekty knihovny ATL musí mít jednu instanci `CComObjectRootEx` nebo [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) v jejich dědičnosti. `CComObjectRootEx`poskytuje výchozí `QueryInterface` mechanismus podle položek mapování COM.  
  
 Prostřednictvím jeho mapu modelu COM se rozhraní objektu zveřejňují pro klienta, když se klient dotazuje rozhraní. Dotaz se provádí prostřednictvím `CComObjectRootEx::InternalQueryInterface`. `InternalQueryInterface`zpracovává jenom rozhraní v tabulce COM mapy.  
  
 Rozhraní můžete zadat do tabulky mapování COM s [COM_INTERFACE_ENTRY](reference/com-interface-entry-macros.md#com_interface_entry) makro nebo jednoho z jeho variant. Například následující kód zadá rozhraní `IDispatch`, `IBeeper`, a `ISupportErrorInfo` do tabulky mapování COM:  
  
 [!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL COM – objekty](../atl/fundamentals-of-atl-com-objects.md)   
 [Makra map COM](../atl/reference/com-map-macros.md)

