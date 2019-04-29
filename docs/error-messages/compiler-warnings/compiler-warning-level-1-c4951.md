---
title: Kompilátor upozornění (úroveň 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: 73e048aeaa044c35e09539b07d51398829a0fdfd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408053"
---
# <a name="compiler-warning-level-1-c4951"></a>Kompilátor upozornění (úroveň 1) C4951

> "*funkce*' byl upraven od shromáždění dat profilu data profilu funkce se nepoužijí

Funkci byl upraven v vstupu modulu do [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)tak, aby data profilu je nyní neplatný. Vstupní modul byl znovu zkompilovat po **/LTCG:PGINSTRUMENT** a má funkci (*funkce*) s odlišný tok řízení, než se v modulu v době **/LTCG:PGINSTRUMENT**  operace.

Toto upozornění je informační. Pokud chcete vyřešit toto upozornění, spusťte **/LTCG:PGINSTRUMENT**, znovu všech testů běží a spusťte **/LTCG:PGOPTIMIZE**.

Toto upozornění by měl být nahrazen chybu, pokud **/LTCG:PGOPTIMIZE** nepoužilo.