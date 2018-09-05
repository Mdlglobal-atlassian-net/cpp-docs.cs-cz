---
title: CString – sémantika | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 256c71cace15a3906ac048819ab2ffdef2071ff4
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761270"
---
# <a name="cstring-semantics"></a>CString – sémantika

I když [CString](../atl-mfc-shared/reference/cstringt-class.md) objekty jsou dynamické objekty, které můžou růst, působí jako jednoduchý třídy a vestavěnými primitivními typy. Každý `CString` objekt představuje jedinečnou hodnotu. `CString` objekty by měly představit jako skutečný řetězce, nikoli jako ukazatele na řetězce.

Můžete přiřadit jednu `CString` objektu na jiný. Ale při úpravě některého z nich `CString` objekty, druhé `CString` objekt není upraven, jak je znázorněno v následujícím příkladu:

[!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]

Poznámka: v příkladu, který dva `CString` objekty jsou považovány za "stejné", protože představují stejné řetězec znaků. `CString` Třídy přetížení operátoru rovnosti (`==`) pro porovnání dvou `CString` objektů podle jejich hodnoty (obsah) namísto svoji identitu (adresa).

## <a name="see-also"></a>Viz také

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

