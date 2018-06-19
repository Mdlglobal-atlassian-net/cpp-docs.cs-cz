---
title: Podpora IDispatch a IErrorInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IErrorInfo
- IDispatch
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94f4c99da3989cce84bd5b6bd3bbfee8df97ff43
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360946"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Podpora IDispatch a IErrorInfo
Můžete použít třídu šablony [IDispatchImpl](../atl/reference/idispatchimpl-class.md) zajistit výchozí implementaci třídy `IDispatch Interface` část žádné duální rozhraní v objektu.  
  
 Pokud používá objektu `IErrorInfo` rozhraní k hlášení chyb zpět do klienta a pak musí podporovat objektu `ISupportErrorInfo Interface` rozhraní. Šablony třídy [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) poskytuje snadný způsob, jak tuto funkci implementovat Pokud máte pouze jednu rozhraní, které generuje chyby v objektu.  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)

