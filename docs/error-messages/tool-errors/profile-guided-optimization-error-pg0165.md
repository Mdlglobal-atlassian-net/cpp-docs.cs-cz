---
title: Na základě profilu PG0165 chyba optimalizace | Microsoft Docs
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
ms.openlocfilehash: acad97411480112d06dadd454d1368dcfdf2c87f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318412"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Chyba optimalizace na základě profilu PG0165
Čtení 'Filename.pgd': ' PGD verze není podporována (Neshoda verzí)'.  
  
 PGD soubory jsou specifické pro konkrétní kompilátoru nástrojů. Tato chyba se vygeneruje, když používáte jiný než ten, který používá pro kompilátor *Filename*.pgd. Tato chyba označuje, že tento sady nástrojů kompilátoru nelze použít data z *Filename*.pgd za účelem optimalizace aktuálním programem.  
  
 Chcete-li vyřešit tento problém, znovu vygenerovat *Filename*.pgd pomocí aktuální sady nástrojů kompilátoru.