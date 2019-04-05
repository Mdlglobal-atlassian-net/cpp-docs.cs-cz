---
title: Převod dat nepodporovaných zprostředkovatelem
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e60f6cd4f7dca1ed3e176cabefc42f69946436a4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033836"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Převod dat nepodporovaných zprostředkovatelem

Pokud uživatel požádá o datový typ, který není podporována zprostředkovatelem, šablon zprostředkovatele OLE DB kódu pro `IRowsetImpl::GetData` Msdadc.dll k převedení datového typu.

Pokud se rozhodnete implementovat rozhraní jako `IRowsetChange` , který vyžaduje převod dat, můžete volat DLL knihovnu Msdaenum.dll k provedení převodu. Použití `GetData`, definované v Atldb.h jako příklad.

## <a name="see-also"></a>Viz také:

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)