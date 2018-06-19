---
title: CString sémantiku | Microsoft Docs
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
ms.openlocfilehash: b1765f1f7f4103b1b2cfe6012b42ebef12f8863f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356576"
---
# <a name="cstring-semantics"></a>CString sémantiku
I když [CString](../atl-mfc-shared/reference/cstringt-class.md) jsou dynamické objekty, které můžou růst, budou fungovat stejně jako jednoduchý třídy a vestavěné primitivní typy. Každý `CString` objekt představuje jedinečnou hodnotu. `CString` objekty by měl představit jako skutečný řetězce, nikoli jako ukazatele na řetězce.  
  
 Můžete přiřadit jednu **CString** objekt do jiné. Ale když upravíte jednu ze dvou `CString` objekty, dalších `CString` objektu se nemění, jak je znázorněno v následujícím příkladu:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]  
  
 Poznámka: v příkladu, dva `CString` objekty jsou považovány za "stejné", protože představují stejnou řetězcem znaků. `CString` Třída přetížení operátoru rovnosti (`==`) k porovnání dvou `CString` objektů na základě jejich hodnoty (obsah) namísto svou identitu (adresa).  
  
## <a name="see-also"></a>Viz také  
 [Řetězce (ATL a MFC)](../atl-mfc-shared/strings-atl-mfc.md)

