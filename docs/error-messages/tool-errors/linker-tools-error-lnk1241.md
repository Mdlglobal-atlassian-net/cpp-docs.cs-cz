---
title: "Chyba linkerů Lnk1241 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1241
dev_langs: C++
helpviewer_keywords: LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3fee22549e7b5c831aa378dc5caffb9da69bff88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1241"></a>Chyba linkerů LNK1241
soubor prostředků zdrojového souboru, který již zadán.  
  
 Tato chyba je generována, pokud spustíte **cvtres** ručně z příkazového řádku a pokud výsledný .obj pak předejte do souboru linkeru kromě na jiné soubory .res.  
  
 Pokud chcete zadat víc soubory .res, předat je do linkeru jako soubory .res není uvnitř soubory .obj vytvořené **cvtres**.