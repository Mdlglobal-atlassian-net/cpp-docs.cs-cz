---
title: Upozornění (úroveň 1) C4951 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e26c4bc176a54f063a3f9bce2faf451a9c0406f0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204232"
---
# <a name="compiler-warning-level-1-c4951"></a>Kompilátor upozornění (úroveň 1) C4951

> "*funkce*' byl upraven od shromáždění dat profilu data profilu funkce se nepoužijí

Funkci byl upraven v vstupu modulu do [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)tak, aby data profilu je nyní neplatný. Vstupní modul byl znovu zkompilovat po **/LTCG:PGINSTRUMENT** a má funkci (*funkce*) s odlišný tok řízení, než se v modulu v době **/LTCG:PGINSTRUMENT**  operace.

Toto upozornění je informační. Pokud chcete vyřešit toto upozornění, spusťte **/LTCG:PGINSTRUMENT**, znovu všech testů běží a spusťte **/LTCG:PGOPTIMIZE**.

Toto upozornění by měl být nahrazen chybu, pokud **/LTCG:PGOPTIMIZE** nepoužilo.