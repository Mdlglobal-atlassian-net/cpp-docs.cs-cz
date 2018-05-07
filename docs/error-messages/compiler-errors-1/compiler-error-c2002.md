---
title: C2002 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01124fc839d6e788ff2dccae325f01f7d4337f5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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