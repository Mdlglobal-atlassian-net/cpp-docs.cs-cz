---
title: LNK4037 upozornění Linkerů | Microsoft Docs
ms.custom: ''
ms.date: 10/04/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4037
dev_langs:
- C++
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b87f0a415d6ae7d282e29c2ca67fda043c2a901
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302432"
---
# <a name="linker-tools-warning-lnk4037"></a>Upozornění LNK4037 nástroje linkeru

>'*symbol*' neexistuje; ignorovat

Upravený název *symbol* nelze provést řazení podle pomocí [/pořadí](../../build/reference/order-put-functions-in-order.md) možnost, protože nebyl nalezen v programu. Zkontrolujte specifikaci *symbol* v souboru odpovědí, pořadí. Další informace najdete v tématu [/ORDER (Put funkcí v pořadí)](../../build/reference/order-put-functions-in-order.md) – možnost linkeru.

> [!NOTE]
> ODKAZ nelze pořadí statické funkce, protože nejsou statické funkce názvy názvy veřejných symbolů. Když **/pořadí** je zadán, tento linkeru upozornění se vygeneruje pro každý symbol v pořadí souboru odpovědí, který je buď nebo nebyl nalezen.