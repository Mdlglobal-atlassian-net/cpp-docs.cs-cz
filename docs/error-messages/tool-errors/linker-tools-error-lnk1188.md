---
title: "Chyba linkerů Lnk1188 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1188
dev_langs: C++
helpviewer_keywords: LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a77f769aed208c557b72e12572d170482d2538ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1188"></a>Chyba linkerů LNK1188
BADFIXUPSECTION:: cíl neplatná oprava 'symbol'; možné nula délku části  
  
 Cíl přemístění během VxD – odkaz, neměl oddíl. S LINK386 (starší verze), záznamu skupiny OMF (generované direktivu MASM skupiny) pravděpodobně byl použit kombinovat nulové délky oddíl s jinou část nulová délka. Formát COFF nepodporuje GROUP – direktiva a části nulové délky. Při propojení automaticky převede tento typ objektu OMF COFF, této chybě může dojít.