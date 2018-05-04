---
title: Implementace CComObjectRootEx | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CComObjectRootEx
dev_langs:
- C++
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44c62e7589b9b300ceaa2886760bf2c3d85550ce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-ccomobjectrootex"></a>Implementace CComObjectRootEx
[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) je nezbytné; všechny objekty knihovny ATL musí mít jednu instanci `CComObjectRootEx` nebo [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) v jejich dědičnosti. `CComObjectRootEx` poskytuje výchozí `QueryInterface` mechanismus podle položek mapování COM.  
  
 Prostřednictvím jeho mapu modelu COM se rozhraní objektu zveřejňují pro klienta, když se klient dotazuje rozhraní. Dotaz se provádí prostřednictvím `CComObjectRootEx::InternalQueryInterface`. `InternalQueryInterface` Zpracovává jenom rozhraní v tabulce COM mapy.  
  
 Rozhraní můžete zadat do tabulky mapování COM s [COM_INTERFACE_ENTRY](reference/com-interface-entry-macros.md#com_interface_entry) makro nebo jednoho z jeho variant. Například následující kód zadá rozhraní `IDispatch`, `IBeeper`, a `ISupportErrorInfo` do tabulky mapování COM:  
  
 [!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL COM – objekty](../atl/fundamentals-of-atl-com-objects.md)   
 [Makra map COM](../atl/reference/com-map-macros.md)

