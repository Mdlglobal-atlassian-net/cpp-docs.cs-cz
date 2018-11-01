---
title: _setjmp3
ms.date: 11/04/2016
apiname:
- _setjmp3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- setjmp3
- _setjmp3
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
ms.openlocfilehash: 4509738f8e0128e2f9277e744a5965f557f65439
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564003"
---
# <a name="setjmp3"></a>_setjmp3

Vnitřní funkce CRT. Novou implementaci `setjmp` funkce.

## <a name="syntax"></a>Syntaxe

```
int _setjmp3(
   OUT jmp_buf env,
   int count,
   (optional parameters)
);
```

#### <a name="parameters"></a>Parametry

*env*<br/>
[out] Adresa vyrovnávací paměti pro ukládání informací o stavu.

*Počet*<br/>
[in] Počet dalších `DWORD`s informací, které jsou uloženy v `optional parameters`.

*Volitelné parametry*<br/>
[in] Další data nasdílí `setjmp` vnitřní. První `DWORD` je ukazatel na funkci, která slouží k uvolnění doplňující data a vrátit se stálé registraci stavu. Druhá `DWORD` je úroveň, zkuste obnovit. Další data se uloží do pole Obecná data v `jmp_buf`.

## <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

Nepoužívejte tuto funkci v programu v jazyce C++. Je vnitřní funkce, která nepodporuje C++. Další informace o tom, jak používat `setjmp`, naleznete v tématu [používání setjmp/longjmp](../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Požadavky

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[setjmp](../c-runtime-library/reference/setjmp.md)