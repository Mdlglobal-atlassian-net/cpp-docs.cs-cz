---
title: "C3246 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3246
dev_langs: C++
helpviewer_keywords: C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 262dc8bde5dcb4c12909c69bce3fa867685245eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3246"></a>C3246 chyby kompilátoru
'class': nemůže Zdědit z "typ", jako byla deklarována jako 'zapečetěné.  
  
Třídu, která je označena jako [zapečetěné](../../windows/sealed-cpp-component-extensions.md) nemůže být základní třída pro jiné třídy.  
  
Následující ukázka generuje C3246:  
  
```  
// C3246_2.cpp  
// compile with: /clr /LD  
ref class X sealed {};  
  
ref class Y : public X {}; // C3246  
```  