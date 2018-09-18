---
title: Profilově řízené optimalizace na základě PG0165 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PG0165
dev_langs:
- C++
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 332751a123bf7d6414c40b79870b5edf27a3d8a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084208"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Chyba optimalizace na základě profilu PG0165

Čtení "Filename.pgd": "verze souboru PGD se nepodporuje (Neshoda verzí)".

Soubor PGD soubory jsou specifické pro sadu nástrojů konkrétního kompilátoru. Tato chyba se vygeneruje, když používáte jiný kompilátoru, než jaký se používá pro *Filename*.pgd. Tato chyba označuje, že tato sada nástrojů kompilátoru nelze použít data z *Filename*.pgd k optimalizaci aktuálním programem.

Chcete-li tento problém vyřešit, znovu vygenerovat *Filename*.pgd pomocí aktuální sady nástrojů kompilátoru.