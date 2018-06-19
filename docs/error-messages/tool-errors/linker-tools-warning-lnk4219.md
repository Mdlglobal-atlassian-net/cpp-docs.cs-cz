---
title: Upozornění linkerů Lnk4219 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4219
dev_langs:
- C++
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59cb7376957b7985b7ae2335ea472171d490ff42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301132"
---
# <a name="linker-tools-warning-lnk4219"></a>Upozornění linkerů LNK4219
Oprava název oprava přetečení. Cíl "název cílové symbol" je mimo rozsah, vkládání převodu  
  
 Linkeru vložit jinou bitovou šířku v situaci, kdy se nepodařilo vhodná pro dané pokyn, protože symbol cíl je příliš daleko od umístění tuto instrukci adresu nebo offset.  
  
 Možná budete chtít změnit pořadí bitovou kopii (pomocí [/pořadí](../../build/reference/order-put-functions-in-order.md) volby, například) předejdete úroveň dereference.