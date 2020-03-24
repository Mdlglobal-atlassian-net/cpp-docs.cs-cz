---
title: Upozornění kompilátoru (úroveň 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: d94347df17bac01334cfd85c2bd9f6c8a98b5fc0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174593"
---
# <a name="compiler-warning-level-1-c4951"></a>Upozornění kompilátoru (úroveň 1) C4951

> '*Function*' se od shromáždění dat profilu upravovala; data profilu funkce se nepoužijí.

Funkce se upravovala ve vstupním modulu do [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), takže data profilu teď nejsou platná. Vstupní modul byl znovu zkompilován po **/LTCG: PGINSTRUMENT** a má funkci (*Function*) s jiným tokem řízení než byl v modulu v čase operace **/LTCG: PGINSTRUMENT** .

Toto upozornění je informativní. Chcete-li vyřešit toto upozornění, spusťte **/LTCG: PGINSTRUMENT**, znovu spusťte všechny testovací běhy a spusťte **/LTCG: PGOPTIMIZE**.

Toto upozornění by bylo nahrazeno chybou, pokud byla použita **/LTCG: PGOPTIMIZE** .
