---
title: Kompilátor upozornění (úroveň 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: 73e048aeaa044c35e09539b07d51398829a0fdfd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617856"
---
# <a name="compiler-warning-level-1-c4951"></a>Kompilátor upozornění (úroveň 1) C4951

> "*funkce*' byl upraven od shromáždění dat profilu data profilu funkce se nepoužijí

Funkci byl upraven v vstupu modulu do [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)tak, aby data profilu je nyní neplatný. Vstupní modul byl znovu zkompilovat po **/LTCG:PGINSTRUMENT** a má funkci (*funkce*) s odlišný tok řízení, než se v modulu v době **/LTCG:PGINSTRUMENT**  operace.

Toto upozornění je informační. Pokud chcete vyřešit toto upozornění, spusťte **/LTCG:PGINSTRUMENT**, znovu všech testů běží a spusťte **/LTCG:PGOPTIMIZE**.

Toto upozornění by měl být nahrazen chybu, pokud **/LTCG:PGOPTIMIZE** nepoužilo.