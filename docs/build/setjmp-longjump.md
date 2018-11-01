---
title: setjmp longjump
ms.date: 11/04/2016
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
ms.openlocfilehash: 765cef3f02bed09bed0278aaeecdcdbd55d86b67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427895"
---
# <a name="setjmplongjump"></a>setjmp/longjump

Pokud zahrnete setjmpex.h nebo setjmp.h, veškerá volání [setjmp](../c-runtime-library/reference/setjmp.md) nebo [longjmp](../c-runtime-library/reference/longjmp.md) způsobí uvolnění, který vyvolá destruktory a finally.  Tím se liší od x86, včetně setjmp.h výsledků v klauzulích finally a destruktory.

Volání `setjmp` zachová aktuální ukazatel zásobníku, bez registry a MxCsr registrů.  Volání `longjmp` vraťte se na nejnovější `setjmp` volání webu a obnoví ukazatel zásobníku, bez registry a MxCsr zaregistruje, zpět do stavu jako zachovaný nejnovější `setjmp` volání.

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)