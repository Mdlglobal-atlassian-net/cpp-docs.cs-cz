---
title: "Závažná chyba C1905 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1905
dev_langs: C++
helpviewer_keywords: C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9d1662b05764500d0ac6a96119f865294cac260b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1905"></a>Závažná chyba C1905
Strana klientu a strana serveru nejsou kompatibilní (musí cílit na stejný procesor)  
  
 K této chybě dochází, když je soubor .obj generován kompilátorem na straně klientu (C1.dll), který cílí na jeden procesor, jako je například x86, ARM nebo [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ale je čten stranou serveru (C2.dll), která cílí na jiný procesor.  
  
 Chcete-li tento problém vyřešit, zkontrolujte, že používáte odpovídající front-end a back-end. Toto je výchozí nastavení pro projekty vytvořené v sadě Visual Studio. Této chybě může dojít, pokud máte upravit soubor projektu a použít různé cesty k nástrojům kompilátoru. Pokud jste nenastavili konkrétně cestu k nástrojům kompilátoru, této chybě může dojít instalace Visual Studia jsou poškozená. Například pravděpodobně jste zkopírovali soubory .dll kompilátoru z jednoho umístění do druhého. Použití **programy a funkce** v Ovládacích panelech opravy a nové instalace sady Visual Studio.