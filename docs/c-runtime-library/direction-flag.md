---
title: "Příznak směru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.flags
dev_langs: C++
helpviewer_keywords: direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0a43bac113c013ecb93f5b6e84aa2075a052f8c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="direction-flag"></a>Příznak směru
Příznak směru je příznak procesoru specifické pro procesory Intel 80 x 86. Platí pro všechny pokyny sestavení pomocí (opakování) předponu REP, jako je například MOVS, MOVSD, MOVSW a dalších. Adresy zadané na příslušné pokyny jsou zvýšena, pokud se vymaže příznak směru.  
  
 Běhové rutiny C předpokládá, že není zaškrtnuto příznak směru. Pokud používáte jiné funkce s funkcí jazyka C Runtime, musíte zajistit, dalších funkcí ponecháte příznak směru nebo obnovit do původního stavu. Byla očekávána příznak směru být zrušte při vstupu díky běhového kódu rychlejší a efektivnější.  
  
 Funkce knihovny C Run-Time, jako je například rutiny zacházení s řetězci a zacházení s vyrovnávací pamětí očekávat příznak směru být zrušte.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)