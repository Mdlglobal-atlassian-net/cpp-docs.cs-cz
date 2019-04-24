---
title: Implementace CComObjectRootEx
ms.date: 11/04/2016
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
ms.openlocfilehash: 80ce9936546b936770d8dedd0ba55f8c05617d37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197468"
---
# <a name="implementing-ccomobjectrootex"></a>Implementace CComObjectRootEx

[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) je nezbytné; všechny objekty knihovny ATL musí mít jednu instanci `CComObjectRootEx` nebo [ccomobjectroot –](../atl/reference/ccomobjectroot-class.md) v jejich dědičnosti. `CComObjectRootEx` poskytuje výchozí hodnotu `QueryInterface` mechanismus podle položek mapování modelu COM.

Prostřednictvím jeho mapy modelu COM jsou vystaveny rozhraní objektu klientovi při klient se dotáže rozhraní. Dotaz se provádí prostřednictvím `CComObjectRootEx::InternalQueryInterface`. `InternalQueryInterface` zpracovává pouze v tabulce mapy modelu COM rozhraní.

Rozhraní můžete zadat do tabulky mapování modelu COM s [COM_INTERFACE_ENTRY](reference/com-interface-entry-macros.md#com_interface_entry) – makro nebo jeden z jeho variant. Například následující kód zadá rozhraní `IDispatch`, `IBeeper`, a `ISupportErrorInfo` do tabulky mapování modelu COM:

[!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]

## <a name="see-also"></a>Viz také:

[Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Makra map COM](../atl/reference/com-map-macros.md)
