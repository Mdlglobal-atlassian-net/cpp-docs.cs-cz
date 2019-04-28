---
title: Chyba optimalizace na základě profilu PG0165
ms.date: 11/04/2016
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: f39bbe6540ebec10cd25c41ac2fe9f2acfca9b13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359732"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Chyba optimalizace na základě profilu PG0165

Čtení "Filename.pgd": "Verze souboru PGD se nepodporuje (Neshoda verzí)".

Soubor PGD soubory jsou specifické pro sadu nástrojů konkrétního kompilátoru. Tato chyba se vygeneruje, když používáte jiný kompilátoru, než jaký se používá pro *Filename*.pgd. Tato chyba označuje, že tato sada nástrojů kompilátoru nelze použít data z *Filename*.pgd k optimalizaci aktuálním programem.

Chcete-li tento problém vyřešit, znovu vygenerovat *Filename*.pgd pomocí aktuální sady nástrojů kompilátoru.