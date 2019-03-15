---
title: Podpora IDispatch a IErrorInfo
ms.date: 11/04/2016
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
ms.openlocfilehash: 2dcebd215ff5e1bdf72323323dfbaebd16fa3403
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807413"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Podpora IDispatch a IErrorInfo

Můžete použít třídu šablony [třídou IDispatchImpl](../atl/reference/idispatchimpl-class.md) poskytnout výchozí implementaci třídy `IDispatch Interface` část jakékoli duální rozhraní na objekt.

Pokud váš objekt používá `IErrorInfo` rozhraní hlášení chyb zpátky do klienta a pak musí váš objekt podporovat `ISupportErrorInfo Interface` rozhraní. Třída šablony [isupporterrorinfoimpl –](../atl/reference/isupporterrorinfoimpl-class.md) poskytuje snadný způsob, jak toto implementovat, pokud máte pouze jedno rozhraní, který generuje chyby na objekt.

## <a name="see-also"></a>Viz také:

[Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)
