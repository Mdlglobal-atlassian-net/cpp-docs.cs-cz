---
title: Chyba linkerů Lnk2017 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2017
dev_langs:
- C++
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 095423b5f2d86cef309ed4316ff72d195b11eb26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2017"></a>Chyba linkerů LNK2017
přemístění 'symbol' do 'segment"Neplatná bez /LARGEADDRESSAWARE:NO  
  
 Pokoušíte se vytvořit bitovou kopii 64-bit adresy 32-bit. Chcete-li to provést, postupujte takto:  
  
-   Použijte adresu pevné zatížení.  
  
-   Omezte bitovou kopii na 3 GB.  
  
-   Zadejte [/largeaddressaware:no](../../build/reference/largeaddressaware-handle-large-addresses.md).