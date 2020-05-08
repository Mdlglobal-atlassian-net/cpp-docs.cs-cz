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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 19ad6c2f517d9ddf277a7bdda6e46c7940f0d3f1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913332"
---
# <a name="_purecall"></a>_purecall

Výchozí obslužná rutina chyby volání čistě virtuální funkce. Kompilátor generuje kód pro volání této funkce při volání čistě virtuální členské funkce.

## <a name="syntax"></a>Syntaxe

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Poznámky

Funkce **_purecall** je podrobný popis implementace pro Microsoft C++ kompilátorem specifickým pro společnost Microsoft. Tato funkce není určena k volání přímo v kódu a nemá žádnou veřejnou deklaraci hlavičky. Je zde popsána, protože se jedná o veřejný export běhové knihovny jazyka C.

Volání čistě virtuální funkce je chyba, protože nemá žádnou implementaci. Kompilátor generuje kód pro vyvolání funkce obslužné rutiny chyb **_purecall** , když je volána čistě virtuální funkce. Ve výchozím nastavení **_purecall** program ukončí. Před ukončením funkce **_purecall** vyvolá funkci **_purecall_handler** , pokud byla jedna nastavena pro daný proces. Můžete nainstalovat vlastní funkci obslužné rutiny chyb pro volání čistě virtuální funkce, abyste je mohli zachytit pro účely ladění nebo generování sestav. Chcete-li použít vlastní obslužnou rutinu chyb, vytvořte funkci, která má podpis **_purecall_handler** a pak pomocí [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) ji nastavte na aktuální obslužnou rutinu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

Funkce **_purecall** nemá deklaraci hlavičky. **_Purecall_handler** typedef je definována v \<> Stdlib. h.

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
