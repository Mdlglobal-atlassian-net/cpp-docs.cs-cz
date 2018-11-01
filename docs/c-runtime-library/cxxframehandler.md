---
title: __CxxFrameHandler
ms.date: 11/04/2016
apiname:
- __CxxFrameHandler
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __CxxFrameHandler
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
ms.openlocfilehash: d059df597826c68f4f51eb85f592b7eb44ac7d1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432121"
---
# <a name="cxxframehandler"></a>__CxxFrameHandler

Vnitřní funkce CRT. Používá CRT pro zpracování strukturovaných výjimek snímků.

## <a name="syntax"></a>Syntaxe

```cpp
EXCEPTION_DISPOSITION __CxxFrameHandler(
      EHExceptionRecord  *pExcept,
      EHRegistrationNode *pRN,
      void               *pContext,
      DispatcherContext  *pDC
   )
```

#### <a name="parameters"></a>Parametry

*pExcept*<br/>
Záznam o výjimce, která je předána možné `catch` příkazy.

*PRN*<br/>
Dynamické informace o zásobníku, který se používá ke zpracování výjimky. Další informace najdete v tématu ehdata.h.

*pContext*<br/>
Kontext. (Nelze použít na procesorech Intel.)

*primární řadič domény*<br/>
Další informace o funkci položku a v zásobníku rámce.

## <a name="return-value"></a>Návratová hodnota

Jeden z *výrazu filtru* hodnot použitých [zkuste-except – příkaz](../cpp/try-except-statement.md).

## <a name="remarks"></a>Poznámky

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__CxxFrameHandler|excpt.h, ehdata.h|