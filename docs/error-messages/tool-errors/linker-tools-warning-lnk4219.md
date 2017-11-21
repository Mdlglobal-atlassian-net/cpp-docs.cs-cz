---
title: "Upozornění linkerů Lnk4219 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4219
dev_langs: C++
helpviewer_keywords: LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c2416e8872998f9cb59efee21d33bbe60dd96d37
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4219"></a>Upozornění linkerů LNK4219
Oprava název oprava přetečení. Cíl "název cílové symbol" je mimo rozsah, vkládání převodu  
  
 Linkeru vložit jinou bitovou šířku v situaci, kdy se nepodařilo vhodná pro dané pokyn, protože symbol cíl je příliš daleko od umístění tuto instrukci adresu nebo offset.  
  
 Možná budete chtít změnit pořadí bitovou kopii (pomocí [/pořadí](../../build/reference/order-put-functions-in-order.md) volby, například) předejdete úroveň dereference.