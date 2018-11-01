---
title: _purecall
ms.date: 11/04/2016
apiname:
- _purecall
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: a7a6db42dc4b8d9b2962a66c7866aae9db55eb3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541180"
---
# <a name="purecall"></a>_purecall

Výchozí čistě virtuální funkce volání obslužné rutiny. Kompilátor generuje kód pro volání této funkce při volání čistě virtuální členské funkce.

## <a name="syntax"></a>Syntaxe

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Poznámky

**_Purecall –** funkce je specifické pro společnost Microsoft podrobnosti implementace kompilátoru Microsoft Visual C++. Tato funkce není určena k volání přímo ve vašem kódu a nemá žádné veřejné záhlaví deklarace. Je tady popsali, protože je k veřejné exportu knihovny Runtime jazyka C.

Volání čistě virtuální funkce se o chybu, protože nemá žádnou implementaci. Kompilátor generuje kód, který má být vyvolán **_purecall –** funkci obslužné rutiny chyb při volání čistě virtuální funkce. Ve výchozím nastavení **_purecall –** ukončí program. Než se ukončí, **_purecall –** vyvolá funkce **_purecall_handler** fungovat, pokud byla nastavena pro proces. Můžete nainstalovat vlastní funkci obslužné rutiny chyby pro volání čistě virtuální funkce, je pro ladění nebo pro účely vykazování zachytit. Pokud chcete použít vlastní obslužnou rutinu chyb, vytvořte funkci, která má **_purecall_handler** podpis, pak použít [_set_purecall_handler –](get-purecall-handler-set-purecall-handler.md) k němu aktuální obslužné rutiny.

## <a name="requirements"></a>Požadavky

**_Purecall –** funkce nemá deklaraci záhlaví. **_Purecall_handler** definice typedef je definována v \<stdlib.h >.

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
