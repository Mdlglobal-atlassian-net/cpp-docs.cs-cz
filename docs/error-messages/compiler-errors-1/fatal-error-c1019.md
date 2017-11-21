---
title: "Závažná chyba C1019 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1019
dev_langs: C++
helpviewer_keywords: C1019
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 90d826ded9ebd8fdc2b304900af523b7ffe8b395
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1019"></a>Závažná chyba C1019
neočekávané #else  
  
 `#else` – Direktiva se zobrazí mimo `#if`, `#ifdef`, nebo `#ifndef` vytvořit. Použití `#else` pouze do jedné z těchto konstrukce.  
  
 Následující ukázka generuje C1019:  
  
```  
// C1019.cpp  
#else   // C1019  
#endif  
  
int main() {}  
```  
  
 Možná řešení:  
  
```  
// C1019b.cpp  
#if 1  
#else  
#endif  
  
int main() {}  
```