---
title: "C2722 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2722
dev_langs: C++
helpviewer_keywords: C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c2db3d8ac30d51e04d425bd27e9d9d5c12e62931
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2722"></a>C2722 chyby kompilátoru
':: operátor ': neplatný následující operátor příkaz; operátor ' operátor '  
  
 `operator` Příkaz předefinování `::new` nebo `::delete`. `new` a `delete` operátory jsou globální, proto operátor řešení rozsahu (`::`) je smysl. Odeberte `::` operátor.