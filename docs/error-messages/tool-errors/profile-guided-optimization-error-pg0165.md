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
ms.openlocfilehash: dbc85ad329a990ecdd7bc3a05f28d16a0c58c8e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="profile-guided-optimization-error-pg0165"></a>Chyba optimalizace na základě profilu PG0165
Čtení 'Filename.pgd': ' PGD verze není podporována (Neshoda verzí)'.  
  
 PGD soubory jsou specifické pro konkrétní kompilátoru nástrojů. Tato chyba se vygeneruje, když používáte jiný než ten, který používá pro kompilátor *Filename*.pgd. Tato chyba označuje, že tento sady nástrojů kompilátoru nelze použít data z *Filename*.pgd za účelem optimalizace aktuálním programem.  
  
 Chcete-li vyřešit tento problém, znovu vygenerovat *Filename*.pgd pomocí aktuální sady nástrojů kompilátoru.