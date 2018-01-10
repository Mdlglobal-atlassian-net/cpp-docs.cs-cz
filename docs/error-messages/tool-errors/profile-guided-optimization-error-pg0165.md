---
title: "Na základě profilu PG0165 chyba optimalizace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PG0165
dev_langs: C++
helpviewer_keywords: PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 32b9f5f3ee335aac0a8382377aa850c3b91a27a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="profile-guided-optimization-error-pg0165"></a>Chyba optimalizace na základě profilu PG0165
Čtení 'Filename.pgd': ' PGD verze není podporována (Neshoda verzí)'.  
  
 PGD soubory jsou specifické pro konkrétní kompilátoru nástrojů. Tato chyba se vygeneruje, když používáte jiný než ten, který používá pro kompilátor *Filename*.pgd. Tato chyba označuje, že tento sady nástrojů kompilátoru nelze použít data z *Filename*.pgd za účelem optimalizace aktuálním programem.  
  
 Chcete-li vyřešit tento problém, znovu vygenerovat *Filename*.pgd pomocí aktuální sady nástrojů kompilátoru.