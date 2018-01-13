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
ms.workload: cplusplus
ms.openlocfilehash: 1331931ba2fa7219a27b8f60b185dc3ab9310328
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4219"></a>Upozornění linkerů LNK4219
Oprava název oprava přetečení. Cíl "název cílové symbol" je mimo rozsah, vkládání převodu  
  
 Linkeru vložit jinou bitovou šířku v situaci, kdy se nepodařilo vhodná pro dané pokyn, protože symbol cíl je příliš daleko od umístění tuto instrukci adresu nebo offset.  
  
 Možná budete chtít změnit pořadí bitovou kopii (pomocí [/pořadí](../../build/reference/order-put-functions-in-order.md) volby, například) předejdete úroveň dereference.