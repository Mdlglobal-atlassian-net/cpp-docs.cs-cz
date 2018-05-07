---
title: Chyba linkerů Lnk1188 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1188
dev_langs:
- C++
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e31943ae253a332576fba73102db410b103a0096
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1188"></a>Chyba linkerů LNK1188
BADFIXUPSECTION:: cíl neplatná oprava 'symbol'; možné nula délku části  
  
 Cíl přemístění během VxD – odkaz, neměl oddíl. S LINK386 (starší verze), záznamu skupiny OMF (generované direktivu MASM skupiny) pravděpodobně byl použit kombinovat nulové délky oddíl s jinou část nulová délka. Formát COFF nepodporuje GROUP – direktiva a části nulové délky. Při propojení automaticky převede tento typ objektu OMF COFF, této chybě může dojít.