---
title: Převod dat nepodporovaných zprostředkovatelem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 79889125675a3e544802eb700718dee0829457c5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066120"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Převod dat nepodporovaných zprostředkovatelem

Pokud uživatel požádá o datový typ, který není podporována zprostředkovatelem, šablon zprostředkovatele OLE DB kódu pro `IRowsetImpl::GetData` Msdadc.dll k převedení datového typu.

Pokud se rozhodnete implementovat rozhraní jako `IRowsetChange` , který vyžaduje převod dat, můžete volat DLL knihovnu Msdaenum.dll k provedení převodu. Použití `GetData`, definované v Atldb.h jako příklad.

## <a name="see-also"></a>Viz také

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)