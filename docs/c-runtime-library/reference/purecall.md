---
title: _purecall
ms.date: 11/04/2016
api_name:
- _purecall
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
ms.openlocfilehash: 5d62ec30731ce26c4683afc88474d4bddb63a697
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950157"
---
# <a name="_purecall"></a>_purecall

Výchozí obslužná rutina chyby volání čistě virtuální funkce. Kompilátor generuje kód pro volání této funkce při volání čistě virtuální členské funkce.

## <a name="syntax"></a>Syntaxe

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Poznámky

Funkce **_purecall** je podrobné informace o implementaci kompilátoru Microsoftu C++ specifické pro společnost Microsoft. Tato funkce není určena k volání přímo v kódu a nemá žádnou veřejnou deklaraci hlavičky. Je zde popsána, protože se jedná o veřejný export běhové knihovny jazyka C.

Volání čistě virtuální funkce je chyba, protože nemá žádnou implementaci. Kompilátor generuje kód pro vyvolání funkce obslužné rutiny chyb **_purecall** při volání čistě virtuální funkce. Ve výchozím nastavení program **_purecall** ukončí program. Před ukončením funkce **_purecall** vyvolá funkci **_purecall_handler** , pokud byla jedna nastavena pro daný proces. Můžete nainstalovat vlastní funkci obslužné rutiny chyb pro volání čistě virtuální funkce, abyste je mohli zachytit pro účely ladění nebo generování sestav. Chcete-li použít vlastní obslužnou rutinu chyb, vytvořte funkci, která má signaturu **_purecall_handler** , pak pomocí [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) ji nastavte na aktuální obslužnou rutinu.

## <a name="requirements"></a>Požadavky

Funkce **_purecall** neobsahuje deklaraci hlavičky. Definice typedef **_purecall_handler** je definována v \<Stdlib. h >.

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
