---
title: _CxxThrowException
ms.date: 11/04/2016
apiname:
- _CxxThrowException
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
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- CxxThrowException
- _CxxThrowException
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
ms.openlocfilehash: 925b72a120b31029b76fa38bee73eea003511cd2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550329"
---
# <a name="cxxthrowexception"></a>_CxxThrowException

Vytvoří záznam o výjimce a volá běhové prostředí, abyste mohli začít zpracovávat výjimky.

## <a name="syntax"></a>Syntaxe

```C
extern "C" void __stdcall _CxxThrowException(
   void* pExceptionObject
   _ThrowInfo* pThrowInfo
);
```

### <a name="parameters"></a>Parametry

*pExceptionObject*<br/>
Objekt, který vygeneroval výjimku.

*pThrowInfo*<br/>
Informace, které je vyžadován ke zpracování výjimky.

## <a name="remarks"></a>Poznámky

Tato metoda je součástí souboru jen pro kompilátor, kterou kompilátor používá ke zpracování výjimek. Nevolejte metodu přímo z uživatelského kódu.

## <a name="requirements"></a>Požadavky

**Zdroj:** Throw.cpp

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
