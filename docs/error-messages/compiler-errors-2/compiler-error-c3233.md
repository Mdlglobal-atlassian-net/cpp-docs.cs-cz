---
title: "C3233 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3233
dev_langs: C++
helpviewer_keywords: C3233
ms.assetid: a9210830-1136-4f02-ba41-030c85f93547
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d3d29fbfb33a0697120fa0386d94f4023360abd1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3233"></a>C3233 chyby kompilátoru
'type': Parametr obecného typu již omezené.  
  
 Není platné. Chcete-li omezit obecný parametr ve více než jeden `where` klauzule.  
  
 Následující ukázka generuje C3233:  
  
```  
// C3233.cpp  
// compile with: /clr /LD  
  
interface struct C {};  
interface struct D {};  
  
generic <class T>  
where T : C  
where T : D  
ref class E {};   // C3233  
```