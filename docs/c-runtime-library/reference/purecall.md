---
title: _purecall
ms.date: 4/2/2020
api_name:
- _purecall
- _o__purecall
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: f841bc70a4a5365bb9cc6086dd752bd2a1b583ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338485"
---
# <a name="_purecall"></a>_purecall

Výchozí obslužná rutina chyby volání čisté virtuální funkce. Kompilátor generuje kód pro volání této funkce při volání čisté virtuální členské funkce.

## <a name="syntax"></a>Syntaxe

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Poznámky

Funkce **_purecall** je podrobností implementace kompilátoru Microsoft C++. Tato funkce není určena k volání přímo kódu a nemá žádnou deklaraci veřejné hlavičky. Je zde dokumentován, protože se jedná o veřejný export knihovny C Runtime.

Volání čisté virtuální funkce je chyba, protože nemá žádnou implementaci. Kompilátor generuje kód pro vyvolání funkce obslužné rutiny **chyb _purecall** při volání čisté virtuální funkce. Ve výchozím nastavení **_purecall** program ukončí. Před ukončením **_purecall** funkce vyvolá **funkci _purecall_handler,** pokud byla pro proces nastavena. Můžete nainstalovat vlastní funkci obslužné rutiny chyb pro volání čistě virtuální funkce, chcete-li je zachytit pro účely ladění nebo vytváření sestav. Chcete-li použít vlastní obslužnou rutinu chyb, vytvořte funkci, která má **_purecall_handler** podpis, a potom [použijte _set_purecall_handler](get-purecall-handler-set-purecall-handler.md) k tomu, aby byla aktuální obslužnou rutinou.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

Funkce **_purecall** nemá deklaraci záhlaví. _purecall_handler **_purecall_handler** typedef je \<definován v> stdlib.h.

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
