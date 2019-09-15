---
title: _setjmp3
ms.date: 11/04/2016
api_name:
- _setjmp3
api_location:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp3
- _setjmp3
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
ms.openlocfilehash: d7120ddd10322d0b7391608fd388d9f45c1600e8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957797"
---
# <a name="_setjmp3"></a>_setjmp3

Vnitřní funkce CRT. Nová implementace `setjmp` funkce.

## <a name="syntax"></a>Syntaxe

```
int _setjmp3(
   OUT jmp_buf env,
   int count,
   (optional parameters)
);
```

#### <a name="parameters"></a>Parametry

*ENV*<br/>
mimo Adresa vyrovnávací paměti pro ukládání informací o stavu.

*výpočtu*<br/>
pro Počet dalších `DWORD`s informacemi, které jsou uloženy `optional parameters`v.

*volitelné parametry*<br/>
pro Další data, která jsou `setjmp` vydaná vnitřními. První `DWORD` je ukazatel na funkci, který se používá k unwind dat navíc a návrat do nestálého stavu registrace. Druhá `DWORD` je úroveň pokusu o obnovení. Všechna další data jsou uložena do obecného datového pole v `jmp_buf`.

## <a name="return-value"></a>Návratová hodnota

Vždycky vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

Nepoužívejte tuto funkci v C++ programu. Jedná se o vnitřní funkci, která nepodporuje C++. Další informace o tom, jak používat `setjmp`, najdete v tématu [použití setjmp/longjmp](../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Požadavky

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[setjmp](../c-runtime-library/reference/setjmp.md)
