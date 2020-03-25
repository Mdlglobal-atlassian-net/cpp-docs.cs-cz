---
title: __CxxFrameHandler
ms.date: 11/04/2016
api_name:
- __CxxFrameHandler
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __CxxFrameHandler
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
ms.openlocfilehash: db856850688e378cde9eaa1fb510cb325ce0644b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170979"
---
# <a name="__cxxframehandler"></a>__CxxFrameHandler

Vnitřní funkce CRT. Používá se v CRT ke zpracování strukturovaných rámců výjimek.

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
Záznam výjimky, který je předán možným příkazům `catch`.

*pRN*<br/>
Dynamické informace o bloku zásobníku, který se používá pro zpracování výjimky. Další informace naleznete v tématu ehdata. h.

*pContext*<br/>
Souvislost. (Nepoužívá se na procesorech Intel.)

*Emulátor*<br/>
Další informace o položce funkce a snímku zásobníku.

## <a name="return-value"></a>Návratová hodnota

Jedna z hodnot *výrazu filtru* , kterou používá [příkaz try-except](../cpp/try-except-statement.md).

## <a name="remarks"></a>Poznámky

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__CxxFrameHandler|EXCPT. h, ehdata. h|
