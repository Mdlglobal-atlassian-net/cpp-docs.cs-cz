---
title: jitintrinsic
ms.date: 11/04/2016
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
ms.openlocfilehash: 9e726413f0bbfbd9d6affa348777c995c51283a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245510"
---
# <a name="jitintrinsic"></a>jitintrinsic

Označí funkci jako významnou pro 64bitový modul CLR (Common Language Runtime). Používáno pro určité funkce v knihovnách poskytnutých společností Microsoft.

## <a name="syntax"></a>Syntaxe

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>Poznámky

**jitintrinsic** přidá klíčové slovo MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) k signatuře funkce.

Není doporučeno použití této funkce **__declspec** modifikátor, jako výsledky neočekávané situace může nastat.

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)