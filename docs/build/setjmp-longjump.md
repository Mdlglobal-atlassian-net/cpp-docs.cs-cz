---
title: setjmp longjump | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 744b855d1b867507b54973f17e2a4f98b63e2b67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="setjmplongjump"></a>setjmp/longjump
Když zahrnete setjmpex.h nebo setjmp.h, veškerá volání [setjmp](../c-runtime-library/reference/setjmp.md) nebo [longjmp](../c-runtime-library/reference/longjmp.md) bude mít za následek unwind, které vyvolá destruktory a finally.  To se liší od x86, kde včetně výsledků setjmp.h finally – klauzule a destruktory.  
  
 Volání `setjmp` zachová aktuální ukazatel zásobníku, nezávislé registry a registry MxCsr.  Volání `longjmp` vraťte se na nejnovější `setjmp` volání stránku a obnoví ukazatel zásobníku, nezávislé registry a MxCsr zaregistruje, zpátky do stavu voláním nejnovější `setjmp` volání.  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)