---
title: Upozornění linkerů LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 43fae7d0f19f96998d2e1a1739bc3e596bbd9ea9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194197"
---
# <a name="linker-tools-warning-lnk4037"></a>Upozornění linkerů LNK4037

>*symbol ' symbol*' neexistuje; přeskočen

Upravený *symbol* názvu nelze seřadit pomocí možnosti [/Order](../../build/reference/order-put-functions-in-order.md) , protože nebyl nalezen v programu. Ověřte specifikaci *symbolu* v souboru odezvy objednávky. Další informace naleznete v tématu [/Order (Put Functions in order)](../../build/reference/order-put-functions-in-order.md) – možnost linkeru.

> [!NOTE]
> ODKAZ nemůže seřadit statické funkce, protože názvy statických funkcí nejsou názvy veřejných symbolů. Při zadání **/Order** se toto upozornění linkeru generuje pro každý symbol v souboru odezvy objednávky, který je buď statický, nebo nebyl nalezen.
