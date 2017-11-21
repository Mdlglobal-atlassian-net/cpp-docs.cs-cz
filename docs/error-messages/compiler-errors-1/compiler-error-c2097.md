---
title: "C2097 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2097
dev_langs: C++
helpviewer_keywords: C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d6955a610e3109c3b16edf96913be4503ee4c647
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2097"></a>C2097 chyby kompilátoru
Neplatný inicializace  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Inicializace pomocí nonconstant hodnotu proměnné.  
  
2.  Inicializace krátké adresy se dlouho adresou.  
  
3.  Inicializace místní struktury, sjednocení nebo pole s výraz nonconstant při kompilaci s **/Za**.  
  
4.  Inicializace s výrazem, který obsahuje operátor čárka.  
  
5.  Inicializace s výrazem, který není konstantní ani symbolický.