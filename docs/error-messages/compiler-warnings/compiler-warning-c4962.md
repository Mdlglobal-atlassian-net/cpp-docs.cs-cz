---
title: "C4962 upozornění kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4962
dev_langs: C++
helpviewer_keywords: C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dae3bfa67f9f40072c8c200cd681b3babd92aff3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4962"></a>C4962 upozornění kompilátoru
"function': optimalizace na základě profilu zakázán, protože optimalizace způsobila data profilu nekonzistenci"  
  
 Funkce nebyl kompilovat s /LTCG:PGO, protože počet (profil) data pro funkce nespolehlivé. Umožňuje znovu proveďte profilace znovu vygenerovat .pgc soubor, který obsahuje data nespolehlivé profilu pro tuto funkci.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. Další informace najdete v tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).