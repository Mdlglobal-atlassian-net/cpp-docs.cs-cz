---
title: Převod dat nepodporovaných zprostředkovatelem
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: 44cdde2bad24d21adbc728c90ecd173717c02b04
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265188"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Převod dat nepodporovaných zprostředkovatelem

Pokud uživatel požádá o datový typ, který není podporována zprostředkovatelem, šablon zprostředkovatele OLE DB kódu pro `IRowsetImpl::GetData` Msdadc.dll k převedení datového typu.

Pokud se rozhodnete implementovat rozhraní jako `IRowsetChange` , který vyžaduje převod dat, můžete volat DLL knihovnu Msdaenum.dll k provedení převodu. Použití `GetData`, definované v Atldb.h jako příklad.

## <a name="see-also"></a>Viz také

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)