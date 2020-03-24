---
title: Převod dat nepodporovaných zprostředkovatelem
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e87aebc4d6f23343af9a2f966d2c522e95b304ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211494"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Převod dat nepodporovaných zprostředkovatelem

Když spotřebitel požaduje datový typ, který není podporován poskytovatelem, kód šablony poskytovatele OLE DB pro `IRowsetImpl::GetData` zavolá Msdadc. dll pro převod datového typu.

Pokud implementujete rozhraní jako `IRowsetChange`, které vyžaduje převod dat, můžete volat Msdaenum. dll k provedení převodu. Jako příklad použijte `GetData`definované v Atldb. h.

## <a name="see-also"></a>Viz také

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
