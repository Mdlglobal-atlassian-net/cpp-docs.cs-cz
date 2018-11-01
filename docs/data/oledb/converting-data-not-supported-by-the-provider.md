---
title: Převod dat nepodporovaných zprostředkovatelem
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: a53781f71a55dfb07dc996e5e25644d9337e4c63
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473435"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Převod dat nepodporovaných zprostředkovatelem

Pokud uživatel požádá o datový typ, který není podporována zprostředkovatelem, šablon zprostředkovatele OLE DB kódu pro `IRowsetImpl::GetData` Msdadc.dll k převedení datového typu.

Pokud se rozhodnete implementovat rozhraní jako `IRowsetChange` , který vyžaduje převod dat, můžete volat DLL knihovnu Msdaenum.dll k provedení převodu. Použití `GetData`, definované v Atldb.h jako příklad.

## <a name="see-also"></a>Viz také

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)