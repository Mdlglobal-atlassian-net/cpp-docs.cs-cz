---
title: Podpora IDispatch a IErrorInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IErrorInfo
- IDispatch
dev_langs: C++
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6d34f0d0616ae3980d1132b1f70812fe273d275
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Podpora IDispatch a IErrorInfo
Můžete použít třídu šablony [IDispatchImpl](../atl/reference/idispatchimpl-class.md) zajistit výchozí implementaci třídy `IDispatch Interface` část žádné duální rozhraní v objektu.  
  
 Pokud používá objektu `IErrorInfo` rozhraní k hlášení chyb zpět do klienta a pak musí podporovat objektu `ISupportErrorInfo Interface` rozhraní. Šablony třídy [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) poskytuje snadný způsob, jak tuto funkci implementovat Pokud máte pouze jednu rozhraní, které generuje chyby v objektu.  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL COM – objekty](../atl/fundamentals-of-atl-com-objects.md)

