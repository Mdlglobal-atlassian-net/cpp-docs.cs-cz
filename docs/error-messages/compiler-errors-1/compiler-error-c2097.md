---
title: C2097 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa4b867c7f043d796f208fdc7100509893147daf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168357"
---
# <a name="compiler-error-c2097"></a>C2097 chyby kompilátoru
Neplatný inicializace  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Inicializace pomocí nonconstant hodnotu proměnné.  
  
2.  Inicializace krátké adresy se dlouho adresou.  
  
3.  Inicializace místní struktury, sjednocení nebo pole s výraz nonconstant při kompilaci s **/Za**.  
  
4.  Inicializace s výrazem, který obsahuje operátor čárka.  
  
5.  Inicializace s výrazem, který není konstantní ani symbolický.