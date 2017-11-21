---
title: "LNK4037 upozornění Linkerů | Microsoft Docs"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4037
dev_langs: C++
helpviewer_keywords: LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9ba06af937f15ff70e6de0aa36e394fef5815f0a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4037"></a>Upozornění LNK4037 nástroje linkeru

>'*symbol*' neexistuje; ignorovat

Upravený název *symbol* nelze provést řazení podle pomocí [/pořadí](../../build/reference/order-put-functions-in-order.md) možnost, protože nebyl nalezen v programu. Zkontrolujte specifikaci *symbol* v souboru odpovědí, pořadí. Další informace najdete v tématu [/ORDER (Put funkcí v pořadí)](../../build/reference/order-put-functions-in-order.md) – možnost linkeru.

> [!NOTE]
> ODKAZ nelze pořadí statické funkce, protože nejsou statické funkce názvy názvy veřejných symbolů. Když **/pořadí** je zadán, tento linkeru upozornění se vygeneruje pro každý symbol v pořadí souboru odpovědí, který je buď nebo nebyl nalezen.