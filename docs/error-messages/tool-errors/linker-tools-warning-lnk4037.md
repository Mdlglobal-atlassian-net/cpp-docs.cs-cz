---
title: Upozornění linkerů LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 9a8121617e622fc12efe5bd26aac23faf2530f24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410301"
---
# <a name="linker-tools-warning-lnk4037"></a>Upozornění linkerů LNK4037

>"*symbol*' neexistuje; ignoruje se.

Upravený název *symbol* nelze provést řazení podle pomocí [/ORDER](../../build/reference/order-put-functions-in-order.md) možnost, protože nebyl nalezen v programu. Zkontrolujte si specifikace *symbol* v souboru odpovědí pořadí. Další informace najdete v tématu [/Order (Put funkcí v pořadí)](../../build/reference/order-put-functions-in-order.md) – možnost linkeru.

> [!NOTE]
> ODKAZ nelze řadit statické funkce, protože názvy statickou funkci nejsou názvy veřejných symbolů. Když **/ORDER** je zadaný, vygeneruje se tento linker upozornění pro každý symbolů v souboru odpovědí pořadí, který je buď statický, nebo nebyl nalezen.