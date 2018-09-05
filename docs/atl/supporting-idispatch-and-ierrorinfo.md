---
title: Podpora IDispatch a IErrorInfo | Dokumentace Microsoftu
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
ms.openlocfilehash: 0d9c27dfe81c3bbd2978f418c8e942ac20190b30
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753605"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Podpora IDispatch a IErrorInfo

Můžete použít třídu šablony [třídou IDispatchImpl](../atl/reference/idispatchimpl-class.md) poskytnout výchozí implementaci třídy `IDispatch Interface` část jakékoli duální rozhraní na objekt.

Pokud váš objekt používá `IErrorInfo` rozhraní hlášení chyb zpátky do klienta a pak musí váš objekt podporovat `ISupportErrorInfo Interface` rozhraní. Třída šablony [isupporterrorinfoimpl –](../atl/reference/isupporterrorinfoimpl-class.md) poskytuje snadný způsob, jak toto implementovat, pokud máte pouze jedno rozhraní, který generuje chyby na objekt.

## <a name="see-also"></a>Viz také

[Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)

