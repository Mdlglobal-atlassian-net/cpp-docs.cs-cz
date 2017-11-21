---
title: "Chyba linkerů Lnk2017 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2017
dev_langs: C++
helpviewer_keywords: LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f1b588abe7bb222751506e21d90b4b8596b381f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2017"></a>Chyba linkerů LNK2017
přemístění 'symbol' do 'segment"Neplatná bez /LARGEADDRESSAWARE:NO  
  
 Pokoušíte se vytvořit bitovou kopii 64-bit adresy 32-bit. Chcete-li to provést, postupujte takto:  
  
-   Použijte adresu pevné zatížení.  
  
-   Omezte bitovou kopii na 3 GB.  
  
-   Zadejte [/largeaddressaware:no](../../build/reference/largeaddressaware-handle-large-addresses.md).