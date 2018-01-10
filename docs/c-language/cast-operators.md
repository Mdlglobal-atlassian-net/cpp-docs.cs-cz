---
title: "Operátory přetypování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c3f922bb052d6a69bc8a051769bc552b1f2653de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cast-operators"></a>Operátory přetypování
Přetypování poskytuje způsob explicitního převodu typu objektu v konkrétní situaci.  
  
## <a name="syntax"></a>Syntaxe  
 *výraz CAST*:  
 *Unární výraz*  
  
 **(***název typu***)***výraz cast*   
  
 Kompilátor zpracovává *výraz cast* jako typ *název typu* po přetypování. Přetypování lze použít k převodu objektů libovolného skalárního typu na jiný skalární typ a zpět. Přetypování typu explicitní jsou omezeny stejné pravidla, která určují důsledky implicitní převody, popsané v [převody přiřazení](../c-language/assignment-conversions.md). Při přetypování mohou být uplatněna další omezení vyplývající ze skutečných velikostí nebo reprezentací konkrétních typů. V tématu [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o skutečné velikosti integrální typy. Další informace o přetypování typu, najdete v části [převody přetypování](../c-language/type-cast-conversions.md).  
  
## <a name="see-also"></a>Viz také  
 [Operátor přetypování: ()](../cpp/cast-operator-parens.md)