---
title: "C2002 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2002
dev_langs: C++
helpviewer_keywords: C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9a2cbd21c27cff3effad69b19f42eeaecacf20d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2002"></a>C2002 chyby kompilátoru
Neplatný široká charakterová konstanta  
  
 Konstanta vícebajtových znaků není platný.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Konstanta široká charakterová obsahuje další bajtů, než se očekávalo.  
  
2.  Standardní hlavičku STDDEF.h není součástí.  
  
3.  Široké znaky nemůže být zřetězen s obyčejnou textové literály.  
  
4.  Široká charakterová konstanta musí předcházet znak "L":  
  
    ```  
    L'mbconst'  
    ```  
  
5.  Microsoft C++ musí být text argumenty direktivy preprocesoru ASCII. Například direktiva `#pragma message(L"string")`, není platný.