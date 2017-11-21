---
title: "Upozornění linkerů Lnk4206 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4206
dev_langs: C++
helpviewer_keywords: LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1227cd792065198a3cd7f7a684e51e7c87452e77
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4206"></a>Upozornění linkerů LNK4206
informace o předkompilovaných typu nebyl nalezen. 'název souboru' není propojený nebo přepsat; propojování objektů, jako kdyby žádné informace o ladění  
  
 Soubor daného objektu, kompilovat s [/Yc](../../build/reference/yc-create-precompiled-header-file.md), nebyl zadaný v příkazu odkaz nebo byl přepsán.  
  
 Běžný scénář pro toto upozornění je po .obj, který byl kompilován s /Yc v knihovně, a tam, kde neexistují žádné symbol odkazy na tento .obj z vašeho kódu.  V takovém případě linkeru nebude používat (nebo i v tématu) souboru .obj.  V takovém případě by měl znovu zkompiluje kód a použít [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) pro zbývající objekty (objekty, které nejsou kompilovat s /Yc).