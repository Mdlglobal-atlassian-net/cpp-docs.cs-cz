---
title: setjmp longjump | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55cf6a2503367777464f09f92e3e3614c3d9f11b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="setjmplongjump"></a>setjmp/longjump
Když zahrnete setjmpex.h nebo setjmp.h, veškerá volání [setjmp](../c-runtime-library/reference/setjmp.md) nebo [longjmp](../c-runtime-library/reference/longjmp.md) bude mít za následek unwind, které vyvolá destruktory a finally.  To se liší od x86, kde včetně výsledků setjmp.h finally – klauzule a destruktory.  
  
 Volání `setjmp` zachová aktuální ukazatel zásobníku, nezávislé registry a registry MxCsr.  Volání `longjmp` vraťte se na nejnovější `setjmp` volání stránku a obnoví ukazatel zásobníku, nezávislé registry a MxCsr zaregistruje, zpátky do stavu voláním nejnovější `setjmp` volání.  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)