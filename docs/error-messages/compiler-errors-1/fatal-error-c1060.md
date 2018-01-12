---
title: "Závažná chyba C1060 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1060
dev_langs: C++
helpviewer_keywords: C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c551ed3a6befbf646394929a6bcc6406ea93b19f
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="fatal-error-c1060"></a>Závažná chyba C1060
kompilátoru nemá dostatek místa na haldy  
  
 Operační systém nebo běhové knihovny nelze vyplnit žádost o paměti.  
  
### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Chcete-li vyřešit tuto chybu, zkuste to zvažte následující možná řešení  
  
1.  Pokud také vydává chyby kompilátoru [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) a [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), použijte [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) – možnost kompilátoru na nižší omezení přidělení paměti. Více místa na haldy je k dispozici do vaší aplikace, pokud můžete snížit zbývající přidělení paměti.  
  
     Pokud [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) možnost je již nastaven, zkuste ji odebrat. Protože je příliš vysoká. omezení přidělení paměti zadaný v možnosti, může dojít k vyčerpání haldy místa. Kompilátor používá výchozí limit, když odeberete [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) možnost.  
  
2.  Pokud jste se kompilování na 64bitové platformě, pomocí sady nástrojů kompilátoru 64-bit. Informace najdete v tématu [postupy: povolení 64bitová verze sady nástrojů Visual C++ v příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).  
  
3.  V systému Windows 32-bit, zkuste použít [3 GB](http://go.microsoft.com/fwlink/p/?linkid=177831) boot.ini přepínače.  
  
4.  Zvětšete velikost odkládacího souboru v systému Windows.  
  
5.  Ukončete ostatní spuštěné programy.  
  
6.  Odstraňte nepotřebné vkládané soubory.  
  
7.  Odstranění nepotřebných globální proměnné, například přidělením paměti dynamicky místo deklarace velké pole.  
  
8.  Odstraňte nepoužité deklarace.  
  
9. Aktuální soubor rozdělte na menší soubory.