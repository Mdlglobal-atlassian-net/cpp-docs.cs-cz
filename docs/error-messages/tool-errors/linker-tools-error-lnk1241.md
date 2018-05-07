---
title: Chyba linkerů Lnk1241 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1241
dev_langs:
- C++
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b02b1d9d06706c70478d958dd3c2af8dbc9c2c03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1241"></a>Chyba linkerů LNK1241
soubor prostředků zdrojového souboru, který již zadán.  
  
 Tato chyba je generována, pokud spustíte **cvtres** ručně z příkazového řádku a pokud výsledný .obj pak předejte do souboru linkeru kromě na jiné soubory .res.  
  
 Pokud chcete zadat víc soubory .res, předat je do linkeru jako soubory .res není uvnitř soubory .obj vytvořené **cvtres**.