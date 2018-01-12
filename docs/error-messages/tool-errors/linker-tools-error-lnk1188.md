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
ms.workload: cplusplus
ms.openlocfilehash: 81d2988742eb9e8cd6aef134510ac8272d3dd27c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1188"></a>Chyba linkerů LNK1188
BADFIXUPSECTION:: cíl neplatná oprava 'symbol'; možné nula délku části  
  
 Cíl přemístění během VxD – odkaz, neměl oddíl. S LINK386 (starší verze), záznamu skupiny OMF (generované direktivu MASM skupiny) pravděpodobně byl použit kombinovat nulové délky oddíl s jinou část nulová délka. Formát COFF nepodporuje GROUP – direktiva a části nulové délky. Při propojení automaticky převede tento typ objektu OMF COFF, této chybě může dojít.