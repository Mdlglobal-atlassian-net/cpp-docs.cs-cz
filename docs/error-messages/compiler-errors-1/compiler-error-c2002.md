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
ms.openlocfilehash: d8f6fc5983a462850581f69ca32dd7c305f9e847
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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