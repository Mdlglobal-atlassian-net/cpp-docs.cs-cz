---
title: setjmp longjump | Dokumentace Microsoftu
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
ms.openlocfilehash: f53160a5deeb3ea0db111fc0aae7429b19b7cc86
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703271"
---
# <a name="setjmplongjump"></a>setjmp/longjump

Pokud zahrnete setjmpex.h nebo setjmp.h, veškerá volání [setjmp](../c-runtime-library/reference/setjmp.md) nebo [longjmp](../c-runtime-library/reference/longjmp.md) způsobí uvolnění, který vyvolá destruktory a finally.  Tím se liší od x86, včetně setjmp.h výsledků v klauzulích finally a destruktory.

Volání `setjmp` zachová aktuální ukazatel zásobníku, bez registry a MxCsr registrů.  Volání `longjmp` vraťte se na nejnovější `setjmp` volání webu a obnoví ukazatel zásobníku, bez registry a MxCsr zaregistruje, zpět do stavu jako zachovaný nejnovější `setjmp` volání.

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)